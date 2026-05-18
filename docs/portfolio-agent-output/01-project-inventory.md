# Project Inventory — Artem Sidnev Portfolio

> Generated from: `EN CV Artem Sidnev Codex.tex`, `RU CV Artem Sidnev Codex.tex`, `additional_experience.md`, `additional_project_descriptions.md`

---

## Legend

| Field | Meaning |
|-------|---------|
| **Source** | File where the project was first identified |
| **Type** | corporate / freelance / personal / open-source / university |
| **Risk** | public / private / confidential — whether it can be shown externally |
| **Case study?** | Should this become a full portfolio case study? |
| **Mock UI needed?** | Does it need a synthetic demo frontend? |
| **Real screenshots?** | Are there real UI screenshots available? |
| **Format** | Suggested representation in the portfolio |
| **Missing info** | Data still needed from the human |
| **TODOs** | Action items for human review |

---

## 1. Cashback Targeting Platform (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | Cashback Targeting Platform |
| **Source** | EN CV, RU CV |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | YES — high-impact backend/data project |
| **Mock UI needed?** | YES — internal dashboard / audience builder |
| **Real screenshots?** | NO — internal tool, no external screenshots |
| **Format** | Markdown case study + mock screenshots of audience-builder UI |
| **Missing info** | Exact architecture diagram, sample (anonymized) data schema, specific ClickHouse query patterns, more detailed flow of audience setup |
| **TODOs** | [ ] Confirm which metrics can be shared publicly ($600K+ impact is already in CV, but reconfirm); [ ] Create anonymized system-architecture diagram; [ ] Decide if a short demo video of mock UI is needed |

**Notes:**
- Processes ~30M transactions/day across 1.5 years of history.
- Major achievement: 5x speedup via ClickHouse-as-a-Service migration.
- This is the strongest corporate project; it should lead the "Experience" section of the portfolio.

---

## 2. Document Workflow Service — Incident Resolution (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | Document Workflow Service Incident Resolution |
| **Source** | EN CV, RU CV |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | NO — too sensitive, but mention as a bullet in the T-Bank summary |
| **Mock UI needed?** | NO |
| **Real screenshots?** | NO |
| **Format** | 1-2 sentences in the overall T-Bank case study or CV narrative |
| **Missing info** | Specifics of the incident are sensitive and should NOT be documented |
| **TODOs** | [ ] Do NOT expand into a separate case study; keep only high-level mention |

**Notes:**
- Resolved a major incident, eliminated reputational risk, prevented financial loss.
- Do not expose internal service names, incident timelines, or financial figures beyond what is already in the CV.

---

## 3. AI Code Review for GitLab (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | AI Code Review for GitLab |
| **Source** | additional_project_descriptions.md |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | YES — strong AI-automation story |
| **Mock UI needed?** | YES |
| **Real screenshots?** | NO |
| **Format** | Markdown case study + mock GitLab-like review dashboard |
| **Missing info** | Which LLM/model was used, integration details with GitLab API, review latency, team adoption rate, false-positive rate |
| **TODOs** | [ ] Build mock screenshots: MR list, AI summary, issues with severity, suggested fix, approval status, developer feedback; [ ] Confirm what internal metrics can be shared |

**Notes:**
- Visual target: GitLab-like review dashboard.
- Good candidate for demonstrating AI-enabled developer productivity tooling.

---

## 4. AI CI Refactor Bot (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | AI CI Refactor Bot |
| **Source** | additional_project_descriptions.md |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | YES |
| **Mock UI needed?** | YES |
| **Real screenshots?** | NO |
| **Format** | Markdown case study + mock automation-control-center UI |
| **Missing info** | Tech debt detection heuristics, model used, MR acceptance rate, pipeline time improvement numbers beyond 5-7 min |
| **TODOs** | [ ] Build mock screenshots: pipeline timeline, detected tech debt, refactor plan, generated branch, MR status, human approval, CI result; [ ] Verify if the 10% CI/CD acceleration from additional_experience.md refers to this bot or overall pipeline work |

