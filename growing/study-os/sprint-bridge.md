# Sprint Bridge — Еженедельный шаблон

> Этот файл объединяет milestones из `tracker.md` и execution-формат `t-rost-study`.
> Каждую неделю скопируй шаблон ниже и заполни.

## Принцип

Ни один день не заканчивается "прочитал". Только конкретный артефакт: бенчмарк, query, RFC-фрагмент, domain map, decision note.

---

## Week of: [DATE]

### Milestones этой недели (из tracker.md)

| Направление | Цель недели | Статус |
|-------------|-------------|--------|
| Алгоритмы | X задач LeetCode | |
| System Design | [track/sprint] | |
| Public Voice | [пост / talk / draft] | |
| Pet Project | [фича / users] | |
| Soft Skills | [mock / mentorship] | |

### Активный t-rost-study Sprint

- **Sprint:** [sprint-NN-name](https://github.com/sidnevart/t-rost-study/tree/main/05-weekly-sprints)
- **Track:** [Track NN — Name](https://github.com/sidnevart/t-rost-study/tree/main/04-learning-tracks)
- **Книга месяца:** [Book Title](https://github.com/sidnevart/t-rost-study/blob/main/03-books/01-reading-plan-12-months.md)
- **Цель спринта:** (скопировать из sprint файла)

### Daily Execution

| День | Артефакт | Статус | Notes |
|------|----------|--------|-------|
| Пн | | | |
| Вт | | | |
| Ср | | | |
| Чт | | | |
| Пт | | | |
| Сб | [книга / эксперимент] | | |
| Вс | [книга / reflection] | | |

### Weekly Reflection

#### Что сделано:
1.
2.
3.

#### Что не сделано и почему:
1.

#### Артефакты недели (линки):
- RFC-фрагмент:
- Benchmark / Query:
- Пост / Draft:
- Код / PR:

#### Insight недели:

#### Energy level (1-10):

#### Фокус на следующей неделе:

---

## Пример заполненной недели

### Week of: 19 May 2026

#### Milestones этой недели (из tracker.md)

| Направление | Цель недели | Статус |
|-------------|-------------|--------|
| Алгоритмы | 6 задач LeetCode (Two Pointers) | ✅ |
| System Design | Sprint 1 — AP end-to-end map | 🔄 |
| Public Voice | Habr пост draft | ❌ |

#### Активный t-rost-study Sprint

- **Sprint:** [sprint-01-ap-end-to-end-map](https://github.com/sidnevart/t-rost-study/blob/main/05-weekly-sprints/sprint-01-ap-end-to-end-map.md)
- **Track:** [Track 01 — Audience Platform Domain](https://github.com/sidnevart/t-rost-study/blob/main/04-learning-tracks/01-audience-platform-domain.md)
- **Книга месяца:** Designing Data-Intensive Applications (DDIA), гл. 1, 3
- **Цель спринта:** Нарисовать end-to-end flow аудитории от запроса до доставки, найти 3+ узких места

#### Daily Execution

| День | Артефакт | Статус | Notes |
|------|----------|--------|-------|
| Пн | LeetCode 3 задачи (Two Pointers) | ✅ | 1. Two Sum, 2. 3Sum, 3. Container |
| Вт | AP domain map — Mermaid diagram | ✅ | Нарисовал lifecycle аудитории |
| Ср | LeetCode 3 задачи + trace kafka consumer | ✅ | Нашел consumer в A-P |
| Чт | DDIA гл. 1 + notes | ✅ | Термины: reliability, scalability, maintainability |
| Пт | RFC-фрагмент: compute-export-delivery split | ✅ | 2 страницы, нашел метрику "2-3 сек" |
| Сб | DDIA гл. 3 (Storage) | ✅ | B-tree vs LSM |
| Вс | Weekly reflection + планы | ✅ | |

#### Weekly Reflection

**Что сделано:**
1. LeetCode: 6 задач (цель недели — выполнена)
2. AP domain map: нарисовал lifecycle и state machine
3. RFC-фрагмент: compute-export-delivery split

**Что не сделано:**
1. Habr draft — не хватило времени, переношу на след. неделю

**Артефакты недели:**
- Mermaid diagram: `ap-lifecycle.mmd`
- RFC-фрагмент: `rfc-compute-export.md`

**Insight:** "2-3 секунды на аудиторию" — это compute, но export в S3 + delivery до Target занимает 10-30 сек. Нужно разделить метрики.

**Energy level:** 7/10

**Фокус на следующей неделе:** Sprint 2 — Target contract + LeetCode Sliding Window
