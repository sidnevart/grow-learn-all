# Site Architecture Document

## Overview

This document defines the information architecture, page hierarchy, URL structure, and component inventory for Artem Sidnev's personal portfolio website. The site is designed to position Artem as a **Backend / Platform / AI Automation Engineer** with demonstrated experience in data-intensive systems, internal platforms, and AI-enabled engineering workflows.

The architecture prioritizes:
- Clear project storytelling with measurable impact
- Separation of "work experience" from "project demos"
- Mock visualizations for backend/AI projects that lack traditional frontends
- Fast navigation between technical depth and high-level positioning

---

## Page Hierarchy and URL Structure

```
/
├── /projects
│   ├── /projects/cashback-targeting-platform          (case study)
│   ├── /projects/ai-code-review-gitlab                (case study + mock)
│   ├── /projects/ai-ci-refactor-bot                   (case study + mock)
│   ├── /projects/rag-onboarding-agent                 (case study + mock)
│   ├── /projects/n8n-cashback-automation                (case study + mock)
│   ├── /projects/commercial-real-estate-analytics     (case study)
│   ├── /projects/double-kiss-telegram-mini-app        (case study + screenshots)
│   ├── /projects/svobodno-telegram-mini-app           (case study + screenshots)
│   ├── /projects/cian-mole                            (case study + mock)
│   ├── /projects/arc-local-first-ai-platform            (case study)
│   ├── /projects/ai-office-personal-agent             (case study + mock)
│   └── /projects/cumock-competitive-coding          (case study + mock)
├── /about
├── /contact
├── /resume                                            (PDF download + inline summary)
└── /blog (future)
    └── /blog/building-ai-assisted-engineering-workflows
    └── /blog/reducing-manual-setup-in-partner-targeting
    └── /blog/designing-telegram-mini-apps-with-fastapi
    └── /blog/local-first-platform-for-ai-agents
```

### URL Conventions
- All project URLs use kebab-case project names
- No trailing slashes enforced via redirect rules
- Canonical URLs point to `https://sidnev.dev` (recommended domain)

---

## Navigation Design

### Primary Navigation (persistent top bar)

| Label | Destination | Rationale |
|-------|-------------|-----------|
| Projects | /projects | Primary conversion path — recruiters and hiring managers want to see shipped work first |
| About | /about | Humanizes the profile; explains trajectory into backend/AI |
| Resume | /resume | Direct access to downloadable CV |
| Contact | /contact | Low-friction CTA for opportunities |

### Secondary Navigation (projects listing page)

Filter tabs on `/projects`:
- **All Projects** (default)
- **AI & Automation** — AI Code Review, AI CI Refactor Bot, RAG Onboarding, n8n Automation, AI Office, ARC
- **Platforms & Data** — Cashback Targeting, Commercial Real Estate, CIAN Mole
- **Telegram Mini Apps** — Double Kiss, Svobodno
- **Developer Tools** — ARC, CU Mock, AI Office

### Footer Navigation

- GitHub
- LinkedIn
- Habr
- Telegram
- X/Twitter
- Email

---

## Content Model for Projects

Every project page follows a standardized content model to ensure consistency and readability.

### Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `project_name` | string | yes | Display title |
| `slug` | string | yes | URL segment |
| `category` | enum | yes | `ai-automation`, `platforms-data`, `telegram-apps`, `developer-tools` |
| `featured` | boolean | yes | Whether it appears on homepage |
| `employer` | string | optional | T-Bank, Freelance, Open Source, Personal |
| `timeline` | string | yes | e.g., "Jan 2025 -- Present" |
| `stack` | string[] | yes | Technology tags |
| `one_liner` | string | yes | Single-line description |
| `challenge` | text | yes | Problem context |
| `solution` | text | yes | What was built |
| `impact` | text[] | yes | Bullet points with metrics |
| `mock_ui_needed` | boolean | yes | Whether a mock visualization is required |
| `mock_ui_type` | enum | optional | `dashboard`, `chat-interface`, `automation-center`, `timeline`, `code-review` |
| `real_screenshots_available` | boolean | yes |
| `synthetic_data_strategy` | enum | optional | `synthetic`, `anonymized`, `real-structure` |
| `github_url` | string | optional |
| `demo_url` | string | optional |
| `private` | boolean | yes | Whether source is confidential |

### Content Model Example (Cashback Targeting)

```yaml
project_name: "Cashback Targeting Platform"
slug: "cashback-targeting-platform"
category: platforms-data
featured: true
employer: T-Bank
timeline: "Jan 2025 -- Present"
stack: ["Java", "Kotlin", "Spring Boot", "ClickHouse", "PostgreSQL", "Kafka", "Redis", "GitLab CI"]
one_liner: "Backend systems for partner-funded cashback targeting over 30M daily transactions."
challenge: "Legacy audience-building workflows were slow, manual, and hard to maintain."
solution: "Built targeting logic by customer spend and income; migrated critical workflows to internal ClickHouse-as-a-Service; automated partner-region setup; added early validation."
impact:
  - "Built targeting over ~30M transactions/day across 1.5 years of history"
  - "Estimated annual business impact: $600K+"
  - "5x faster critical scenario via ClickHouse migration"
  - "Saved 40-60 hours/month by automating partner-region substitution"
  - "Reduced diagnosis time by 20-40 minutes per issue via early validation"
  - "Accelerated CI pipeline by 5-7 minutes (~15-20%)"
mock_ui_needed: true
mock_ui_type: dashboard
real_screenshots_available: false
synthetic_data_strategy: synthetic
github_url: null
demo_url: null
private: true
```