**Notes:**
- Visual target: automation control center.
- Overlaps with CV claim "accelerated the main CI pipeline by 5-7 minutes" and additional_experience.md claim "ускорил CI/CD на 10%".

---

## 5. RAG Onboarding Agent (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | RAG Onboarding Agent |
| **Source** | additional_project_descriptions.md |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | YES |
| **Mock UI needed?** | YES — T-Bank/Tinkoff style |
| **Real screenshots?** | NO |
| **Format** | Markdown case study + mock AI-knowledge-assistant UI |
| **Missing info** | Embedding model, vector store, doc source count, intern satisfaction or time-to-productivity metrics |
| **TODOs** | [ ] Build mock screenshots: chat interface, docs sources, retrieved context, confidence score, onboarding checklist, suggested next steps; [ ] Confirm whether T-Bank branding can be mimicked or should be genericized |

**Notes:**
- Visual target: AI knowledge assistant in a T-Bank/Tinkoff-inspired style.
- Strong story for AI + internal-platforms portfolio angle.

---

## 6. n8n Cashback Audience Automation (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | n8n Cashback Audience Automation |
| **Source** | additional_project_descriptions.md |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | YES |
| **Mock UI needed?** | YES — T-Bank/Tinkoff style |
| **Real screenshots?** | NO |
| **Format** | Markdown case study + mock business-automation dashboard |
| **Missing info** | n8n workflow count, partner-region substitution logic details, exact hours saved per month (CV says 40-60 hrs/month) |
| **TODOs** | [ ] Build mock screenshots: campaign creation flow, audience builder, workflow execution, integration statuses, logs, result summary; [ ] Reconfirm 40-60 hrs/month metric for public use |

**Notes:**
- Visual target: business automation dashboard.
- Directly linked to CV claim about automated partner-region substitution.

---

## 7. Personalized AI Customer Assistant (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | Personalized AI Customer Assistant |
| **Source** | additional_experience.md |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | MAYBE — check if it was shipped or only an experiment |
| **Mock UI needed?** | YES if included |
| **Real screenshots?** | NO |
| **Format** | Short paragraph or case study depending on shipping status |
| **Missing info** | Was this a prototype or production feature? Which channels (app, Telegram, web)? Model used? Any public references? |
| **TODOs** | [ ] Confirm production vs. experimental status; [ ] If experimental, consider dropping from portfolio or keeping as a brief mention |

**Notes:**
- Recommends places (restaurants, cafes, leisure) based on transactions and partner data.
- High potential, but only viable as a case study if it went beyond internal R&D.

---

## 8. AI Office (T-Bank / Personal)

| Field | Value |
|-------|-------|
| **Project title** | AI Office |
| **Source** | additional_experience.md |
| **Type** | corporate (internal tooling) |
| **Risk** | private / confidential |
| **Case study?** | NO — keep as a high-level mention in CV or skills section |
| **Mock UI needed?** | NO |
| **Real screenshots?** | NO |
| **Format** | 1-2 sentences in the AI-skills narrative |
| **Missing info** | Whether this is a personal side project or an internal T-Bank initiative; Grafana dashboards are likely internal |
| **TODOs** | [ ] Clarify ownership (T-Bank internal vs. personal); [ ] Do NOT expose OpenClaw configuration details or internal monitoring URLs |

**Notes:**
- Does research, builds financial models, generates ideas.
- If personal, can be merged with the "AI Office" personal project (see item 15).

---

## 9. Token Economy / Token Saving Tool (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | Token Saving Tool |
| **Source** | additional_experience.md |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | MAYBE — narrow scope; good as a portfolio bullet if visuals can be made |
| **Mock UI needed?** | YES if expanded |
| **Real screenshots?** | NO |
| **Format** | Short section inside a larger AI case study or standalone micro-case study |
| **Missing info** | Exact mechanism (prompt compression, caching, model switching?), integration points, team adoption |
| **TODOs** | [ ] Decide if this deserves its own case study or should be a metric inside the AI Code Review / RAG agent stories |

**Notes:**
- Claim: 60% token reduction.
- Could be a powerful metric if paired with a clear explanation.

---

## 10. Bank-Wide Skills Library (T-Bank)

