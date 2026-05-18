# YClients Integration Skill

## Overview

Complete guide for integrating with the YClients API (or any similar external booking/CRM API) in the FreeUp project. Covers the full stack: schemas, database, backend gateway, service layer, REST endpoints, frontend types, UI components, and testing.

## Architecture Pattern

```
External API
    |
    v
YClientsGateway          <-- raw HTTP, auth, error translation
    |
    v
YClients Schemas         <-- Pydantic models for API request/response
    |
    v
Domain Service Layer     <-- business logic, DB transactions
    |
    v
Partner/Booking Router   <-- REST endpoints
    |
    v
Frontend API Client      <-- typed fetch wrapper
    |
    v
React Components         <-- UI with loading/error states
```

## 1. Database Layer

### Pattern: Store external IDs as nullable strings on existing tables

Never create separate tables for external entities unless you need to cache large datasets. Store foreign keys inline:

```python
# backend/src/models.py
class Venue(Base):
    # ... existing fields ...
    yclients_location_id: Mapped[str | None] = mapped_column(String(128), nullable=True)
    yandex_org_id: Mapped[str | None] = mapped_column(String(64), nullable=True)

class Slot(Base):
    # ... existing fields ...
    yclients_service_id: Mapped[str | None] = mapped_column(String(128), nullable=True)
    yclients_staff_id: Mapped[str | None] = mapped_column(String(128), nullable=True)

class Booking(Base):
    # ... existing fields ...
    yclients_record_id: Mapped[str | None] = mapped_column(String(128), nullable=True)
    yclients_record_status: Mapped[str | None] = mapped_column(String(64), nullable=True)
```

### Migration Rule

Always use Alembic. Never modify `models.py` without a migration:

```bash
cd backend && alembic revision --autogenerate -m "add_yclients_fields_to_venues_slots_bookings"
```

## 2. Schemas Layer

### Pattern: Separate API schemas from domain schemas

```python
# backend/src/integrations/yclients/schemas.py

# --- YClients API response models ---
class YClientsClient(BaseModel):
    id: int
    name: str
    phone: str
    email: str | None = None

class YClientsService(BaseModel):
    id: int
    title: str
    cost: int | None = None
    duration: int | None = None  # seconds

class YClientsStaff(BaseModel):
    id: int
    name: str
    specialization: str | None = None
    bookable: bool = False

class YClientsFilial(BaseModel):
    id: int
    title: str
    address: str | None = None
    city: str | None = None
    phone: str | None = None

class YClientsBookingRecord(BaseModel):
    record_id: str
    location_id: str
    location_name: str
    resource_id: str
    resource_name: str
    resource_type: str
    starts_at: datetime
    ends_at: datetime
```

### Pattern: Domain response models for frontend

```python
# backend/src/domains/partners/schemas.py

class YClientsServiceItem(BaseModel):
    id: int
    title: str
    cost: int | None = None
    duration: int | None = None

class YClientsStaffItem(BaseModel):
    id: int
    name: str
    specialization: str | None = None
    bookable: bool = False

class YClientsFilialItem(BaseModel):
    id: int
    title: str
    address: str | None = None
    city: str | None = None
    phone: str | None = None
```

## 3. Gateway Layer

### Pattern: Async gateway with context manager client

