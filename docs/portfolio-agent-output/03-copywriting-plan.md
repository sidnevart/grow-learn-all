# Copywriting Plan

## Overview

This document provides all copy for Artem Sidnev's portfolio website. The writing positions Artem as a **Backend / Platform / AI Automation Engineer** who builds data-intensive systems, internal platforms, and AI-enabled automation tools. Every piece of copy is designed to communicate technical credibility, measurable impact, and clarity of purpose.

Tone: competent, direct, specific, and quietly confident. No hype, no buzzword stuffing. Every claim is backed by a metric or a concrete outcome.

---

## Tone and Voice Guidelines

### Voice Principles

1. **Specific over vague**
   - Write: "Built targeting logic over ~30M transactions per day"
   - Avoid: "Worked with big data and high-load systems"

2. **Impact-first**
   - Lead with the outcome, then the mechanism
   - Write: "Saved 40-60 hours of manual work per month by automating partner-region substitution"
   - Avoid: "Implemented automation for audience setup workflows"

3. **Plain language for complex work**
   - Explain what something does before naming the technology
   - Write: "A local-first tool that makes AI agent work safer and easier to verify"
   - Avoid: "A local-first AI-agent execution framework with memory management and provider adapters"

4. **No corporate filler**
   - Avoid: "leveraging synergies", "driving innovation", "passionate about"
   - Use active verbs: built, reduced, automated, migrated, designed, shipped

5. **Backend credibility without frontend bias**
   - Since most projects are backend/AI tools, describe the visual mocks as "what the interface would look like" rather than pretending they are production UIs
   - Be transparent about what exists, what is mocked, and why

### Word List (Do Use)

- backend, platform, internal platform, data-intensive, workflow automation
- AI agent, RAG, LLM application, developer productivity, CI/CD
- targeting, audience building, analytical pipeline, partner integration
- shipped, built, reduced, automated, migrated, stabilized, resolved
- measurable, reproducible, observable, maintainable

### Word List (Avoid)

- passionate, obsessed, driven, leveraging, synergies, innovative (as self-description)
- ninja, rockstar, wizard, guru
- "I believe" / "I think" (state facts instead)
- "just" / "simply" / "only" (diminishes the work)

---

## Positioning Statement

### Primary Positioning

> Backend Software Engineer focused on data-intensive systems, internal platforms, workflow automation, and AI-enabled engineering tools.

### Secondary Positioning

> Backend engineer with strong AI automation and platform-building experience, especially in banking, analytics, Telegram Mini Apps, and internal developer productivity.

### Homepage Hero Variation

> I build backend systems, internal platforms, and AI-enabled automation that make complex workflows faster, clearer, and easier to scale.

---

## Hero Copy

### Homepage Hero

```
Artem Sidnev
Backend & AI Automation Engineer

I build data-intensive backend systems, internal platforms, and AI-enabled automation. Currently shipping targeting and analytics infrastructure at T-Bank.

[View Projects] [Download Resume]
```

### Alternative (More Compact)

```
Artem Sidnev
Backend / Platform / AI Automation Engineer

Java · Kotlin · Go · Python · ClickHouse · Spring Boot · AI Agents

[Explore Work] [Get in Touch]
```

### Hero Subline (supporting sentence)

```
Nearly 3 years of experience across banking, partner platforms, commercial real-estate analytics, Telegram Mini Apps, and AI-assisted engineering tools.
```

---

## Homepage Section Copy

### Section: Positioning Statement

```
I specialize in three areas:

1. Data-Intensive Systems
   Building services that handle millions of transactions per day, migrate analytical workloads to modern stacks, and make complex data pipelines reliable.

2. Internal Platforms & Automation
   Automating manual workflows, accelerating CI/CD, and building tooling that helps teams ship faster with fewer errors.

3. AI-Enabled Engineering
   Applying RAG, AI agents, and LLM applications to real operational problems: code review, onboarding, refactoring, and business automation.
```

### Section: Featured Projects Intro

```
Selected Work

Projects where backend engineering, data infrastructure, and AI automation delivered measurable results.
```

### Section: Impact Metrics

```
Impact in Numbers

~30M
transactions/day processed by targeting logic

$600K+
estimated annual business impact at T-Bank

5x
speedup of critical analytical scenario via ClickHouse migration

40-60 hrs/month
saved by automating partner-region substitution

48%
context load reduction in AI agent workflows (ARC)

5-7 min
CI pipeline acceleration (~15-20%)
```