| Field | Value |
|-------|-------|
| **Project title** | Bank-Wide Skills Library |
| **Source** | additional_experience.md |
| **Type** | corporate |
| **Risk** | confidential |
| **Case study?** | NO — too abstract for a visual portfolio case study |
| **Mock UI needed?** | NO |
| **Real screenshots?** | NO |
| **Format** | Mention in CV or LinkedIn as a platform/enablement initiative |
| **Missing info** | Number of skills, consumption metrics, tech stack |
| **TODOs** | [ ] Keep as a narrative bullet about internal platform building; [ ] Do NOT expose internal library names or API schemas |

**Notes:**
- Good for demonstrating platform-thinking and scaling culture, but not a visual portfolio piece.

---

## 11. CIAN Mole / Commercial Real Estate Analytics Platform

| Field | Value |
|-------|-------|
| **Project title** | CIAN Mole (Commercial Real Estate Analytics Platform) |
| **Source** | EN CV, RU CV, additional_project_descriptions.md |
| **Type** | freelance |
| **Risk** | private — client data must be anonymized |
| **Case study?** | YES — strongest freelance project |
| **Mock UI needed?** | YES |
| **Real screenshots?** | NO — Telegram bot only, no real frontend |
| **Format** | Markdown case study + mock admin-panel / analytics dashboard |
| **Missing info** | Tech stack details, architecture diagram, sample (synthetic) property data, exact auction/CIAN data flow, geocoding provider |
| **TODOs** | [ ] Confirm whether any anonymized screenshots of the Telegram bot can be used; [ ] Create mock admin panel screens: object catalog, economic calculator, district market analysis, geocoding map; [ ] Prepare synthetic data set for demo |

**Notes:**
- Real frontend did not exist; the product was a Telegram bot + backend.
- Data should be synthetic / anonymized / based on real structure (per additional_project_descriptions.md).
- Path referenced: `documents/projects/ГОША ПРОЕКТ/commercial_real_estate_analysis` — but this directory does not currently exist in the repo.

---

## 12. Double Kiss — Telegram Mini App (Billiards Club)

| Field | Value |
|-------|-------|
| **Project title** | Double Kiss |
| **Source** | EN CV, RU CV, additional_experience.md |
| **Type** | freelance |
| **Risk** | private — client business data |
| **Case study?** | YES |
| **Mock UI needed?** | NO — real frontend exists |
| **Real screenshots?** | YES — but need to obtain / generate them |
| **Format** | Markdown case study + real screenshots of the Mini App |
| **Missing info** | URL or access to the live Mini App, actual screenshots, YClients integration flow diagram, Elo-rating logic details |
| **TODOs** | [ ] Capture real screenshots of booking flow, match result, loyalty/bonus screen, admin view; [ ] If live app is unavailable, create mock screens; [ ] Anonymize player names and club branding if needed |

**Notes:**
- Full stack: FastAPI, SQLAlchemy, Redis, Telegram bot runtime, React/Vite/Tailwind, nginx, Docker Compose.
- Loyalty flows include bonus debit/credit, retry handling for failed settlements.
- Path referenced: `documents/projects/double-kiss-loyalty` — but this directory does not currently exist in the repo.

---

## 13. Svobodno / УРВИ! — Telegram Mini App (Last-Minute Slot Booking)

| Field | Value |
|-------|-------|
| **Project title** | Svobodno (УРВИ!) |
| **Source** | EN CV, RU CV, additional_project_descriptions.md |
| **Type** | freelance / personal product |
| **Risk** | public — live at https://urvi.app |
| **Case study?** | YES |
| **Mock UI needed?** | NO — real frontend exists |
| **Real screenshots?** | YES — but must be captured |
| **Format** | Markdown case study + real screenshots |
| **Missing info** | Current operational status of urvi.app, YClients integration details, partner onboarding flow, admin panel access |
| **TODOs** | [ ] Take screenshots of customer flow (slot discovery, booking), partner flow (slot creation, YClients connect), admin flow; [ ] Verify if urvi.app is still live and functional; [ ] Prepare public-safe description without exposing partner PII |

