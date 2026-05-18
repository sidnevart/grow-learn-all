# Distributed Systems и System Design

> **Цель:** Перейти от "я ускорил ClickHouse в 5x" к "я могу спроектировать систему для 1B событий/день с нуля"
> **Время:** 2-3 месяца
> **Формат:** Теория + pet project + case studies + публичные посты

---

## Что именно учить

### 1. Основы (неделя 1-2)

**Темы:**
- CAP Theorem (в depth: CP vs AP, PACELC)
- Consistency Models: Strong, Eventual, Causal, Read-Your-Writes, Session
- ACID vs BASE
- Replication (synchronous, asynchronous, multi-leader)
- Partitioning / Sharding (hash, range, consistent hashing)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| Designing Data-Intensive Applications (DDIA) — Ch. 1-6 | Книга | 20 часов | [Amazon](https://amazon.com) / PDF |
| ByteByteGo Newsletter | Статьи | 30 мин/неделю | [newsletter.bytebytego.com](https://newsletter.bytebytego.com) |
| System Design Primer | GitHub | 5 часов | [github.com/donnemartin/system-design-primer](https://github.com/donnemartin/system-design-primer) |
| MIT 6.824 (Distributed Systems) | Курс | 12 лекций | [pdos.csail.mit.edu/6.824](https://pdos.csail.mit.edu/6.824/) |

**Output:** Написать пост: "CAP Theorem в production: что я узнал из ClickHouse миграции"

### 2. Consensus и Coordination (неделя 3-4)

**Темы:**
- Paxos (включать Multi-Paxos)
- Raft (Election, Log Replication, Membership Changes)
- ZAB (Zookeeper)
- Distributed Transactions (2PC, 3PC, Saga pattern)
- Distributed Locks (Redis Redlock, Zookeeper, etcd)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| The Raft Paper | Paper | 2 часа | [raft.github.io/raft.pdf](https://raft.github.io/raft.pdf) |
| Raft Visualization | Интерактив | 1 час | [thesecretlivesofdata.com/raft](http://thesecretlivesofdata.com/raft/) |
| MIT 6.824 — Raft Lab | Лабораторная | 20 часов | [pdos.csail.mit.edu/6.824/labs/lab-raft.html](https://pdos.csail.mit.edu/6.824/labs/lab-raft.html) |
| etcd Raft implementation | Код | 5 часов | [github.com/etcd-io/raft](https://github.com/etcd-io/raft) |

**Pet Project:**
- Написать Raft implementation на Go (или Kotlin)
- Не production-ready, но working consensus
- Тесты: leader election, log replication, failure recovery

**Output:** GitHub repo + пост: "Пишем Raft за выходные: что я узнал про distributed consensus"

### 3. Storage Systems (неделя 5-6)

**Темы:**
- LSM Trees (RocksDB, LevelDB, Cassandra)
- B-Trees (PostgreSQL, MySQL)
- SSTables, MemTables
- Write-Ahead Log (WAL)
- MVCC (Multi-Version Concurrency Control)
- Time-Series DB (ClickHouse internals, TimescaleDB)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| DDIA — Ch. 3 (Storage) | Книга | 5 часов | [Amazon](https://amazon.com) |
| Designing High-Performance Database Systems | Paper | 2 часа | [Google Scholar](https://scholar.google.com) |
| ClickHouse Architecture | Документация | 3 часа | [clickhouse.com/docs](https://clickhouse.com/docs) |
| RocksDB Wiki | Документация | 2 часа | [github.com/facebook/rocksdb/wiki](https://github.com/facebook/rocksdb/wiki) |

**Output:** Пост: "LSM Tree vs B-Tree: почему ClickHouse выбрал именно это"

### 4. Messaging и Streaming (неделя 7)

**Темы:**
- Kafka internals (partitions, replication, ISR, exactly-once semantics)
- NATS, Pulsar
- Event Sourcing
- CQRS
- Backpressure

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| Kafka: The Definitive Guide | Книга | 10 часов | [Amazon](https://amazon.com) |
| Confluent Blog | Статьи | 5 часов | [confluent.io/blog](https://www.confluent.io/blog) |
| DDIA — Ch. 11 (Stream Processing) | Книга | 5 часов | [Amazon](https://amazon.com) |

**Output:** Пост: "Kafka Exactly-Once: теория и production практика"

### 5. System Design Case Studies (неделя 8-10)

**Практика:**
- Нарисовать систему для каждого сценария
- Объяснить trade-offs
- Масштабировать до 1B events/day

**Case Studies:**
```
1. URL Shortener (TinyURL)
2. Design Twitter / News Feed
3. Design WhatsApp / Chat System
4. Design Uber / Ride-Sharing
5. Design Rate Limiter
6. Design Web Crawler
7. Design Pastebin
8. Design Key-Value Store (Dynamo / Cassandra)
9. Design YouTube / Video Streaming
10. Design Payment System
11. Design ClickHouse from scratch (твой опыт!)
12. Design AI Inference Platform (твой AI angle)
```

**Ресурсы для case studies:**

| Ресурс | Тип | Ссылка |
|--------|-----|--------|
| System Design Primer | GitHub | [github.com/donnemartin/system-design-primer](https://github.com/donnemartin/system-design-primer) |
| ByteByteGo — System Design Interview | YouTube | [youtube.com/@ByteByteGo](https://www.youtube.com/@ByteByteGo) |
| System Design Interview (Alex Xu) | Книга | [Amazon](https://amazon.com) |
| System Design Interview Volume 2 | Книга | [Amazon](https://amazon.com) |
| Designing Data-Intensive Applications | Книга | [Amazon](https://amazon.com) |
| High Scalability Blog | Статьи | [highscalability.com](http://highscalability.com) |

**Output:** Каждый case study → пост на Habr с архитектурной диаграммой

### 6. Kubernetes и Cloud-Native (неделя 11-12)

**Темы:**
- Kubernetes internals (etcd, API server, scheduler)
- Service Mesh (Istio, Linkerd)
- Observability (Prometheus, Grafana, Jaeger, OpenTelemetry)
- GitOps (ArgoCD, Flux)
- eBPF

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| Kubernetes: Up and Running | Книга | 10 часов | [Amazon](https://amazon.com) |
| Kubernetes Documentation | Docs | 5 часов | [kubernetes.io/docs](https://kubernetes.io/docs) |
| The Kubernetes Book | Nigel Poulton | 8 часов | [Amazon](https://amazon.com) |
| CNCF Landscape | Карта | 2 часа | [landscape.cncf.io](https://landscape.cncf.io) |
| Prometheus + Grafana Tutorial | Tutorial | 3 часа | [prometheus.io/docs](https://prometheus.io/docs) |

**Output:** Пост: "Kubernetes для backend-разработчика: что нужно знать, чтобы не бояться"

---

## Книги (must-read)

| Книга | Автор | Почему | Где |
|-------|-------|--------|-----|
| Designing Data-Intensive Applications | Martin Kleppmann | **Библия**. Всё, что нужно знать о distributed systems. | [Amazon](https://amazon.com) |
| System Design Interview | Alex Xu | Практика собеседований. Case studies. | [Amazon](https://amazon.com) |
| System Design Interview Vol. 2 | Alex Xu | Больше case studies. | [Amazon](https://amazon.com) |
| Kubernetes: Up and Running | Brendan Burns | K8s для production. | [Amazon](https://amazon.com) |
| Database Internals | Alex Petrov | Как работают БД изнутри. | [Amazon](https://amazon.com) |
| Understanding Distributed Systems | Roberto Vitillo | Коротко и понятно. | [Amazon](https://amazon.com) |

---

## Курсы

| Курс | Платформа | Время | Ссылка |
|------|-----------|-------|--------|
| MIT 6.824 Distributed Systems | MIT OCW (бесплатно) | 12 лекций | [pdos.csail.mit.edu/6.824](https://pdos.csail.mit.edu/6.824/) |
| CMU 15-440 Distributed Systems | CMU (бесплатно) | 20 лекций | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLSE8ODhjZXjYVdQaYeGNkifLR5vCH_8RF) |
| Stanford CS244B | Stanford (бесплатно) | 15 лекций | [web.stanford.edu/class/cs244b](https://web.stanford.edu/class/cs244b/) |
| ByteByteGo System Design | ByteByteGo | 20 часов | [bytebytego.com](https://bytebytego.com) |
| System Design Primer | GitHub (бесплатно) | 10 часов | [github.com/donnemartin/system-design-primer](https://github.com/donnemartin/system-design-primer) |

---

## Pet Projects с distributed systems

### Project 1: Distributed Key-Value Store
- **Stack:** Go / Kotlin
- **Features:** Raft consensus, sharding, replication
- **Scale:** Handles 10K requests/second locally
- **Output:** GitHub repo + Habr post
- **Time:** 2-3 weeks

### Project 2: URL Shortener with Analytics
- **Stack:** Go, Redis, PostgreSQL, Kafka
- **Features:** Distributed counters, analytics pipeline, rate limiting
- **Output:** GitHub repo + live demo
- **Time:** 1-2 weeks

### Project 3: Real-Time Chat (WebSocket + distributed)
- **Stack:** Go, Redis pub/sub, PostgreSQL
- **Features:** Horizontal scaling, message persistence, presence
- **Output:** GitHub repo + Habr post
- **Time:** 2 weeks

### Project 4: Distributed Task Queue
- **Stack:** Go, Redis, PostgreSQL
- **Features:** At-least-once delivery, retries, dead letter queue
- **Output:** GitHub repo
- **Time:** 1-2 weeks

---

## Трекер: 12-недельный план

| Неделя | Фокус | Output |
|--------|-------|--------|
| 1 | DDIA Ch. 1-3, CAP Theorem | Пост: "CAP в production" |
| 2 | Replication, Partitioning, Consistency | Пост: "Consistency Models простыми словами" |
| 3 | Raft paper + visualization | Начать Raft implementation |
| 4 | Raft implementation (Go) | GitHub repo + пост |
| 5 | Storage: LSM Tree, B-Tree | Пост: "ClickHouse storage internals" |
| 6 | Storage: ClickHouse deep dive | Архитектурная диаграмма |
| 7 | Kafka internals, Stream Processing | Пост: "Exactly-Once в Kafka" |
| 8 | System Design Case Study #1-2 | URL Shortener + Twitter |
| 9 | System Design Case Study #3-4 | Uber + Payment System |
| 10 | System Design Case Study #5-6 | Key-Value Store + Web Crawler |
| 11 | Kubernetes internals | Пост: "K8s для бэкендера" |
| 12 | Observability, GitOps | Пост: "Observability: metrics vs logs vs traces" |

---

**Последнее обновление:** 16 May 2026