```python
# backend/src/integrations/yclients/gateway.py

class YClientsGateway:
    """Raw YClients API client.
    
    CRITICAL: YCLIENTS_COMPANY_ID is the PARTNER id (e.g. 15930), NOT a filial.
    All API calls that reference a company must use the location_id (filial id)
    passed at call time, NOT the partner id.
    """

    def _raise_on_unexpected_status(self, response, message: str) -> None:
        if response.status_code not in (200, 201, 204):
            raise YClientsError(f"{message}: {response.text}", response.status_code)

    async def list_filials(self) -> list[YClientsFilial]:
        async with get_yclients_client() as client:
            response = await client.get("/companies")
            self._raise_on_unexpected_status(response, "list companies failed")
            data = response.json().get("data", [])
            return [YClientsFilial(**item) for item in data]

    async def list_services(self, location_id: str) -> list[YClientsService]:
        async with get_yclients_client() as client:
            response = await client.get(f"/company/{location_id}/services")
            self._raise_on_unexpected_status(response, "list services failed")
            data = response.json().get("data", [])
            return [YClientsService(**item) for item in data]

    async def list_staff(self, location_id: str) -> list[YClientsStaff]:
        async with get_yclients_client() as client:
            response = await client.get(f"/staff/{location_id}")
            self._raise_on_unexpected_status(response, "list staff failed")
            data = response.json().get("data", [])
            return [YClientsStaff(**item) for item in data]

    async def find_client_by_phone(self, phone: str, *, location_id: str) -> YClientsClient | None:
        async with get_yclients_client() as client:
            response = await client.post(
                f"/company/{location_id}/clients/search",
                json={"phone": phone, "page": 1, "page_size": 10, "fields": ["id", "name", "phone"]},
            )
            self._raise_on_unexpected_status(response, "client search failed")
            clients = response.json().get("data", [])
            return YClientsClient(**clients[0]) if clients else None

    async def create_client(self, name: str, phone: str, *, location_id: str) -> YClientsClient:
        async with get_yclients_client() as client:
            response = await client.post(f"/clients/{location_id}", json={"name": name, "phone": phone})
            self._raise_on_unexpected_status(response, "create client failed")
            return YClientsClient(**response.json()["data"])

    async def create_booking(self, *, location_id: str, resource_id: str, resource_name: str,
                             resource_type: str, service_id: str, starts_at: datetime,
                             ends_at: datetime, phone: str, full_name: str,
                             email: str | None, idempotency_key: str) -> YClientsBookingRecord:
        async with get_yclients_client() as client:
            response = await client.post(
                f"/book_record/{location_id}",
                json={
                    "phone": phone,
                    "fullname": full_name,
                    "email": email or "",
                    "code": "",
                    "comment": f"idempotency_key={idempotency_key}",
                    "type": "mobile_api",
                    "notify_by_sms": 0,
                    "notify_by_email": 0,
                    "api_id": idempotency_key,
                    "appointments": [{
                        "id": 0,
                        "services": [int(service_id) if service_id.isdigit() else service_id],
                        "staff_id": int(resource_id) if resource_id.isdigit() else resource_id,
                        "datetime": starts_at.isoformat(),
                    }],
                },
            )
            self._raise_on_unexpected_status(response, "create booking failed")
            # ... parse response ...

    async def cancel_booking(self, location_id: str, record_id: str) -> None:
        async with get_yclients_client() as client:
            response = await client.delete(f"/record/{location_id}/{record_id}")
            self._raise_on_unexpected_status(response, "cancel booking failed")

    async def get_record(self, location_id: str, record_id: str) -> YClientsBookingRecord:
        async with get_yclients_client() as client:
            response = await client.get(f"/record/{location_id}/{record_id}")
            if response.status_code == 404:
                raise YClientsError(f"Record {record_id} not found", 404)
            self._raise_on_unexpected_status(response, "get record failed")
            # ... parse response ...
```

### Critical Rules

1. **Never use partner_id (15930) as location_id** — always use venue's `yclients_location_id`
2. **Auth header format**: `Bearer {PARTNER_TOKEN}, User {USER_TOKEN}`
3. **Accept header**: `application/vnd.yclients.v2+json`
4. **All gateway methods are async** and use `async with get_yclients_client()` context manager
5. **Gateway has NO constructor args** — removed `company_id` parameter
6. **Client binding happens at booking time** — `_ensure_yclients_client_id()` inside `create_booking()` where venue context exists

## 4. Mock Gateway

### Pattern: Mock extends real gateway, overrides methods

```python
# backend/src/integrations/yclients/mock_gateway.py

class MockYClientsGateway(YClientsGateway):
    def __init__(self) -> None:
        self._cancelled_records: set[str] = set()

    async def list_filials(self) -> list[YClientsFilial]:
        return [
            YClientsFilial(id=1868505, title="Свободно", address="", city="Москва", phone=""),
        ]

    async def list_services(self, location_id: str) -> list[YClientsService]:
        return [
            YClientsService(id=28295493, title="Услуга", cost=0, duration=3600),
        ]

    async def list_staff(self, location_id: str) -> list[YClientsStaff]:
        return [
            YClientsStaff(id=5282874, name="Сотрудник 1", specialization="специалист", bookable=False),
        ]

    async def find_client_by_phone(self, phone: str, *, location_id: str) -> YClientsClient | None:
        return YClientsClient(id=9000001, name="Demo Client", phone=phone)

    async def create_booking(self, **kwargs) -> YClientsBookingRecord:
        return YClientsBookingRecord(
            record_id=f"YC-{datetime.now().strftime('%Y%m%d')}-1234",
            location_id=kwargs["location_id"],
            location_name="YClients (demo)",
            resource_id=kwargs["resource_id"],
            resource_name=kwargs["resource_name"],
            resource_type=kwargs["resource_type"],
            starts_at=kwargs["starts_at"],
            ends_at=kwargs["ends_at"],
        )

    async def cancel_booking(self, location_id: str, record_id: str) -> None:
        self._cancelled_records.add(record_id)

    async def get_record(self, location_id: str, record_id: str) -> YClientsBookingRecord:
        if record_id in self._cancelled_records:
            raise YClientsError("Record not found", 404)
        return YClientsBookingRecord(...)
```

