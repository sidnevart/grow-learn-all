# Pet Projects с real users

> **Цель:** Показать, что ты можешь строить продукты, не только писать код
> **Формат:** MVP → users → metrics → iterate
> **Метрика:** 1000+ users, retention, revenue (опционально)

---

## Почему это важно

| Только CV | CV + pet project |
|-----------|------------------|
| "Работал в команде" | "Построил продукт с 1000 пользователями" |
| Теоретические навыки | Доказанные product skills |
| Одинаковый с другими | Уникальный опыт |

Топ-компании и вузы ценят:
- **End-to-end thinking** (от идеи до production)
- **User empathy** (решил реальную проблему)
- **Metrics-driven** (измерял результат)
- **Resilience** (дошел до конца, не бросил)

---

## Идеи проектов

### 1. AI-ассистент для учебы (StudyBuddy AI)

**Проблема:** Студенты тратят часы на поиск материалов, составление конспектов, подготовку к экзаменам

**Решение:**
- Загружаешь PDF/лекции → AI делает summary
- Генерирует flashcards для запоминания
- Создает practice questions
- Отслеживает прогресс

**Стек:**
- Frontend: Next.js + Tailwind
- Backend: Python + FastAPI
- AI: OpenAI API / Claude API
- DB: PostgreSQL + pgvector
- Deploy: Vercel + Railway

**Монетизация:** Freemium ($5/месяц за advanced features)

**Метрики:**
- 1000+ users
- 20% weekly retention
- $500 MRR

---

### 2. Telegram-бот для трекинга привычек (HabitTracker Bot)

**Проблема:** Приложения для привычек сложные, требуют установки

**Решение:**
- Telegram-бот: просто пишешь "выпил воды"
- AI напоминает, анализирует паттерны
- Геймификация: streaks, challenges
- Интеграция с Google Calendar

**Стек:**
- Bot: Python + aiogram
- Backend: Go / Python
- DB: PostgreSQL
- AI: OpenAI API для анализа
- Deploy: VPS / Railway

**Монетизация:**
- Бесплатно: базовый трекинг
- Premium ($3/мес): AI insights, advanced analytics

**Метрики:**
- 2000+ users
- 30% daily active
- $300 MRR

---

### 3. Distributed Systems Playground (DS Playground)

**Проблема:** Изучать distributed systems сложно, нет интерактивных инструментов

**Решение:**
- Веб-приложение: визуализация Raft, Paxos, consensus
- Можно "запустить" кластер, убить ноды, посмотреть recovery
- Интерактивные упражнения
- Code challenges (реализуй leader election)

**Стек:**
- Frontend: React + D3.js (визуализация)
- Backend: Go (simulation engine)
- DB: PostgreSQL
- Deploy: Vercel + Fly.io

**Монетизация:**
- Бесплатно: базовые симуляции
- Pro ($10/мес): advanced scenarios, code challenges

**Метрики:**
- 500+ users (students, engineers)
- Используется в 2+ университетах
- 1000+ GitHub stars

---

### 4. Personal Finance AI (FinanceAI)

**Проблема:** Люди не понимают, куда уходят деньги

**Решение:**
- Подключаешь банковские выписки (CSV)
- AI категоризирует траты
- Прогнозирует бюджет
- Дает рекомендации по экономии

**Стек:**
- Frontend: Next.js
- Backend: Python + FastAPI
- AI: OpenAI / Claude для анализа
- DB: PostgreSQL
- Deploy: Vercel + Railway

**Монетизация:** Freemium

---

### 5. Code Interview Prep Platform (InterviewPrep)

**Проблема:** Подготовка к собеседованиям хаотична

**Решение:**
- Персонализированный план подготовки
- AI-мок interview (голосовой бот)
- Отслеживание прогресса
- Community для mock interviews

**Стек:**
- Frontend: Next.js
- Backend: Go / Python
- AI: Whisper (STT) + GPT-4 (ответы) + ElevenLabs (TTS)
- DB: PostgreSQL

---

## Критерии выбора проекта

Проверь свою идею:

| Критерий | Важность | Вопрос |
|----------|----------|--------|
| Личная проблема | Высокая | "Я бы сам этим пользовался?" |
| Решаем за 2-3 месяца | Высокая | "Можно ли сделать MVP за 8-12 недель?" |
| Масштабируется | Средняя | "Могут ли 1000+ людей использовать?" |
| AI angle | Бонус | "Можно ли добавить AI для ценности?" |
| Монетизируется | Бонус | "Будут ли люди платить?" |

---

## План запуска (12 недель)

### Недели 1-2: Idea + Validation

- [ ] Определить проблему
- [ ] Опросить 10 потенциальных пользователей
- [ ] Написать MVP scope (1-2 core features)
- [ ] Выбрать стек

### Недели 3-6: MVP

- [ ] Настроить проект
- [ ] Реализовать core features
- [ ] Deploy
- [ ] Протестировать с 5 друзьями

### Недели 7-8: Launch

- [ ] Опубликовать на Product Hunt
- [ ] Рассказать в соцсетях
- [ ] Написать пост на Habr/dev.to
- [ ] Поделиться в Telegram-каналах

### Недели 9-12: Iterate

- [ ] Собирать feedback
- [ ] Считать метрики
- [ ] Дорабатывать
- [ ] Планировать monetization

---

## Метрики для отслеживания

| Метрика | Цель 3 мес | Цель 6 мес |
|---------|------------|------------|
| Users | 100 | 1000 |
| DAU/MAU | 10% | 20% |
| Retention (7-day) | 15% | 25% |
| NPS | — | 30+ |
| Revenue | $0 | $100-500 MRR |

---

## Ресурсы

| Ресурс | Для чего |
|--------|----------|
| "The Lean Startup" (Eric Ries) | Валидация идей |
| "Zero to One" (Peter Thiel) | Продуктовое мышление |
| Indie Hackers | Сообщество solo founders |
| Product Hunt | Платформа для запуска |
| Stripe Atlas | Инкорпорация + платежи |
| Supabase / Railway | Быстрый backend deploy |

---

## Чеклист

- [ ] Выбрать идею
- [ ] Провалидировать с 10 людьми
- [ ] Написать MVP
- [ ] Задеплоить
- [ ] Получить первых 10 users
- [ ] Запустить на Product Hunt
- [ ] 100 users
- [ ] Добавить analytics
- [ ] 1000 users
- [ ] Monetize (опционально)

---

**Последнее обновление:** 16 May 2026