---

## Homepage Section Structure

### Section 1: Hero
- Name + role headline
- One-line positioning statement
- Primary CTA: "View Projects"
- Secondary CTA: "Download Resume"
- Social proof: GitHub stars, LinkedIn, key metrics ticker

### Section 2: Positioning Statement
- 2-3 sentences defining the engineer profile
- Emphasis on backend, platforms, data, AI automation
- Trust signals: T-Bank, 3 years experience, measurable impact

### Section 3: Featured Projects (3-4 cards)
- Cashback Targeting Platform
- AI-Assisted Engineering Workflows (aggregate card)
- ARC (Local-First AI Agent Platform)
- Double Kiss or Svobodno (visual project)

### Section 4: Technical Expertise
- Language stack row
- Backend/Data stack row
- Platforms/Automation stack row
- AI/Agents stack row
- Product Areas

### Section 5: Impact Metrics
- ~30M transactions/day
- $600K+ estimated annual impact
- 5x speedup
- 40-60 hours/month saved
- 48% context load reduction

### Section 6: Recent Writing / Case Studies (optional)
- Links to blog posts or case studies

### Section 7: Contact CTA
- "Open to backend, platform, and AI tooling roles"
- Email + LinkedIn + calendly/telegram

---

## Project Page Structure

### Standard Template

1. **Breadcrumb** — Home > Projects > [Project Name]
2. **Project Header**
   - Name, timeline, employer badge
   - Stack tags
   - GitHub / Demo links (if public)
   - Category badge
3. **Mock UI / Screenshot Gallery**
   - Full-width mock visualization or screenshot carousel
   - Caption explaining what is shown
4. **Challenge Section**
   - Problem statement in plain language
   - Business/technical context
5. **Solution Section**
   - Architecture overview
   - Key engineering decisions
   - Role and responsibilities
6. **Impact Section**
   - Bulleted metrics
   - Time saved, money saved, performance gains
7. **Technical Deep-Dive** (expandable or tabbed)
   - Architecture diagram
   - Stack justification
   - Key code patterns (sanitized snippets)
8. **Lessons Learned**
   - What worked, what didn't, what next
9. **Related Projects**
   - 2-3 linked projects in same category
10. **CTA Footer**
    - "Discuss this project" / "Contact"

### Mock UI Integration Rules

| Project | Mock Type | Visual Direction |
|---------|-----------|------------------|
| AI Code Review GitLab | Code-review dashboard | GitLab-like review dashboard: MR list, AI summary, severity, suggested fixes |
| AI CI Refactor Bot | Automation center | Pipeline timeline, detected tech debt, refactor plan, MR status, approval gate |
| RAG Onboarding Agent | Chat interface | AI knowledge assistant: chat, docs sources, retrieved context, confidence, checklist |
| n8n Cashback Automation | Business dashboard | Campaign builder, audience builder, workflow execution, integration statuses, logs |
| CIAN Mole | Analytics dashboard | Commercial real estate analytics: map view, property cards, metrics panel |
| AI Office | Research dashboard | Research topics, VC deals feed, generated reports, project pipeline |
| CU Mock | Competition arena | Real-time coding battle interface, leaderboard, player activity feed |

---

## About Page Structure

1. **Hero** — Name, role, location, availability status
2. **Engineering Story**
   - How I got into backend and AI automation
   - Trajectory: university -> freelance -> T-Bank -> open source
3. **What I Do** (3 columns)
   - Data-Intensive Systems
   - Internal Platforms & Automation
   - AI-Enabled Engineering Tools
4. **Experience Timeline**
   - T-Bank (current)
   - Commercial Real Estate Analytics
   - Freelance Projects
   - Open Source (ARC)
   - Education (Canisius University, CS50, MIT OCW)
5. **Beyond the Code**
   - Habr writing
   - Telegram / X presence
   - Community contributions
6. **Availability & Interests**
   - Open to: full-time, contract, remote, hybrid
   - Target roles: Backend, Platform, AI Platform, Developer Productivity
7. **CTA** — Contact / Download Resume

---

## Contact Page Structure

1. **Headline** — "Let's Build Something Reliable"
2. **Positioning Recap** — 1 sentence on what I do
3. **Contact Methods** (cards)
   - Email (primary)
   - LinkedIn
   - Telegram
   - GitHub
4. **What I'm Open To** — role types, locations, contract vs full-time
5. **Typical Response Time** — e.g., "Usually within 24 hours"
6. **CTA** — Simple form (name, email, message) or direct mailto link
7. **Social Links Row**

---

## SEO Metadata Strategy

### Global Defaults