### Mock Toggle

```python
# backend/src/core/deps.py
def get_yclients_gateway():
    if get_settings().USE_YCLIENTS_MOCK:
        from src.integrations.yclients.mock_gateway import MockYClientsGateway
        return MockYClientsGateway()
    return YClientsGateway()
```

## 5. Service Layer

### Pattern: Gateway injected into service functions

```python
# backend/src/domains/partners/service.py

async def create_partner_venue(
    db: AsyncSession,
    user: User,
    *,
    name: str,
    service_category: str,
    description: str,
    address: str,
    latitude: float | None = None,
    longitude: float | None = None,
    yclients_location_id: str | None = None,
    yandex_org_id: str | None = None,
) -> Venue:
    venue = Venue(
        partner_id=user.id,
        name=name,
        service_category=service_category,
        description=description,
        address=address,
        latitude=latitude or 0.0,
        longitude=longitude or 0.0,
        yclients_location_id=yclients_location_id,
        yandex_org_id=yandex_org_id,
    )
    db.add(venue)
    await db.commit()
    await db.refresh(venue)
    return venue
```

### Pattern: Two-way sync with polling

```python
async def sync_partner_bookings_with_yclients(
    db: AsyncSession,
    user: User,
    yclients_gateway: YClientsGateway | None = None,
) -> dict:
    gateway = yclients_gateway or YClientsGateway()
    
    # Get confirmed bookings with yclients_record_id
    result = await db.execute(
        select(Booking, Venue)
        .join(Venue, Booking.venue_id == Venue.id)
        .where(
            Venue.partner_id == user.id,
            Booking.status == "confirmed",
            Booking.yclients_record_id.is_not(None),
        )
    )
    
    checked = updated = skipped = 0
    errors: list[str] = []
    
    for booking, venue in result.all():
        checked += 1
        location_id = venue.yclients_location_id
        record_id = booking.yclients_record_id
        
        if not location_id:
            skipped += 1
            continue
            
        try:
            await gateway.get_record(location_id, record_id)
        except YClientsError as exc:
            if exc.status_code == 404:
                booking.status = "cancelled"
                booking.yclients_record_status = "cancelled"
                updated += 1
            else:
                errors.append(f"Record {record_id}: {exc.message}")
    
    await db.commit()
    return {"checked": checked, "updated": updated, "skipped": skipped, "errors": errors}
```

## 6. Router Layer

### Pattern: Gateway injected via dependency, domain schemas for response

```python
# backend/src/domains/partners/router.py

@router.get("/yclients/filials", response_model=list[YClientsFilialItem])
async def get_yclients_filials(
    user: User = Depends(require_roles(UserRole.PARTNER, UserRole.ADMIN)),
) -> list[YClientsFilialItem]:
    gateway = get_yclients_gateway()
    try:
        filials = await gateway.list_filials()
        return [YClientsFilialItem(id=f.id, title=f.title, address=f.address, city=f.city, phone=f.phone) for f in filials]
    except Exception:
        return []

@router.get("/yclients/services", response_model=list[YClientsServiceItem])
async def get_yclients_services(
    venue_id: str,
    db: AsyncSession = Depends(get_db),
    user: User = Depends(require_roles(UserRole.PARTNER, UserRole.ADMIN)),
) -> list[YClientsServiceItem]:
    venues = await list_partner_venues(db, user)
    venue = next((v for v in venues if v.id == venue_id), None)
    if venue is None or not venue.yclients_location_id:
        return []
    gateway = get_yclients_gateway()
    services = await gateway.list_services(venue.yclients_location_id)
    return [YClientsServiceItem(id=s.id, title=s.title, cost=s.cost, duration=s.duration) for s in services]

@router.get("/yclients/staff", response_model=list[YClientsStaffItem])
async def get_yclients_staff(
    venue_id: str,
    db: AsyncSession = Depends(get_db),
    user: User = Depends(require_roles(UserRole.PARTNER, UserRole.ADMIN)),
) -> list[YClientsStaffItem]:
    venues = await list_partner_venues(db, user)
    venue = next((v for v in venues if v.id == venue_id), None)
    if venue is None or not venue.yclients_location_id:
        return []
    gateway = get_yclients_gateway()
    staff = await gateway.list_staff(venue.yclients_location_id)
    return [YClientsStaffItem(id=s.id, name=s.name, specialization=s.specialization, bookable=s.bookable) for s in staff]
```