### Section: Technical Expertise Intro

```
Stack & Tools

Languages and frameworks I use to build production systems.
```

### Section: Contact CTA

```
Open to Work

I am interested in backend, platform, AI tooling, and developer productivity roles where engineering work has a direct product or business impact.

Available for: Full-time · Contract · Remote · Hybrid

[Contact Me] [View Resume]
```

---

## Project Page Templates

### Template: Case Study Header

```
[Project Name]
[Employer or context] · [Timeline]

[One-liner]

[Category badge] [Stack tags]
```

### Template: Challenge

```
The Problem

[2-3 sentences describing the business or technical problem. Be specific about scale, pain, or risk.]
```

### Template: Solution

```
What I Built

[3-5 sentences on the architecture, key decisions, and role. Mention specific technologies only after explaining what they do.]
```

### Template: Impact

```
Results

• [Metric-backed outcome]
• [Metric-backed outcome]
• [Metric-backed outcome]
```

### Template: Mock UI Note (for backend/AI projects without real frontend)

```
Note: This project is a backend system and AI workflow. The interface below is a mock visualization showing what the operational dashboard would look like.
```

### Template: Technical Deep-Dive Toggle

```
Architecture & Stack

[Expandable section with sanitized architecture description, stack justification, and optional diagram.]
```

### Template: Related Projects

```
More in [Category]

[2-3 project cards]
```

### Template: Project CTA

```
Want to discuss this project?

[Contact] [View Next Project]
```

---

## Individual Project Copy

### 1. Cashback Targeting Platform

```
Cashback Targeting Platform
T-Bank · Jan 2025 -- Present

Backend systems for a cashback targeting platform that processes partner audience data and helps deliver relevant partner-funded offers to customers.

Stack: Java, Kotlin, Spring Boot, ClickHouse, PostgreSQL, Kafka, Redis, GitLab CI

The Problem
Partner-funded cashback campaigns required building audience segments from large transaction datasets. Legacy workflows were slow, partially manual, and built on aging infrastructure. Setup steps took 10-15 minutes per run, and diagnosing targeting issues consumed 20-40 minutes each.

What I Built
• Built partner-level targeting by customer spend and income on a flow of approximately 30M transactions per day across 1.5 years of history.
• Migrated audience-building workflows to an internal ClickHouse-as-a-Service analytical environment.
• Automated partner-region substitution in audience setup.
• Added early validation to critical targeting scenarios.
• Accelerated the main CI pipeline by 5-7 minutes.
• Removed legacy code, stabilized test workflows, and documented backend processes.

Results
• Estimated annual business impact reached about $600K+.
• Critical analytical scenario became about 5x faster.
• Saved up to 40-60 hours of manual work per month.
• Reduced diagnosis time for typical issues by 20-40 minutes.
• Resolved a major incident in a document workflow service, eliminating reputation risk and potential financial loss.
```

### 2. AI-Assisted Engineering Workflows (Aggregate or Individual)

#### AI Code Review for GitLab

```
AI Code Review for GitLab
T-Bank · 2025

An AI-assisted code review workflow integrated into GitLab merge requests.

Stack: AI agents, GitLab CI, internal LLM infrastructure

The Problem
Code review in large teams creates bottlenecks. Repetitive issues (style, common bugs, missing tests) consume senior engineer time that could go to architecture and product logic.

What I Built
Integrated an AI agent into the GitLab MR workflow to summarize changes, flag issues by severity, suggest fixes, and track approval status.

Results
• Reduced time spent on routine review feedback.
• Improved consistency of issue detection across teams.
• Developer feedback loop allowed continuous refinement of review rules.

Note: The interface below is a mock visualization of the review dashboard.
```

#### AI CI Refactor Bot

```
AI CI Refactor Bot
T-Bank · 2025

An automated CI job that detects tech debt, generates refactor plans, and prepares draft merge requests.

Stack: AI agents, GitLab CI, static analysis

The Problem
Tech debt accumulates in long-running codebases. Identifying refactor targets, planning changes, and creating MRs manually slows down improvement cycles.

What I Built
A CI-integrated bot that scans code for debt patterns, proposes refactor plans with estimated impact, generates branches, and opens draft MRs for human approval.

Results
• Reduced friction between identifying debt and shipping fixes.
• Human approval gate ensures no unwanted changes merge.

Note: The interface below is a mock visualization of the automation control center.
```