| Property | Value |
|----------|-------|
| Site Title | Artem Sidnev — Backend & AI Automation Engineer |
| Description | Backend engineer building data-intensive systems, internal platforms, and AI-enabled automation. Java, Kotlin, Go, Python, ClickHouse, Spring Boot, AI agents. |
| Author | Artem Sidnev |
| Twitter Handle | @ArtemkaWeb3 |
| Locale | en_US |

### Page-Specific Meta

| Page | Title | Description |
|------|-------|-------------|
| / | Artem Sidnev — Backend & AI Automation Engineer | ... |
| /projects | Projects — Artem Sidnev | Case studies in backend systems, AI automation, Telegram Mini Apps, and developer tools. |
| /projects/[slug] | [Project Name] — Artem Sidnev | One-liner + impact metric |
| /about | About — Artem Sidnev | Engineering background, experience, and what I am looking for next. |
| /contact | Contact — Artem Sidnev | Open to backend, platform, and AI tooling roles. |
| /resume | Resume — Artem Sidnev | Downloadable CV and skills summary. |

### Structured Data

- **Person schema** on /about
- **Project schema** on each /projects/[slug]
- **BreadcrumbList** on all pages
- **Article schema** on future blog posts

### Open Graph / Twitter Cards
- Dynamic OG images per project (mock screenshot or generated card)
- Default OG image for homepage (name + role + key metrics)

### Keywords Strategy

Primary: `Backend Engineer`, `Software Engineer`, `AI Automation`, `Internal Platforms`, `Data-Intensive Systems`, `Platform Engineer`

Secondary: `Java`, `Kotlin`, `Go`, `Python`, `Spring Boot`, `FastAPI`, `ClickHouse`, `Kafka`, `Redis`, `GitLab CI`, `Docker`, `n8n`, `RAG`, `AI Agents`, `Telegram Mini Apps`, `CI/CD`, `Developer Productivity`

---

## Component Inventory

### Layout Components

| Component | Purpose | Reused On |
|-----------|---------|-----------|
| `TopNav` | Primary navigation | All pages |
| `Footer` | Social links, secondary nav | All pages |
| `PageContainer` | Max-width wrapper, padding | All pages |
| `Section` | Vertical spacing, optional background | All pages |
| `Breadcrumb` | Path indicator | Project pages, nested pages |

### UI Components

| Component | Purpose |
|-----------|---------|
| `Button` | CTAs, links — primary (filled), secondary (outline), ghost |
| `Tag` | Technology stack, category badges |
| `Card` | Project cards, contact method cards |
| `MetricPill` | Impact numbers with labels |
| `MockFrame` | Browser-like frame around mock screenshots |
| `ScreenshotCarousel` | For projects with multiple real screenshots |
| `Accordion` | Expandable technical deep-dives |
| `TabGroup` | Project category filtering |
| `Timeline` | Experience timeline on /about |
| `SkillRow` | Horizontal stack of technology tags with category headers |

### Content Components

| Component | Purpose |
|-----------|---------|
| `HeroSection` | Name, headline, CTAs |
| `PositioningBanner` | 2-3 sentence role definition |
| `FeaturedProjectsGrid` | 3-4 project cards on homepage |
| `ProjectCard` | Image/mock + title + one-liner + stack tags |
| `ProjectDetailHeader` | Title, meta, links |
| `MockUIShowcase` | Full-width mock with caption |
| `ImpactList` | Bulleted metrics with icons |
| `StackList` | Technology tags grouped by category |
| `ContactMethods` | Email/LinkedIn/Telegram cards |
| `ResumeBlock` | PDF download + inline summary |

### Data Visualization Components

| Component | Purpose | Used On |
|-----------|---------|---------|
| `MetricsTicker` | Animated counters (30M, $600K, 5x, etc.) | Homepage |
| `MockDashboard` | Generic dashboard shell for mock UIs | AI projects |
| `MockChatInterface` | Chat UI shell for RAG/agent projects | RAG Onboarding, AI Office |
| `MockPipeline` | CI/CD pipeline visualization | AI CI Refactor Bot |
| `MockCodeReview` | MR review interface mock | AI Code Review |

### Utility Components

| Component | Purpose |
|-----------|---------|
| `SeoHead` | Title, meta, OG, structured data |
| `DownloadLink` | Resume PDF with tracking |
| `ExternalLink` | Opens in new tab with security attrs |
| `LazyImage` | Optimized image loading |

---

## Responsive Breakpoints

| Name | Width | Notes |
|------|-------|-------|
| mobile | < 640px | Single column, stacked nav (hamburger), reduced mock UI fidelity |
| tablet | 640-1024px | 2-column grids, side-by-side on project pages |
| desktop | > 1024px | Full layout, 3-4 column grids, max-width 1200px container |

---

## Performance & Accessibility Notes

- All mock UI images should be lazy-loaded with blur-up placeholders
- Mock UIs must include `alt` text describing what the visualization represents
- Focus-visible styles for all interactive elements
- Keyboard navigable project filters
- Reduced-motion preference respected for metric tickers and animations
- Semantic HTML: `nav`, `main`, `article`, `section`, `aside`