## 7. Frontend API Client

### Pattern: Type the response, export both type and method

```typescript
// frontend/src/api/client.ts

export type YClientsFilialItem = {
  id: number;
  title: string;
  address: string | null;
  city: string | null;
  phone: string | null;
};

export type YClientsServiceItem = {
  id: number;
  title: string;
  cost: number | null;
  duration: number | null;
};

export type YClientsStaffItem = {
  id: number;
  name: string;
  specialization: string | null;
  bookable: boolean;
};

export type YClientsSyncResult = {
  checked: number;
  updated: number;
  skipped: number;
  errors: string[];
};

export const api = {
  // ... other methods ...
  
  getYClientsFilials: async () =>
    request<YClientsFilialItem[]>("/api/partner/yclients/filials"),
  
  getYClientsServices: async (venueId: string) =>
    request<YClientsServiceItem[]>(`/api/partner/yclients/services?venue_id=${venueId}`),
  
  getYClientsStaff: async (venueId: string) =>
    request<YClientsStaffItem[]>(`/api/partner/yclients/staff?venue_id=${venueId}`),
  
  syncPartnerBookingsWithYClients: async () =>
    request<YClientsSyncResult>("/api/partner/bookings/sync-yclients", { method: "POST" }),
};
```

## 8. Frontend Components

### Pattern: Card with load action + list + import action

```tsx
// In PartnerDashboardPage.tsx

const [yclientsFilials, setYClientsFilials] = useState<YClientsFilialItem[]>([]);
const [filialsLoading, setFilialsLoading] = useState(false);
const [filialsError, setFilialsError] = useState<string | null>(null);

async function loadYClientsFilials() {
  setFilialsLoading(true);
  setFilialsError(null);
  try {
    const data = await api.getYClientsFilials();
    setYClientsFilials(data);
  } catch (err) {
    setFilialsError(err instanceof Error ? err.message : "Ошибка загрузки");
  } finally {
    setFilialsLoading(false);
  }
}

async function importFilial(filial: YClientsFilialItem) {
  try {
    await api.createPartnerVenue({
      name: filial.title,
      service_category: "billiard",
      description: `Филиал из YClients: ${filial.title}`,
      address: filial.address || "Адрес не указан",
      latitude: undefined,
      longitude: undefined,
      yclients_location_id: String(filial.id),
      yandex_org_id: null,
    });
    setYClientsFilials((prev) => prev.filter((f) => f.id !== filial.id));
    await reload();
  } catch (err) {
    setVenueError(err instanceof Error ? err.message : "Ошибка импорта");
  }
}

// In JSX:
<Card>
  <div className="flex items-center justify-between gap-3">
    <div>
      <h3 className="text-lg font-semibold text-surface">YClients филиалы</h3>
      <p className="text-xs text-surface/50 mt-1">
        Подтяните филиалы из YClients чтобы автоматически создать точки
      </p>
    </div>
    <Button tone="neutral" disabled={filialsLoading} onClick={() => void loadYClientsFilials()}>
      {filialsLoading ? "Загрузка…" : "Подтянуть филиалы"}
    </Button>
  </div>
  {filialsError && (
    <div className="mt-3 rounded-xl border border-red-200 bg-red-50 px-3 py-2 text-sm text-red-700">
      {filialsError}
    </div>
  )}
  {yclientsFilials.length > 0 && (
    <div className="mt-3 space-y-2">
      {yclientsFilials.map((filial) => (
        <div key={filial.id} className="flex items-center justify-between gap-3 rounded-xl border border-slate-200 bg-white px-3 py-2.5">
          <div className="min-w-0">
            <div className="text-sm font-medium text-surface truncate">{filial.title}</div>
            <div className="text-xs text-surface/50 truncate">ID: {filial.id} {filial.address ? `· ${filial.address}` : ""}</div>
          </div>
          <Button tone="neutral" className="shrink-0 text-xs py-2 px-3" onClick={() => void importFilial(filial)}>
            Импортировать
          </Button>
        </div>
      ))}
    </div>
  )}
</Card>
```

### Pattern: Service/staff dropdowns that depend on venue