**Notes:**
- Live URL: https://urvi.app
- Customer + partner + admin flows.
- Per additional_project_descriptions.md: "фронтенд есть, нужно скрины каким-то образом сделать."

---

## 14. Various Telegram Bots, CRMs, and Small Automations

| Field | Value |
|-------|-------|
| **Project title** | Miscellaneous Telegram Bots & CRM Automations |
| **Source** | additional_project_descriptions.md |
| **Type** | freelance |
| **Risk** | private |
| **Case study?** | NO — too small individually |
| **Mock UI needed?** | NO |
| **Real screenshots?** | NO |
| **Format** | Brief mention in CV or a collective "Other Projects" list |
| **Missing info** | Specific project names, tech stacks, client contexts |
| **TODOs** | [ ] If any project becomes significant later, spin it out into its own inventory item; [ ] Keep GitHub repos private unless explicitly cleared |

**Notes:**
- Nothing "mega" per the source file; represent as a GitHub repo list or bullet points.

---

## 15. ARC — Local-First AI Agent Platform

| Field | Value |
|-------|-------|
| **Project title** | ARC |
| **Source** | EN CV, RU CV |
| **Type** | open-source / personal |
| **Risk** | public |
| **Case study?** | YES — flagship open-source project |
| **Mock UI needed?** | NO — Wails desktop app exists, can record/screenshot |
| **Real screenshots?** | YES — the app itself can be screenshotted |
| **Format** | Markdown case study + real screenshots / screen recordings + GitHub link |
| **Missing info** | GitHub repository URL (not listed in CV), download/install stats, contributor count, demo video |
| **TODOs** | [ ] Add GitHub link to portfolio; [ ] Capture screenshots of CLI runtime, Wails shell, memory management UI, embedded diagrams/mini-apps; [ ] Create a 60-second demo GIF or video; [ ] Write a concise README if not already polished |

**Notes:**
- Go CLI + Wails desktop + multi-provider adapters.
- 48% context-load reduction is a strong metric.
- Embedded diagrams, mini-apps, demos, and simulations in agent responses.

---

## 16. CUMock — University Competition Platform

| Field | Value |
|-------|-------|
| **Project title** | CUMock |
| **Source** | additional_project_descriptions.md |
| **Type** | university |
| **Risk** | public |
| **Case study?** | YES — unique competitive-coding platform |
| **Mock UI needed?** | YES — mock frontend in Central University style |
| **Real screenshots?** | NO — per source, frontend should be mocked |
| **Format** | Markdown case study + mock competition-platform UI |
| **Missing info** | Exact game mechanics beyond "bomb" sabotage, tech stack, whether the backend is still runnable, number of participants in pilot |
| **TODOs** | [ ] Build mock screens: real-time coding arena, leaderboard, sabotage actions, participant status (attempts, successes, solved tasks); [ ] Style mock UI after Central University (T-Bank) branding or genericize if needed; [ ] Check if repos `sidnevart/cumock_frontend` and `sidnevart/cumock_backend` are public and linkable |

