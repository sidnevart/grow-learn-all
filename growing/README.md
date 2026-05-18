# Roadmap роста: от Mid к Senior / Top Engineer

> **Для кого:** Backend/Platform Engineer с 3+ годами опыта, цель — top-tier компании, top-вузы, видимость
> **Время:** 6-12 месяцев интенсивного роста
> **Формат:** Самостоятельное обучение + production-применение + публичный вывод

---

## Глобальная картина

У тебя сильная практическая база: production systems, метрики, open-source. Но до top-tier (Google, Netflix, Stripe, top-вузы) не хватает:

| Что есть | Чего не хватает | Как заполнить |
|----------|----------------|---------------|
| Production Java/Kotlin/Go | Формальная алгоритмическая глубина | LeetCode + MIT 6.006 + книги |
| 30M txns/day | System design для 1B+ | Pet project + теория + посты |
| Open-source проекты | Real users + retention metrics | Запуск SaaS / Telegram-бот |
| Self-taught AI tools | Математика для AI/ML | Linear algebra, probability, optimization |
| ClickHouse, Kafka | Formal distributed systems theory | Raft, consensus, CAP theorem в depth |
| Great metrics ($600K+) | Публичный voice | Habr, YouTube, конференции |
| Solo execution | Leadership + mentorship | Формально менторить, lead initiatives |

---

## Структура папки

| Файл | Тема | Время |
|------|------|-------|
| [algorithms.md](./algorithms.md) | Алгоритмы и структуры данных | 3-4 месяца |
| [system_design.md](./system_design.md) | Distributed Systems и System Design | 2-3 месяца |
| [math_for_ai.md](./math_for_ai.md) | Математика для AI/ML/физического AI | 4-6 месяцев |
| [public_voice.md](./public_voice.md) | Публичный voice, блог, выступления | Постоянно |
| [research.md](./research.md) | Исследования, публикации, arXiv | 3-6 месяцев |
| [pet_projects.md](./pet_projects.md) | Pet projects с real users | 2-3 месяца |
| [soft_skills.md](./soft_skills.md) | Leadership, mentorship, собеседования | Постоянно |
| [tracker.md](./tracker.md) | Трекер прогресса по неделям | Обновлять еженедельно |
| [study-os/](./study-os/) | Мост между roadmap и execution (t-rost-study) | Стартовать отсюда |

---

## Приоритеты по времени

### Ближайшие 2 месяца (май — июль 2026)
- [ ] LeetCode: 100 задач (medium/hard) — [algorithms.md](./algorithms.md)
- [ ] MIT 6.006: первые 10 лекций + problem sets
- [ ] Написать 2 tech-поста (Habr или dev.to) — [public_voice.md](./public_voice.md)
- [ ] Запросить mentorship role в T-Bank — [soft_skills.md](./soft_skills.md)
- [ ] Определить pet project для запуска — [pet_projects.md](./pet_projects.md)

### 3-4 месяца (август — октябрь 2026)
- [ ] LeetCode: еще 100 задач (focus: graphs, DP, system design)
- [ ] Запустить pet project с real users
- [ ] Написать 1 system design case study (например, "How I'd redesign T-Bank for 1B txns")
- [ ] Начать math track (linear algebra) — [math_for_ai.md](./math_for_ai.md)
- [ ] Сделать 1 tech talk (YouTube или митап)
- [ ] Получить 3 LinkedIn recommendations

### 5-6 месяцев (ноябрь — декабрь 2026)
- [ ] Закончить MIT 6.006 полностью
- [ ] Запустить arXiv paper draft — [research.md](./research.md)
- [ ] Pet project: 1000+ users
- [ ] Linear Algebra + Probability: базовый уровень
- [ ] Системный дизайн: 5 case studies
- [ ] Выступить на конференции/митапе

### 7-12 месяцев (январь — май 2027)
- [ ] Архивировать paper на arXiv
- [ ] Advanced system design (Raft implementation, sharding)
- [ ] Math: оптимизация, calculus
- [ ] 10+ публичных постов / talks
- [ ] Подать на стипендии и вузы

---

## Как использовать эту папку

1. **Читай README** — понять картину
2. **Открой [study-os/README.md](./study-os/README.md)** — это твой портал между roadmap и execution
3. **Выбери 2-3 направления** из приоритетов выше
4. **Открой конкретный файл** — там пошаговый план
5. **Обновляй tracker.md** каждую неделю (используй [sprint-bridge.md](./study-os/sprint-bridge.md) как шаблон)
6. **Не пытайся всё сразу** — лучше глубоко 2 направления, чем поверхностно 8

## Как это связано с t-rost-study

- `growing/` — отвечает на вопрос **что** учить и **зачем**.
- [`t-rost-study`](https://github.com/sidnevart/t-rost-study) — отвечает на вопрос **как** учить: tracks, sprints, artifacts, книги.
- `study-os/` — мост между ними: матрица соответствия, sprint-шаблон, список тем без покрытия.

Правило: открывай `study-os/mapping.md` → находишь свою тему → идёшь в `t-rost-study` за execution или в `external-only-topics.md` за самостоятельным планом.

---

## Золотое правило

**Каждый learning должен заканчиваться output:**
- Прочитал про Raft → написал post на Habr
- Решил 50 задач LeetCode → сделал mock interview с другом
- Изучил ClickHouse internals → сделал tech talk
- Построил pet project → получил real users + метрики

**Output > Input.** Топ-компании нанимают по тому, что ты **сделал**, не по тому, что ты **прочитал**.

---

**Последнее обновление:** 16 May 2026
