# Mapping: growing/ → t-rost-study

> Матрица соответствия. Для каждой темы из `growing/` указано, где она пересекается с `t-rost-study` (track, sprint, книга), а где учится отдельно.

## Легенда

- **Track** — learning track из `t-rost-study/04-learning-tracks/`
- **Sprint** — weekly sprint из `t-rost-study/05-weekly-sprints/`
- **Book** — книга из `t-rost-study/03-books/01-reading-plan-12-months.md`
- **External** — тема не покрывается `t-rost-study`, учится самостоятельно (см. `external-only-topics.md`)

---

## Общая таблица

| Growing Topic | t-rost-study Track | Sprint | Book / Resource | Notes |
|---------------|-------------------|--------|-----------------|-------|
| [Алгоритмы](../algorithms.md) | Track 06 (DAG algorithms), Track 09 (bitmap/index) | Sprint 8 | CLRS (month 9), MIT 6.006 (external) | Алгоритмы в t-rost-study — прикладные: DAG scheduling, bitmap ops, inverted index. Абстрактный LeetCode — external. |
| [System Design](../system_design.md) | Tracks 01–08 (A-P, Target, TQ, CH, cache, coordination) | Sprints 1–7 | DDIA (months 1, 5, 7) | t-rost-study — это system design в production: реальные системы, реальные trade-off. |
| [Math for AI](../math_for_ai.md) | — | — | External only | Не покрывается t-rost-study (work-focused). Учить отдельно по `math_for_ai.md`. |
| [Public Voice](../public_voice.md) | Track 12 (business/product) | Final RFC | — | Output: RFC, посты, CFP. Использовать `public_voice.md` для платформ (Habr, YouTube, конференции). |
| [Research](../research.md) | Final RFC (07-final-rfc) | Sprints 7–8 | — | Финальный RFC в t-rost-study — это research artifact. `research.md` добавляет arXiv и paper writing. |
| [Pet Projects](../pet_projects.md) | 06-practice/experiments | Любой sprint | — | Идеи проектов — в `pet_projects.md`. Execution — через t-rost-study templates (benchmark, RFC). |
| [Soft Skills](../soft_skills.md) | Track 12 (business/product) | — | Inspired, High Output Management, Team Topologies, Empowered | Leadership и бизнес-треки + книги в t-rost-study. Mock interviews — external. |

---

## Детальный breakdown по темам

### 1. Алгоритмы ([algorithms.md](../algorithms.md))

**В t-rost-study:**
- Track 06 — DAG algorithms (topological sort, critical path). Прямое применение к задаче `getAvailableTasks` в TQ.
- Track 09 — Bitmap & inverted index serving. Алгоритмы работы с bitmap-индексами.
- Sprint 8 — эксперимент с bitmap и critical path.

**Что делать:**
- Если цель — прокачать алгоритмическое мышление на production-задачах → Track 06, 09 + Sprint 8.
- Если цель — закрыть gap до Google/Netflix интервью → MIT 6.006 + LeetCode (external, см. `external-only-topics.md`).

**Книги:**
- DDIA, глава 3 (Storage) — B-tree, LSM (month 1)
- CLRS, графы (month 9)

---

### 2. System Design ([system_design.md](../system_design.md))

**В t-rost-study — полное покрытие:**
- Track 01 — Audience Platform domain (что такое аудитория, lifecycle, DSL)
- Track 02 — Target integration (контракты, API)
- Track 03 — TQ Kotlin coroutines (concurrency, scheduling)
- Track 04 — PostgreSQL queues (LISTEN/NOTIFY, MVCC)
- Track 05 — Distributed coordination (locks, leader election)
- Track 06 — DAG algorithms & critical path
- Track 07 — ClickHouse performance (OLAP, column-oriented)
- Track 08 — Data locality & S3 pushdown
- Track 09 — Bitmap & inverted index serving
- Track 10 — Cache & incremental CDC
- Track 11 — JVM/Go performance

**Sprints:**
- Sprint 1 — AP end-to-end map
- Sprint 2 — Target contract
- Sprint 3 — Compute/export/delivery split
- Sprint 4 — Graph vs SQL vs Bitmap vs Cache
- Sprint 5 — TQ coroutines
- Sprint 6 — Postgres queue
- Sprint 7 — ClickHouse baseline
- Sprint 8 — Bitmap experiment