**Notes:**
- GitHub repos: `sidnevart/cumock_frontend`, `sidnevart/cumock_backend`
- Real-time competitive coding with sabotage mechanics (e.g., "bomb" drops opponent's progress).
- More engaging than LeetCode-style competitions.

---

## 17. AI Office v2 (Personal)

| Field | Value |
|-------|-------|
| **Project title** | AI Office v2 |
| **Source** | additional_project_descriptions.md |
| **Type** | personal |
| **Risk** | public |
| **Case study?** | MAYBE — overlaps with corporate AI Office (item 8) |
| **Mock UI needed?** | YES if included |
| **Real screenshots?** | NO |
| **Format** | GitHub repo + short description, or merge with item 8 |
| **Missing info** | How this differs from the T-Bank AI Office; whether it is a continuation or a separate side project |
| **TODOs** | [ ] Clarify relationship to item 8; [ ] If distinct, decide if it adds value to the portfolio or duplicates narrative; [ ] Repo: `sidnevart/chappi-ai-office-v2` |

**Notes:**
- Uses OpenClaw.
- Capabilities: business research, VC deal discovery, trend analysis, full development pipeline from a short prompt.
- Consider merging with the AI-skills narrative rather than a standalone case study.

---

## Summary Table

| # | Project | Type | Risk | Case study? | Mock UI? | Real screenshots? | Format |
|---|---------|------|------|-------------|----------|-------------------|--------|
| 1 | Cashback Targeting Platform | corporate | confidential | YES | YES | NO | Case study + mock dashboard |
| 2 | Document Workflow Incident | corporate | confidential | NO | NO | NO | CV bullet only |
| 3 | AI Code Review for GitLab | corporate | confidential | YES | YES | NO | Case study + mock GitLab UI |
| 4 | AI CI Refactor Bot | corporate | confidential | YES | YES | NO | Case study + mock control center |
| 5 | RAG Onboarding Agent | corporate | confidential | YES | YES | NO | Case study + mock assistant UI |
| 6 | n8n Cashback Audience Automation | corporate | confidential | YES | YES | NO | Case study + mock automation dashboard |
| 7 | Personalized AI Customer Assistant | corporate | confidential | MAYBE | YES if included | NO | Paragraph or case study |
| 8 | AI Office (corporate) | corporate | private | NO | NO | NO | CV/LinkedIn mention |
| 9 | Token Saving Tool | corporate | confidential | MAYBE | YES if included | NO | Micro-case or metric bullet |
| 10 | Bank-Wide Skills Library | corporate | confidential | NO | NO | NO | CV/LinkedIn mention |
| 11 | CIAN Mole / Real Estate Analytics | freelance | private | YES | YES | NO | Case study + mock analytics UI |
| 12 | Double Kiss | freelance | private | YES | NO | YES | Case study + real screenshots |
| 13 | Svobodno (УРВИ!) | freelance | public | YES | NO | YES | Case study + real screenshots |
| 14 | Misc. Telegram Bots & CRMs | freelance | private | NO | NO | NO | Collective list |
| 15 | ARC | open-source | public | YES | NO | YES | Case study + real app screenshots |
| 16 | CUMock | university | public | YES | YES | NO | Case study + mock competition UI |
| 17 | AI Office v2 | personal | public | MAYBE | YES if included | NO | Repo link or merged narrative |

---

## Recommended Portfolio Priority (Top 7)

1. **Cashback Targeting Platform** — strongest corporate backend + data story.
2. **ARC** — flagship open-source, public, visually demonstrable.
3. **CIAN Mole / Real Estate Analytics** — strongest freelance, clear business value.
4. **Double Kiss** — real product with real frontend, good full-stack demonstration.
5. **Svobodno (УРВИ!)** — live public URL, easy to screenshot and link.
6. **RAG Onboarding Agent** — best AI story with tangible human impact.
7. **CUMock** — unique, fun, shows system design + real-time challenges.

Honorable mentions for AI case studies: AI Code Review, AI CI Refactor Bot, n8n Cashback Audience Automation.

---

## Global TODOs for Human Review

- [ ] **Reconfirm T-Bank public metrics:** Verify which numbers ($600K+, 5x speedup, 40-60 hrs/month, 48% context reduction) are cleared for public portfolio use.
- [ ] **T-Bank branding:** Decide whether mock UIs should use T-Bank/Tinkoff visual identity or be fully generic.
- [ ] **Missing directories:** Several referenced project directories do not exist in the repo (`documents/projects/double-kiss-loyalty`, `documents/projects/ГОША ПРОЕКТ/commercial_real_estate_analysis`). Populate or remove references.
- [ ] **Screenshot inventory:** For projects marked "Real screenshots? = YES", schedule a session to capture or request them.
- [ ] **Mock UI scope:** Confirm whether "need mock" projects should be static images, interactive HTML, or Figma frames.
- [ ] **AI Office clarification:** Distinguish corporate AI Office (item 8) from personal AI Office v2 (item 17) to avoid narrative confusion.
- [ ] **GitHub links:** Add repository URLs for ARC, CUMock, and AI Office v2 to the portfolio if they are public and polished.