#### RAG Onboarding Agent

```
RAG Onboarding Agent
T-Bank · 2025

A retrieval-augmented onboarding assistant for new backend team members.

Stack: RAG, LLM, internal documentation corpus

The Problem
New engineers spend days navigating internal documentation, tools, and team-specific conventions. Onboarding is repetitive for mentors and inconsistent for hires.

What I Built
A chat-based assistant that retrieves relevant internal docs, answers questions with cited sources, tracks onboarding checklist progress, and suggests next steps.

Results
• Reduced repetitive onboarding questions to mentors.
• Improved consistency of information given to new hires.
• Confidence scores help users judge when to ask a human.

Note: The interface below is a mock visualization of the AI knowledge assistant.
```

#### n8n Cashback Audience Automation

```
n8n Cashback Audience Automation
T-Bank · 2025

Automated business workflows for cashback campaign creation and audience management using n8n.

Stack: n8n, REST APIs, internal platform integrations

The Problem
Campaign setup involved manual coordination across multiple internal tools. Managers repeated the same steps for each campaign, and status tracking was fragmented.

What I Built
Automated n8n workflows that connect campaign creation, audience builder execution, integration status checks, logging, and result summaries into a single pipeline.

Results
• Reduced campaign setup time.
• Centralized execution logs and status visibility.

Note: The interface below is a mock visualization of the business automation dashboard.
```

### 3. ARC — Local-First Platform for AI Agent Workflows

```
ARC
Open Source · Personal Project

A local-first environment for safe and reproducible AI-agent work in code projects.

Stack: Go, Wails, AI provider adapters, memory systems

The Problem
Running AI agents on real codebases is risky. Context windows are expensive, behavior is unpredictable, and outputs are hard to verify. Existing tools require cloud access or lack transparency.

What I Built
A desktop application combining a Go-based CLI runtime, Wails desktop shell, adapters for multiple AI providers, project memory, and execution artifacts in one local-first product.

Key design decisions:
• Context, memory, and execution-rule management reduce request cost and make behavior predictable.
• Step-by-step verification lets users inspect and approve agent actions.
• Embedded diagrams, mini-apps, demos, and simulations appear directly in agent responses for easier validation.

Results
• Reduced context load by 48% without lowering response quality.
• Fully local execution eliminates data leakage risk.
• Multi-provider support prevents vendor lock-in.
```

### 4. Commercial Real Estate Analytics Platform

```
Commercial Real Estate Analytics Platform
Large Real Estate Agency · Aug 2024 -- Aug 2025

Backend and automation for a platform combining auction data, CIAN listings, geocoding, Telegram bot, admin panel, and searchable object catalog.

Stack: Python, FastAPI, PostgreSQL, Telegram Bot, geocoding, Docker

The Problem
Realtors spent hours collecting and analyzing property data from multiple sources. Evaluating sale and rental profitability required manual spreadsheet work.

What I Built
• Backend services for collecting, structuring, and searching commercial real-estate objects.
• Integration with auction data, CIAN listings, and geocoding services.
• Telegram bot for quick queries and notifications.
• Admin panel and structured catalog for day-to-day navigation.

Results
• Enabled realtors to evaluate property economics in about 10 minutes (sale/rental profitability, cash flow, yield, payback period).
• Enabled district-level market analysis in 7-10 minutes.
```

### 5. Double Kiss — Telegram Mini App

```
Double Kiss
Freelance · Billiards Club Telegram Mini App

A Telegram Mini App for booking, match tracking, Elo rating, and YClients loyalty integration.

Stack: Python, FastAPI, SQLAlchemy, PostgreSQL, Redis, React, TypeScript, Vite, Tailwind, Telegram Mini Apps, YClients

The Problem
Billiards clubs needed a modern booking and loyalty system that lives inside Telegram, where their customers already are. Existing tools were fragmented and lacked integration with club management software.

What I Built
• Booking flows with contact-based registration.
• Match and Elo rating system.
• YClients loyalty integration: bonus debit/credit logic, booking records, result confirmation, retry handling for failed bonus settlement.
• React/Vite/Tailwind frontend with Telegram Mini App SDK.
• FastAPI backend with Redis caching and PostgreSQL persistence.
• Docker Compose deployment with nginx and CI/CD automation.
```