**Книги:**
- DDIA (months 1, 5, 7) — главы 1, 3, 5, 7, 8, 9, 11
- ClickHouse Definitive Guide (month 7)
- Systems Performance, Brendan Gregg (month 8)
- Java Concurrency in Practice (month 10)

---

### 3. Math for AI ([math_for_ai.md](../math_for_ai.md))

**В t-rost-study — не покрывается.**

Это осознанный gap: t-rost-study заточен под production backend/platform engineering, а не под AI research.

**Что делать:**
- Linear Algebra → MIT 18.06 / 3Blue1Brown
- Probability → MIT 6.041 / Bertsekas
- Optimization → Boyd & Vandenberghe
- См. `external-only-topics.md` для конкретного плана.

---

### 4. Public Voice ([public_voice.md](../public_voice.md))

**В t-rost-study — частично:**
- Track 12 — Business/product (позиционирование, pitching)
- Final RFC — артефакт, который можно опубликовать
- Books: Inspired, Obviously Awesome, Good Strategy/Bad Strategy, Sales Acceleration Formula — все про то, как доносить мысли

**Что делать:**
- Использовать `public_voice.md` для выбора платформы (Habr, YouTube, конференция).
- Использовать t-rost-study для создания контента: RFC, benchmark reports, architecture posts — все это материал для public voice.
- Каждый sprint должен заканчиваться не "прочитал", а артефактом — этот артефакт можно опубликовать.

---

### 5. Research ([research.md](../research.md))

**В t-rost-study — финальный RFC:**
- 07-final-rfc/ — структура итогового предложения
- Sprint 7–8 — эксперименты, которые становятся данными для RFC

**Что делать:**
- t-rost-study дает execution framework (как провести исследование, как оформить RFC).
- `research.md` дает high-level цели (arXiv paper, conference submission).
- Итоговый RFC из t-rost-study — это первый draft для публикации.

---

### 6. Pet Projects ([pet_projects.md](../pet_projects.md))

**В t-rost-study — через experiments:**
- 06-practice/experiments/ — шаблоны для прототипирования
- Benchmark template, RFC template — использовать для pet project

**Что делать:**
- Идеи — в `pet_projects.md` (StudyBuddy AI, etc.).
- Execution — через t-rost-study: MVP → benchmark → RFC-фрагмент.
- Pet project тоже должен заканчиваться артефактом, а не только "запустил".

---

### 7. Soft Skills ([soft_skills.md](../soft_skills.md))

**В t-rost-study — через business tracks и книги:**
- Track 12 — Business/product/sales leadership
- Books: Inspired, High Output Management, Team Topologies, Empowered, Continuous Discovery Habits

**External:**
- Mock interviews — не покрываются t-rost-study. См. `external-only-topics.md`.
- Формальное менторство — external.

**Что делать:**
- Leadership: волонтериться на lead роли в проектах → оформлять как RFC через t-rost-study.
- Mock interviews — внешние платформы (Pramp, interviewing.io).

---

## Быстрые ссылки на t-rost-study

| Ресурс | Ссылка |
|--------|--------|
| Index / карта | [00-index.md](https://github.com/sidnevart/t-rost-study/blob/main/00-index.md) |
| Learning Tracks | [04-learning-tracks/](https://github.com/sidnevart/t-rost-study/tree/main/04-learning-tracks) |
| Weekly Sprints | [05-weekly-sprints/](https://github.com/sidnevart/t-rost-study/tree/main/05-weekly-sprints) |
| 12-month Reading Plan | [03-books/01-reading-plan-12-months.md](https://github.com/sidnevart/t-rost-study/blob/main/03-books/01-reading-plan-12-months.md) |
| Practice / Experiments | [06-practice/](https://github.com/sidnevart/t-rost-study/tree/main/06-practice) |
| Final RFC | [07-final-rfc/](https://github.com/sidnevart/t-rost-study/tree/main/07-final-rfc) |
| GPT Prompts | [gpt-prompts.md](https://github.com/sidnevart/t-rost-study/blob/main/gpt-prompts.md) |