```tsx
const [yclientsServices, setYClientsServices] = useState<YClientsServiceItem[]>([]);
const [yclientsStaff, setYClientsStaff] = useState<YClientsStaffItem[]>([]);
const [yclientsLoading, setYClientsLoading] = useState(false);

useEffect(() => {
  const venue = venues.find((v) => v.id === slotForm.venue_id);
  if (!venue || !venue.yclients_location_id) {
    setYClientsServices([]);
    setYClientsStaff([]);
    return;
  }
  setYClientsLoading(true);
  Promise.all([
    api.getYClientsServices(venue.id),
    api.getYClientsStaff(venue.id),
  ])
    .then(([services, staff]) => {
      setYClientsServices(services);
      setYClientsStaff(staff);
    })
    .catch(() => {
      setYClientsServices([]);
      setYClientsStaff([]);
    })
    .finally(() => setYClientsLoading(false));
}, [slotForm.venue_id, venues]);

// In form:
<Field label={<>YClients услуга <InlineTip text="Услуги подгружаются из YClients автоматически." /></>}>
  <select value={slotForm.yclients_service_id} onChange={...}>
    <option value="">— выберите услугу —</option>
    {yclientsServices.map((s) => (
      <option key={s.id} value={String(s.id)}>{s.title} ({s.cost}₽)</option>
    ))}
  </select>
</Field>
```

## 9. Testing

### Pattern: Fake gateway in tests

```python
# backend/tests/test_yclients_integration.py

class FakeYClientsGateway(YClientsGateway):
    def __init__(self):
        self.missing_records: set[str] = set()

    async def get_record(self, location_id: str, record_id: str) -> YClientsBookingRecord:
        if record_id in self.missing_records:
            raise YClientsError("Not found", 404)
        return YClientsBookingRecord(...)

@pytest.mark.asyncio
async def test_sync_yclients_updates_cancelled_bookings(db, partner_user, venue_with_location):
    gateway = FakeYClientsGateway()
    gateway.missing_records.add("yc-record-123")
    
    result = await sync_partner_bookings_with_yclients(db, partner_user, gateway)
    
    assert result["updated"] == 1
    assert booking.status == "cancelled"
```

### Frontend e2e pattern

Mock `window.Telegram.WebApp` in tests. See `frontend/src/test/e2e/app.spec.ts` for `installTelegramWebApp()` helper.

## 10. Environment Configuration

```bash
# .env
YCLIENTS_PARTNER_TOKEN=""
YCLIENTS_USER_TOKEN=""
YCLIENTS_COMPANY_ID=""
YCLIENTS_BASE_URL="https://api.yclients.com/api/v1"
USE_YCLIENTS_MOCK=false
```

## 11. Error Handling Patterns

| Scenario | Pattern |
|----------|---------|
| YClients 404 on get_record | Mark booking as cancelled (external cancellation) |
| YClients 403 on cancel | Mark as `cancel_pending`, local cancel succeeds |
| Partial mapping | Return 422 with clear message |
| No location_id | Skip YClients entirely, operate locally |
| Gateway unavailable | Return empty lists for services/staff, don't block UI |

## 12. Checklist for New External API Integration

- [ ] Add external IDs to DB models (nullable strings)
- [ ] Create Alembic migration
- [ ] Create Pydantic schemas for API request/response
- [ ] Create gateway class with context manager client
- [ ] Create mock gateway extending real gateway
- [ ] Wire gateway selection in `core/deps.py`
- [ ] Add domain service functions using gateway
- [ ] Add REST endpoints with proper auth
- [ ] Add frontend API types and methods
- [ ] Add frontend UI components with loading/error states
- [ ] Add tests with fake gateway
- [ ] Add e2e tests mocking external API
- [ ] Document critical IDs and auth format
- [ ] Add env vars to `.env` and `Settings`

## Files

| Layer | Files |
|-------|-------|
| DB Models | `backend/src/models.py` |
| Migrations | `backend/alembic/versions/` |
| API Schemas | `backend/src/integrations/yclients/schemas.py` |
| Gateway | `backend/src/integrations/yclients/gateway.py` |
| Mock | `backend/src/integrations/yclients/mock_gateway.py` |
| Client | `backend/src/integrations/yclients/client.py` |
| Domain Service | `backend/src/domains/partners/service.py` |
| Domain Router | `backend/src/domains/partners/router.py` |
| Domain Schemas | `backend/src/domains/partners/schemas.py` |
| Frontend API | `frontend/src/api/client.ts` |
| Frontend UI | `frontend/src/pages/PartnerDashboardPage.tsx` |
| Tests | `backend/tests/test_yclients_integration.py` |
| e2e Tests | `frontend/src/test/e2e/app.spec.ts` |
| Config | `backend/src/core/config.py`, `.env` |