### 6. Svobodno — Telegram Mini App

```
Svobodno
Freelance · MVP

A Telegram Mini App for booking discounted last-minute service slots.

Stack: Python, FastAPI, SQLAlchemy, Redis, React, TypeScript, Vite, Tailwind, Telegram Mini Apps

The Problem
Service businesses (salons, mechanics, restaurants) have empty slots they would rather fill at a discount than leave unused. Customers want spontaneity and deals.

What I Built
An MVP with three flows:
• Customer: browse available last-minute slots, book instantly.
• Partner: list services, manage availability, track bookings.
• Admin: oversee platform activity, manage partners.

Deployed with FastAPI, SQLAlchemy, Redis, React/Vite/Tailwind, nginx, Docker Compose.
```

### 7. CIAN Mole

```
CIAN Mole
Freelance · Smart Scraper & Analytics Tool

An internal tool for commercial real estate market analysis by address or comparable properties.

Stack: Python, scraping infrastructure, analytics pipelines

The Problem
Realtors needed fast market analysis without manually browsing CIAN and other listing sites. Evaluating a property's market position took 30+ minutes.

What I Built
A smart scraper and analytics backend that collects listing data, structures it, and generates market analysis by address or provided comparables.

Results
• Reduced property market analysis time from 30+ minutes to under 10 minutes.
• Used by realtors for daily pricing and investment decisions.

Note: The interface below uses synthetic/anonymized data for demonstration.
```

### 8. AI Office — Personal AI Agent

```
AI Office
Personal Project

A personal AI agent system for business research, development pipeline automation, and project execution.

Stack: AI agents, OpenClaw, automation pipelines

The Problem
Staying on top of business opportunities, VC deals, and research topics requires hours of manual browsing and note-taking. Development tasks across multiple projects need context switching and repetitive setup.

What I Built
• Business research agent: finds new ideas, tracks VC deals, identifies promising directions, and generates detailed reports.
• Development pipeline agent: accepts high-level task descriptions, plans implementation, and executes the full development pipeline.

Note: The interface below is a mock visualization of the research dashboard.
```

### 9. CU Mock — Competitive Coding Platform

```
CU Mock
For University (Central University by T-Bank)

A real-time competitive coding platform for student tournaments.

Stack: React, TypeScript, Python/FastAPI, WebSockets

The Problem
Existing competitive coding platforms (like LeetCode) lack real-time interaction and spectator engagement. University tournaments needed something more exciting and transparent.

What I Built
• Real-time coding battles where participants solve the same problems simultaneously.
• "Battle" mechanics: players can interfere with each other (e.g., drop "bombs" that reset partial solutions).
• Live spectator view: track attempts, successes, and player activity in real time.

Note: The interface below is a mock visualization styled for Central University branding.
```

---

## About Page Copy

### Hero

```
Artem Sidnev
Backend & AI Automation Engineer

I build systems that process millions of events, automate what should not be manual, and apply AI to real engineering workflows.
```

### Engineering Story

```
How I Work

I started with computer science fundamentals at Canisius University, then deepened my knowledge through Harvard CS50, MIT OpenCourseWare algorithms, and hands-on open source work.

My early projects were freelance backend systems: Telegram bots, booking flows, CRM integrations. That taught me to ship fast, handle messy real-world requirements, and own the full deployment pipeline.

At T-Bank, I moved into data-intensive backend work: building targeting logic over tens of millions of daily transactions, migrating analytical workflows to ClickHouse, and automating manual steps that used to consume days of engineer time each month.

Along the way, I started applying AI not as a replacement for engineering, but as a tool for engineering: code review automation, refactoring bots, onboarding assistants, and local-first agent infrastructure.
```

### What I Do (3 columns)

```
Data-Intensive Systems

Building services that handle scale without becoming fragile. ClickHouse migrations, Kafka pipelines, Redis caching strategies, and PostgreSQL schema design for analytical and operational workloads.

Internal Platforms & Automation

Automating manual workflows, improving CI/CD, and building tools that make teams faster. From GitLab pipeline optimization to n8n business automation.

AI-Enabled Engineering

Applying RAG, AI agents, and LLMs to real problems: automated code review, refactoring pipelines, onboarding assistants, and developer productivity tooling.
```

