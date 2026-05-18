# Study OS — Мост между Roadmap и Execution

> Эта папка связывает два твоих инструмента развития: `growing/` (что учить и зачем) и `t-rost-study` (как учить и что делать каждый день).

## Архитектура двух систем

```
┌─────────────────────────────────────────────────────────────────┐
│                        growing/                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │ algorithms   │  │ system_design│  │ public_voice │  ...     │
│  │ (что учить)  │  │ (что учить)  │  │ (что учить)  │          │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘          │
│         │                 │                 │                   │
│         └─────────────────┴─────────────────┘                   │
│                           │                                     │
│                    study-os/mapping.md                          │
│                           │                                     │
│         ┌─────────────────┼─────────────────┐                 │
│         │                 │                 │                   │
│  ┌──────▼───────┐  ┌──────▼───────┐  ┌──────▼───────┐          │
│  │  t-rost-     │  │  t-rost-     │  │  t-rost-     │          │
│  │  study       │  │  study       │  │  study       │          │
│  │  (tracks)    │  │  (sprints)   │  │  (books)     │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
```

- **`growing/*.md`** — Roadmap. Отвечает на вопросы: что учить, зачем, к чему приведет, какие метрики успеха.
- **`t-rost-study`** (GitHub) — Execution engine. Отвечает на вопросы: с чего начать сегодня, какой артефакт сделать, какой sprint активен, какая книга сейчас читается.
- **`study-os/`** — Bridge. Матрица соответствия, sprint-bridge, и список тем, которые не покрыты t-rost-study и учатся отдельно.

## Файлы в этой папке

| Файл | Назначение |
|------|------------|
| [`mapping.md`](./mapping.md) | Матрица: каждая тема из `growing/` → track / sprint / книга в `t-rost-study` |
| [`sprint-bridge.md`](./sprint-bridge.md) | Еженедельный шаблон, объединяющий milestones из `tracker.md` и формат спринтов `t-rost-study` |
| [`external-only-topics.md`](./external-only-topics.md) | Темы из `growing/`, которых нет в `t-rost-study`, с рекомендациями, как их учить отдельно |

## Как пользоваться

1. Открой `mapping.md` — найди, какая тема из `growing/` тебя интересует.
2. Если у нее есть ссылка на `t-rost-study` — переходи в репозиторий, открывай track/sprint, работай.
3. Если у темы пометка "external only" — иди в `external-only-topics.md` за планом.
4. Каждую неделю открывай `sprint-bridge.md` как шаблон: скопируй секцию недели в `tracker.md` или в отдельный файл.
5. Обновляй `tracker.md` как high-level dashboard — он знает про обе системы.

## Ссылки

- [t-rost-study на GitHub](https://github.com/sidnevart/t-rost-study)
- [t-rost-study — Index (00-index.md)](https://github.com/sidnevart/t-rost-study/blob/main/00-index.md)
- [t-rost-study — Reading Plan](https://github.com/sidnevart/t-rost-study/blob/main/03-books/01-reading-plan-12-months.md)
- [t-rost-study — Weekly Sprints](https://github.com/sidnevart/t-rost-study/tree/main/05-weekly-sprints)
