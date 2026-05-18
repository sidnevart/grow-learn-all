# Cashback Targeting Platform — Technical Challenges

> Материал для LinkedIn / Portfolio / Case Study

---

## Вариант 1: Короткий технишь для LinkedIn Description

```
Backend platform for partner-funded cashback targeting in banking.

The hard part wasn't building the API — it was making complex analytical queries over 30M+ daily transactions feel instant. We were hitting query timeouts on legacy aggregated tables, and ClickHouse migration became the only viable path.

Key technical challenges we solved:
• Querying 1.5 years of raw transaction history with sub-second response for audience building
• Migrating from legacy SQL to ClickHouse-as-a-Service without breaking existing partner integrations
• Eliminating flaky CI tests that slowed down releases by 20+ minutes per run
• Maintaining consistency between ClickHouse analytics and PostgreSQL operational data
• Running real-time audience recomputation when transaction patterns change

Stack: Java, Kotlin, Go, Spring Boot, ClickHouse, PostgreSQL, Kafka, Redis, gRPC

Result: 5x analytics speedup, 80% legacy code removed, 30% faster CI/CD, $600K+ annual business impact.
```

---

## Вариант 2: Развернутый "Behind the Scenes" для Case Study

### The Problem Nobody Talked About

We had 30M+ transactions/day flowing through the system. Partner cashback campaigns required audience building based on spend/income behavior over 1.5 years of history. Legacy solution used pre-aggregated tables that took 40+ seconds for complex queries, and some scenarios simply timed out.

### Challenge 1: Query Performance at Scale

**Symptom:** Audience-building queries over 1.5 years of history were taking 30-60 seconds. Some partners needed near-real-time campaign adjustments.

**Root cause:** PostgreSQL with pre-aggregated tables wasn't designed for analytical queries over billions of rows. Index bloat, lock contention on aggregation jobs, and query planner misestimates.

**Decision:** Evaluate ClickHouse vs Druid vs BigQuery. ClickHouse won on latency for point queries and deployment flexibility.

**Migration nuance:** We couldn't just dump data and switch. Partner APIs expected specific response schemas and SLAs. We ran ClickHouse in parallel for 3 weeks, comparing query results row-by-row before cutting over.

**Result:** 5x speedup on key analytics scenarios. Sub-second audience building where it previously took half a minute.

### Challenge 2: Data Consistency Across Stores

**Symptom:** ClickHouse analytics showed different audience counts than PostgreSQL operational data. Partner teams didn't trust the numbers.

**Root cause:** Eventual consistency between streaming ingestion (Kafka → ClickHouse) and transactional writes (PostgreSQL). Duplicate events, out-of-order processing, and missing backfill logic.

**Solution:**
- Exactly-once semantics on Kafka consumers
- Idempotent inserts with deduplication keys in ClickHouse
- Reconciliation job running hourly comparing row counts and checksums
- Clear SLAs: operational data is source of truth, analytics has 5-minute acceptable lag

**Result:** 99.95% consistency between systems. Partner trust restored.

### Challenge 3: CI/CD That Became a Bottleneck

**Symptom:** Backend pipeline took 40+ minutes. Tests randomly failed on infrastructure issues, forcing re-runs.

**Root cause:** Testcontainers startup time, lack of parallelization, and flaky tests that depended on timing.

**Solution:**
- Parallel test execution with dynamic test slicing
- Mocked external dependencies instead of real containers where possible
- Identified and fixed 12 tests with race conditions

**Result:** 30% faster pipeline execution, 20 minutes saved per run, zero flaky tests.

### Challenge 4: Removing 80% of Legacy Code

**Symptom:** Codebase had 4 years of accumulated technical debt. Multiple "temporary" solutions for audience building coexisted.

**Risk:** Any change required touching 5+ services. Fear of breaking existing partner campaigns paralyzed refactoring.

**Approach:**
- Feature flags for gradual rollout
- Strangler Fig pattern: proxy legacy endpoints, route traffic incrementally
- 3-month deprecation window with partner notifications
- Comprehensive integration tests covering edge cases from production logs

**Result:** 80% code removed, full documentation coverage, and deployment frequency increased from weekly to daily.

---

## Вариант 3: LinkedIn Post (Story Format)

```
We were processing 30M transactions/day for cashback targeting.
Queries over 1.5 years of history took 40+ seconds.
Some just timed out.

Here's what we did:

1. Legacy PostgreSQL couldn't handle analytical queries at this scale. Pre-aggregated tables were a band-aid. We evaluated ClickHouse, Druid, and BigQuery. ClickHouse won on latency.

2. Migration wasn't a simple data dump. Partner APIs had SLAs. We ran parallel systems for 3 weeks, comparing results row-by-row. Only then cut over.

3. Data consistency broke trust. ClickHouse showed different numbers than PostgreSQL. We built exactly-once ingestion, hourly reconciliation, and clear SLAs.

4. CI/CD was slowing us down. 40+ minute pipelines with flaky tests. We parallelized execution, mocked external deps, and fixed 12 race conditions.

5. Removed 80% of legacy code. Used feature flags and Strangler Fig pattern. Partner campaigns didn't break.

Result: 5x speedup, $600K+ annual impact, deployments went from weekly to daily.

The real challenge wasn't picking the database.
It was migrating without anyone noticing.
```

---

## Технические темы, которые можно раскрыть глубже

### 1. ClickHouse Schema Design
- Какие движки использовали (MergeTree, ReplacingMergeTree)
- Партиционирование и шардирование
- Материализованные представления для агрегаций

### 2. Kafka Architecture
- Топология топиков (raw transactions → enriched → audience updates)
- Backpressure handling при пиках нагрузки
- Dead letter queues для failed events

### 3. Multi-Language Backend
- Почему Java + Kotlin + Go в одной системе
- Какие сервисы на чем писали
- gRPC vs REST: trade-offs

### 4. Audience Building Engine
- Как пересчитывать аудитории при изменении правил
- Real-time vs batch processing
- Caching strategy (Redis)

### 5. Observability
- Как отслеживали 5x speedup
- Query performance monitoring
- Alerting на консистентность данных

---

## Мой совет: что добавить в основной description

Добавь 1-2 абзаца с техническими проблемами между текущим business description и bullet points. Это привлечет engineering audience.

**Рекомендуемый фрагмент для вставки (после 1-го абзаца):**

> The hardest technical challenge was running sub-second analytical queries over 1.5 years of raw transaction history. Legacy pre-aggregated tables hit a wall at 30M+ transactions/day. Migrating to ClickHouse-as-a-Service required running dual systems for weeks while maintaining partner SLAs. We also had to solve data consistency between streaming analytics (ClickHouse) and operational stores (PostgreSQL), eliminate flaky tests that slowed CI/CD by 20+ minutes per run, and safely remove 80% of legacy code without breaking active cashback campaigns.

---

*Файл подготовлен для portfolio/LinkedIn. Используйте любой вариант или комбинируйте.*