# External-Only Topics

> Темы из `growing/`, которые **не покрываются** `t-rost-study` и учатся самостоятельно.
> Для каждой темы — why, what, how, и конкретные ресурсы.

---

## 1. Math for AI / ML / Physical AI

**Why:** t-rost-study — work-focused backend/platform learning. Математика для AI нужна для:
- Top AI research/engineering ролей (OpenAI, Anthropic, DeepMind)
- Physical AI / Robotics (Tesla Optimus, Figure AI)
- MS/PhD в AI (MIT, Stanford, CMU)

**What:**
- Linear Algebra (векторы, матрицы, SVD, PCA, eigenvalues)
- Probability & Statistics (Bayes, distributions, hypothesis testing)
- Calculus & Optimization (gradients, convex optimization, Lagrange)

**How:**

| Тема | Ресурс | Формат | Время | Артефакт |
|------|--------|--------|-------|----------|
| Linear Algebra | MIT 18.06 (Gilbert Strang) | Видео + notes | 4 недели | Решить 5 задач из problem sets, написать summary |
| Linear Algebra (visual) | 3Blue1Brown — Essence of LA | Видео | 1 неделя | Схема: как LA применяется к transformers |
| Probability | MIT 6.041 (Tsitsiklis) | Видео + notes | 4 недели | 10 задач, 1 summary post |
| Optimization | Boyd & Vandenberghe (Convex Optimization) | Книга + exercises | 6 недель | Реализовать 1 алгоритм (gradient descent) на Python |
| Математика transformers | "Attention Is All You Need" + разбор формул | Paper | 1 неделя | Нарисовать, как attention = softmax(QK^T/sqrt(d)) |

**Расписание (примерное):**
- Недели 1–4: Linear Algebra
- Недели 5–8: Probability
- Недели 9–14: Optimization
- Недели 15–16: Математика transformers

**Интеграция с t-rost-study:**
- Математику можно учить параллельно с t-rost-study tracks, но как **отдельный трек**.
- Использовать тот же принцип: каждый день заканчивается задачей или summary, не "прочитал".

---

## 2. LeetCode Grind (абстрактные алгоритмы)

**Why:** t-rost-study учит алгоритмы **в контексте** (DAG scheduling, bitmap ops), но не учит решать 45-минутные интервью-задачи. Для Google/Netflix/Stripe нужен отдельный LeetCode трек.

**What:**
- Two Pointers, Sliding Window
- Binary Search, BFS/DFS
- Dynamic Programming
- Graphs (shortest path, topological sort)
- Bit Manipulation

**How:**

| Фаза | Время | Задач | Ресурс |
|------|-------|-------|--------|
| Основы (Arrays, Hash Maps) | 2 недели | 20 задач | LeetCode Patterns |
| Структуры данных | 2 недели | 20 задач | LeetCode Patterns |
| Advanced (DP, Graphs) | 4 недели | 40 задач | MIT 6.006 + LeetCode |
| Hard + Mock | 2 недели | 20 задач | Pramp / interviewing.io |

**Расписание:**
- Будни: 1 час утром (2-3 задачи)
- Выходные: 2 часа (разбор сложных задач + mock)

**Интеграция с t-rost-study:**
- LeetCode — morning routine, независимый от t-rost-study.
- Но: когда в t-rost-study попадаешь на Track 06 (DAG), LeetCode графы закрываются автоматически.

---

## 3. Public Voice Campaigns (Habr, YouTube, Конференции)

**Why:** t-rost-study дает контент (RFC, benchmark, architecture), но не учит, как его упаковать для аудитории.

**What:**
- Habr: технические посты
- YouTube: разборы систем / tutorials
- Конференции: CFP, подача, презентация
- dev.to / Medium: англоязычная аудитория

**How:**

| Платформа | Частота | Формат | Метрика |
|-----------|---------|--------|---------|
| Habr | 1-2/мес | Разбор production-задачи | 100→500→1000 подписчиков |
| YouTube | 1/мес | Tutorial / разбор системы | 100→1000 просмотров |
| Конференция | 1/квартал | CFP + talk | 1 принятый CFP |
| dev.to | 1-2/мес | Перевод / оригинал | followers |

**Интеграция с t-rost-study:**
- Каждый артефакт t-rost-study (RFC, benchmark, architecture decision) — это потенциальный пост.
- После Sprint 8 (bitmap experiment) → пост "Как мы ускорили выборку аудиторий в 10x".
- После Final RFC → talk на внутреннем meetup → потом на внешней конференции.

---

## 4. Mock Interviews

**Why:** t-rost-study не покрывает собеседования. Soft skills файл упоминает их, но без execution plan.

**How:**

| Тип | Частота | Платформа | Notes |
|-----|---------|-----------|-------|
| Behavioral | 1/неделю | С другом / ментором | STAR формат |
| System Design | 1/2 недели | Pramp / interviewing.io | Использовать case studies из `growing/system_design.md` |
| Algorithms | 1/неделю | Pramp / LeetCode mock | Совмещать с LeetCode grind |
| Coding (live) | 1/2 недели | interviewing.io | Kotlin / Go / Java |

**Интеграция с t-rost-study:**
- System Design mock — используй реальные задачи из t-rost-study (AP architecture, TQ scheduling).
- Это дает преимущество: ты обсуждаешь систему, которую реально знаешь end-to-end.

---

## 5. Formal Mentorship

**Why:** Soft skills файл говорит "менторить", но не дает плана.

**How:**

| Роль | Как начать | Метрика |
|------|-----------|---------|
| Менти | Найти ментора через компанию или ADPList | 1 встреча/2 недели |
| Ментор | Волонтериться в компании или open-source | 1 менти, 1 встреча/неделю |

**Интеграция с t-rost-study:**
- Обсуждай t-rost-study tracks с ментором.
- Ментор может дать feedback на RFC перед финальной подачей.

---

## Чек-лист: что учить где

| Тема | Где | Ссылка |
|------|-----|--------|
| System Design, Backend, Distributed | t-rost-study | [sidnevart/t-rost-study](https://github.com/sidnevart/t-rost-study) |
| Math for AI | External | [math_for_ai.md](../math_for_ai.md) + этот файл |
| LeetCode (интервью) | External | [algorithms.md](../algorithms.md) + этот файл |
| Public Voice | External (content из t-rost-study) | [public_voice.md](../public_voice.md) + этот файл |
| Research (arXiv) | External (RFC из t-rost-study как draft) | [research.md](../research.md) + t-rost-study Final RFC |
| Pet Projects | External (execution через t-rost-study templates) | [pet_projects.md](../pet_projects.md) + t-rost-study experiments |
| Soft Skills (mock, mentorship) | External | [soft_skills.md](../soft_skills.md) + этот файл |
| Business/Leadership | t-rost-study (Track 12 + книги) | [t-rost-study Track 12](https://github.com/sidnevart/t-rost-study/tree/main/04-learning-tracks) |