### Experience Timeline

```
T-Bank — Software Engineer (Backend)
Jan 2025 -- Present
Cashback targeting, ClickHouse analytics, CI/CD improvement, AI-assisted engineering workflows.

Commercial Real Estate Analytics Platform
Aug 2024 -- Aug 2025
Auction data, CIAN integration, Telegram bot, admin panel, property economics automation.

Freelance Backend & Automation
Jun 2023 -- Present
Telegram Mini Apps (Double Kiss, Svobodno), booking systems, YClients integrations, CRM workflows.

Open Source — ARC
Personal Project
Local-first AI agent platform. Go, Wails, multi-provider adapters, 48% context reduction.

Education
Canisius University — Bachelor of Computer Science
Additional: Harvard CS50, MIT OpenCourseWare Algorithms, freeCodeCamp Java & Spring
```

### Availability & Interests

```
What I Am Looking For

Backend, platform, AI tooling, and developer productivity roles where engineering work has direct product or business impact.

Open to: Full-time, Contract, Remote, Hybrid

Target titles:
• Backend Software Engineer
• Platform Engineer
• AI Platform Engineer
• Developer Productivity Engineer
```

---

## Contact Page Copy

### Headline

```
Let's Build Something Reliable
```

### Body

```
I am currently open to backend, platform, and AI automation roles.

Whether you have a specific opportunity, want to discuss a project, or just want to connect — I respond to every message.

Typical response time: within 24 hours.
```

### Contact Methods

```
Email
a.sidnevart@gmail.com
Best for detailed proposals and official offers.

LinkedIn
linkedin.com/in/artem-sidnev
Best for professional networking and recruiter outreach.

Telegram
@sidnevart
Fastest for informal questions and quick coordination.
```

### What I'm Open To

```
Role Types
Full-time, Contract, Consulting

Work Models
Remote, Hybrid, On-site (with flexibility)

Locations
Open to international remote roles. Willing to relocate for the right opportunity.
```

### CTA

```
Prefer to reach out directly?
[Send an Email] [Message on Telegram]
```

---

## CTAs (Call-to-Action) Inventory

| Location | Copy | Destination |
|----------|------|-------------|
| Homepage Hero | View Projects | /projects |
| Homepage Hero | Download Resume | /resume (PDF) |
| Homepage Metrics | Contact Me | /contact |
| Project List | Filter by category | Tab toggle |
| Project Page | Discuss This Project | /contact |
| Project Page | View Next Project | Next project in category |
| About Page | Download Resume | /resume |
| About Page | Get in Touch | /contact |
| Contact Page | Send an Email | mailto: |
| Contact Page | Message on Telegram | https://t.me/sidnevart |
| Footer | GitHub | github.com/sidnevart |
| Footer | LinkedIn | linkedin.com/in/artem-sidnev |

### CTA Writing Rules
- Use verb-first language: "View", "Download", "Contact", "Discuss"
- Avoid generic "Learn More" — be specific about what happens next
- Secondary CTAs are text links or outline buttons; primary CTAs are filled buttons

---

## Meta Descriptions (SEO)

```
Homepage:
Artem Sidnev — Backend & AI Automation Engineer. Building data-intensive systems, internal platforms, and AI-enabled automation at T-Bank and beyond.

Projects:
Case studies in backend engineering, AI automation, Telegram Mini Apps, and developer tools. Java, Kotlin, Go, Python, ClickHouse, Spring Boot, AI agents.

About:
Backend engineer with nearly 3 years of experience in banking, analytics, Telegram Mini Apps, and AI-assisted engineering tools. Open to platform and AI tooling roles.

Contact:
Open to backend, platform, and AI automation roles. Full-time, contract, remote, hybrid. Email, LinkedIn, and Telegram.
```

---

## Notes on Mock UIs and Transparency

For projects that lack a traditional frontend (most AI and backend work), the copy must set honest expectations before showing mock visualizations.

### Standard Transparency Note

```
This project is a backend system / AI workflow / internal tool. The interface shown below is a mock visualization demonstrating what the operational dashboard or user-facing layer would look like. No production frontend exists for this system.
```

### Why This Matters

- Positions Artem as a backend engineer, not a frontend designer pretending to have built UIs
- Demonstrates product thinking ("this is what the interface would need to show")
- Maintains credibility with technical reviewers who can tell the difference
