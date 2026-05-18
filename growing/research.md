# Исследования, публикации, arXiv

> **Цель:** Добавить academic credibility для поступления в top-вузы и top AI-роли
> **Формат:** Paper draft → arXiv → conference submission
> **Время:** 3-6 месяцев на первый paper

---

## Почему это важно

Для **MS/PhD в MIT/Stanford/CMU**:
- Публикации — это **proof of research ability**
- Даже arXiv preprint лучше, чем ничего
- Recruiters смотрят: можешь ли ты **самостоятельно исследовать**

Для **top AI компаний** (OpenAI, Anthropic, DeepMind):
- Research culture ценит людей, которые **пишут и читают papers**
- Твой paper — **лучший coding interview**

---

## Темы для papers

### 1. System Design / Distributed Systems

**"Optimizing ClickHouse for High-Frequency Cashback Processing"**
- Твой production опыт
- Метрики: latency, throughput, consistency
- Можно опубликовать как case study

**"A Comparative Analysis of Consensus Protocols in Banking Systems"**
- Raft vs Paxos vs ZAB
- Твой опыт с финансовыми транзакциями
- Practical benchmarks

### 2. AI / ML

**"RAG Pipeline Optimization for Financial Document Analysis"**
- Твой опыт с AI-системами
- Сравнение embedding models
- Retrieval accuracy metrics

**"Code Review Automation: LLM vs Rule-Based Systems"**
- Твой code review bot
- A/B testing результатов
- Cost-benefit analysis

### 3. Physical AI / Robotics

**"Sim-to-Real Transfer for Retail Robotics"**
- Если пойдешь в robotics
- MuJoCo/Isaac Sim experiments
- Real-world validation

---

## Формат paper

### Структура (стандартная для CS)

```
1. Abstract (150-250 слов)
2. Introduction (мотивация + contribution)
3. Related Work (что уже сделано)
4. Methodology (как ты это делал)
5. Experiments / Results (метрики, графики)
6. Discussion (trade-offs, limitations)
7. Conclusion (summary + future work)
8. References
```

### Длина
- **Short paper:** 4-6 страниц (для workshops)
- **Full paper:** 8-12 страниц (для conferences)
- **Survey:** 15+ страниц

---

## Куда публиковать

### Уровень 1: arXiv (быстрый старт)

**Что это:** Preprint сервер, мгновенная публикация без review

**Процесс:**
1. Написать paper в LaTeX
2. Зарегистрироваться на arxiv.org
3. Получить endorsement (может потребоваться для первого paper)
4. Загрузить PDF + source
5. Опубликовать

**Время:** 1-2 дня после написания

**Ценность:**
- Можно указать в CV
- Можно отправить в вуз как writing sample
- Другие исследователи найдут твою работу

### Уровень 2: Workshops

**Куда:**
- NeurIPS workshops
- ICML workshops
- ICLR workshops
- Systems for ML workshops

**Процесс:**
1. Найти CFP (Call for Papers)
2. Написать paper (4-6 страниц)
3. Submit через OpenReview
4. Review (2-3 месяца)
5. Если принят — представить на workshop

### Уровень 3: Conferences

**Tier 1:**
- **SOSP/OSDI** (Systems)
- **SIGMOD/VLDB** (Databases)
- **NeurIPS/ICML/ICLR** (ML)
- **RSS/CoRL** (Robotics)

**Tier 2:**
- **SoCC, EuroSys, ATC** (Systems)
- **ACL, EMNLP** (NLP)
- **CVPR, ICCV** (Vision)

**Процесс:**
1. CFP (обычно за 6 месяцев до конференции)
2. Написать full paper (8-12 страниц)
3. Submit
4. Review (3 месяца)
5. Rebuttal (ответ на review)
6. Decision

---

## План написания первого paper

### Месяц 1-2: Выбор темы и research

- [ ] Определить тему (из списка выше)
- [ ] Прочитать 10-15 related papers
- [ ] Написать Related Work section
- [ ] Сформулировать research question

### Месяц 3: Эксперименты

- [ ] Провести эксперименты / собрать данные
- [ ] Построить графики
- [ ] Зафиксировать методологию
- [ ] Написать Methodology + Experiments

### Месяц 4: Написание

- [ ] Написать Introduction
- [ ] Написать Abstract
- [ ] Собрать весь paper
- [ ] Попросить 2-3 человек проревьюить

### Месяц 5: Ревью и публикация

- [ ] Доработать по feedback
- [ ] Отредактировать LaTeX
- [ ] Загрузить на arXiv
- [ ] Подать на workshop (опционально)

---

## Инструменты

| Инструмент | Для чего |
|------------|----------|
| Overleaf | LaTeX online |
| Zotero | Управление references |
| Google Scholar | Поиск papers |
| arXiv Sanity | Рекомендации papers |
| Papers With Code | Code для papers |
| Connected Papers | Визуализация связей |

---

## LaTeX template

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{amsmath, amssymb}
\usepackage{graphicx}
\usepackage{hyperref}

\title{Your Paper Title}
\author{Your Name}
\date{\today}

\begin{document}
\maketitle

\begin{abstract}
Your abstract here.
\end{abstract}

\section{Introduction}
...

\section{Related Work}
...

\section{Methodology}
...

\section{Experiments}
...

\section{Conclusion}
...

\bibliographystyle{plain}
\bibliography{references}

\end{document}
```

---

## Ресурсы для обучения

| Ресурс | Для чего |
|--------|----------|
| "How to Write a Great Research Paper" (Simon Peyton Jones) | Структура и стиль |
| "The Craft of Research" (Booth et al.) | Исследовательский процесс |
| YouTube: "Two Minute Papers" | Формат презентации |
| Papers We Love | Сообщество для чтения papers |
| MIT OCW: Writing for Research | Курс по академическому письму |

---

## Чеклист

- [ ] Выбрать тему
- [ ] Прочитать 10 related papers
- [ ] Написать Related Work
- [ ] Провести эксперименты
- [ ] Написать полный draft
- [ ] Получить feedback от 2+ людей
- [ ] Загрузить на arXiv
- [ ] Подать на 1 workshop
- [ ] Получить 1 citation

---

**Последнее обновление:** 16 May 2026
