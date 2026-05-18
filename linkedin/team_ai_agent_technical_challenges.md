# Team AI Agent — Technical Challenges

> Материал для LinkedIn / Portfolio / Case Study

---

## Вариант 1: Короткий технишь для LinkedIn Description

```
Autonomous AI developer that takes a Jira task and delivers a production-ready GitLab Merge Request.

The hard part wasn't calling OpenAI API — it was making an agent reliably plan, implement, test, and submit code in a real production codebase without breaking things.

Key technical challenges we solved:
• Understanding Jira tasks with ambiguous requirements and turning them into actionable implementation plans
• Context window limits: the agent needs to reason over entire codebase, not just a few files
• Hallucination in code generation: preventing the agent from inventing APIs, changing unrelated logic, or breaking contracts
• Self-review loop: making the agent critique its own code before submitting, catching bugs that slipped through generation
• Test execution safety: every generated change runs through the real CI pipeline before reaching a human reviewer
• Legacy code comprehension: the agent must understand 4-year-old Kotlin/Java modules with undocumented business logic
• Integration orchestration: Jira → planning → Git branch → implementation → self-review → test run → MR creation, with rollback on any failure
• Human approval gate: keeping the final sign-off with engineers while automating everything before it

Result: engineering capacity freed for architecture and growth work, CI/CD accelerated by 30%, all flaky tests eliminated.
```

---

## Вариант 2: Развернутый "Behind the Scenes" для Case Study

### The Problem Nobody Talked About

We had two related problems. First, legacy code and flaky pipelines consumed engineering time — manual refactoring competed with delivery deadlines. Second, developers spent most of their capacity on ticket delivery and had no bandwidth for skill growth, tech initiatives, or deep architectural work.

The obvious solution was "use AI to write code." The non-obvious part was making it reliable enough to run autonomously in a production banking environment where a bad merge could affect millions of users.

### Challenge 1: From Jira Task to Implementation Plan

**Symptom:** Jira tasks are written for humans, not machines. "Fix the caching issue in cashback service" is clear to an engineer who knows the domain, but ambiguous for an agent.

**Root cause:** Tickets assume shared context — domain knowledge, code familiarity, architectural conventions. The agent has none of this.

**How we solved it:**
- Built a task enrichment pipeline that fetches related code, recent commits, and documentation before planning
- Added requirement clarification step: the agent asks structured questions when requirements are ambiguous
- Maintained a knowledge base of domain concepts ("cashback audience" = specific set of tables and services)
- Used few-shot prompting with examples of well-specified tasks and their implementation plans

**Result:** The agent can turn 80% of Jira tasks into actionable plans without human clarification.

### Challenge 2: Context Window Limits

**Symptom:** Production codebases have 500K+ lines across 1000+ files. GPT-4's context window can't hold the entire codebase. The agent was either missing critical dependencies or hallucinating APIs.

**Root cause:** LLMs have finite context. You can't dump an entire banking monolith into a prompt.

**How we solved it:**
- Implemented semantic code retrieval: vector embeddings of codebase + similarity search to find relevant files
- Built dependency graph traversal: given a Jira task, the agent traces which services/modules are likely involved
- Hierarchical context: class-level summaries, module READMEs, API contracts — loaded before file-level details
- Iterative refinement: the agent starts with a plan, discovers new files during implementation, and adjusts

**Result:** The agent reasons over the relevant 5% of the codebase instead of needing the whole thing.

### Challenge 3: Preventing Hallucinations in Code

**Symptom:** The agent would invent methods that don't exist, change signatures that break downstream callers, or modify unrelated files.

**Root cause:** LLMs generate plausible-looking code, not necessarily correct code. In a large codebase, there are thousands of APIs and contracts the agent has never seen.

**How we solved it:**
- Static analysis before submission: compile the generated code, check for undefined references
- API validation: cross-generated code against actual interfaces in the codebase
- Diff review: the agent reviews its own diff and explains every change — forcing explicit reasoning
- Regression test execution: run the full test suite on the generated branch before MR creation
- Sandboxed execution: the agent works in an isolated branch — nothing reaches main without human approval

**Result:** Broken builds from agent-generated code dropped to near zero before human review.

### Challenge 4: Self-Review That Actually Catches Bugs

**Symptom:** Simple AI code review finds style issues but misses logic bugs. We needed the agent to catch its own mistakes.

**Root cause:** LLMs are good at pattern matching, bad at deep reasoning about edge cases and state mutations.

**How we solved it:**
- Multi-pass review: the agent reviews its code as a "senior engineer" persona, then as a "QA engineer," then as a "security reviewer"
- Structured critique: must identify potential NPEs, race conditions, off-by-one errors, and security issues explicitly
- Test generation: the agent writes tests for its own changes — if tests fail, the code doesn't ship
- Confidence scoring: low-confidence changes are flagged for human review even if they compile

**Result:** The agent catches 60%+ of its own bugs before human review.

### Challenge 5: Safe Test Execution

**Symptom:** Running tests on AI-generated code could be slow, flaky, or resource-intensive. We couldn't let the agent burn CI hours on broken builds.

**Root cause:** Full test suites take 20-40 minutes. The agent might generate code that fails compilation or breaks contracts, wasting CI capacity.

**How we solved it:**
- Fast-feedback loop: compilation and unit tests run first (2-3 minutes). If they fail, the agent gets immediate feedback
- Incremental testing: only tests related to changed files run on the first pass
- Test result analysis: the agent parses test failures and attempts self-correction
- Resource limits: agent branches have CI timeouts and resource caps
- Pipeline isolation: agent runs don't block human CI pipelines

**Result:** Agent-generated MRs have a 90%+ first-pass CI success rate.

### Challenge 6: Legacy Code Comprehension

**Symptom:** 40% of the codebase was legacy — undocumented business logic, implicit conventions, tribal knowledge. The agent would "refactor" critical paths without understanding why they existed.

**Root cause:** Legacy code isn't just old — it's knowledge compressed into code without documentation. An LLM sees the syntax but misses the intent.

**How we solved it:**
- Annotated legacy modules: we added structured comments marking critical paths, known workarounds, and "do not touch" sections
- Change risk scoring: the agent evaluates whether a change touches high-risk legacy areas
- Conservative defaults: the agent prefers additive changes over modifications to legacy code
- Human escalation: changes to flagged legacy areas automatically require human review before execution
- Historical context: the agent can query git history to understand why specific patterns exist

**Result:** Zero production incidents caused by agent misunderstandings of legacy logic.

### Challenge 7: Orchestration and Failure Recovery

**Symptom:** The pipeline has 7+ steps: Jira fetch → planning → branch creation → implementation → self-review → test execution → MR creation. Any step can fail.

**Root cause:** Distributed agent workflows are inherently fragile. Network issues, API limits, timeouts, and unexpected errors happen constantly.

**How we solved it:**
- State machine: each task has a persisted state. On failure, the agent resumes from the last successful step
- Idempotency: running the same Jira task twice produces the same branch name, and the agent detects existing work
- Rollback: on critical failure, the agent cleans up branches and notifies humans
- Observability: every step is logged with structured output — humans can inspect exactly what the agent did
- Circuit breakers: if the agent fails 3 times on the same task, it escalates to humans

**Result:** 95% of tasks complete end-to-end without human intervention.

### Challenge 8: The Human Approval Gate

**Symptom:** In a bank, you can't let AI merge code unsupervised. But if humans must review everything, the automation loses its value.

**Root cause:** Trust. The business needs assurance that AI-generated code meets quality, security, and compliance standards.

**How we solved it:**
- Tiered approval: low-risk changes (refactoring, test additions) can auto-merge after CI passes. High-risk changes (legacy modifications, security-critical paths) require human review
- Explainable output: the MR includes not just code, but the agent's reasoning — why it made each change, what alternatives it considered
- Diff size limits: the agent refuses to create MRs larger than 500 lines. Large changes are split into multiple tasks
- Audit trail: every action the agent takes is logged for compliance
- Gradual rollout: started with 10% of tasks, scaled to 50% over 3 months as confidence built

**Result:** Human review time reduced by 70% while keeping 100% human oversight on critical changes.

---

## Вариант 3: LinkedIn Post (Story Format)

```
We gave an AI agent access to our production codebase.

Not as a copilot. As a developer.

It takes a Jira task, plans the implementation, writes the code, reviews itself, runs tests, and opens a GitLab MR. Humans approve only at the final gate.

Here's what broke and how we fixed it:

1. Context windows. A banking codebase is 500K+ lines. GPT-4 can't hold it all. We built semantic retrieval + dependency graph traversal so the agent reasons over the right 5% of code.

2. Hallucinations. The agent invented APIs that didn't exist and changed signatures that broke callers. We added static analysis, API validation, and forced the agent to explain every diff line before submission.

3. Legacy code. 40% of our codebase is undocumented tribal knowledge. The agent would "refactor" critical paths without understanding why they existed. We annotated high-risk areas and made the agent conservative around legacy.

4. Self-review that actually works. Simple AI review catches style issues, not logic bugs. We made the agent review its code as senior engineer → QA → security reviewer in sequence.

5. Safe execution. Every change runs through real CI before reaching humans. Compilation fails? The agent gets feedback and retries. Tests break? It analyzes failures and self-corrects.

6. Human trust. This is a bank — we can't let AI merge unsupervised. We built tiered approval: low-risk changes auto-merge, high-risk changes require humans. Every action is logged.

Result: engineering capacity freed for architecture work, CI/CD accelerated by 30%, all flaky tests eliminated.

The future isn't AI assisting developers.
It's developers overseeing AI.
```

---

## Технические темы, которые можно раскрыть глубже

### 1. Agent Architecture
- ReAct vs Plan-and-Execute patterns
- Tool use: Jira API, GitLab API, compiler, test runner, static analyzer
- Memory: short-term (task context) vs long-term (domain knowledge base)

### 2. Code Retrieval System
- Vector embeddings of codebase (CodeBERT, GraphCodeBERT)
- AST-based similarity search
- Dependency graph construction
- Incremental indexing on commits

### 3. Hallucination Mitigation
- Retrieval-Augmented Generation (RAG) for code
- Few-shot prompting with verified code examples
- Self-consistency checks: generate 3 solutions, pick the one that compiles and passes tests

### 4. Testing Strategy
- Unit test generation by the agent
- Mutation testing to verify test quality
- Property-based testing for edge cases
- Test flakiness detection

### 5. Security Considerations
- Preventing injection via Jira task descriptions
- Sandboxing agent execution
- Secrets management: the agent must not leak credentials
- Compliance: audit trails for every action

### 6. Performance Optimization
- Parallel plan generation and code retrieval
- Caching compilation results
- Incremental test execution
- API rate limiting and backoff strategies

### 7. Evaluation Metrics
- How we measured "engineering capacity freed"
- Code quality metrics: review comments per MR, bug escape rate
- Time-to-MR: from Jira creation to MR submission
- Human review time reduction

---

## Рекомендуемый фрагмент для вставки в основной description

**После первого абзаца:**

> The hardest technical challenge wasn't calling an LLM API — it was making an agent reliably reason over a 500K-line production codebase without breaking things. We had to solve context window limits through semantic code retrieval, prevent hallucinations via static analysis and API validation, build a multi-pass self-review that catches logic bugs, and run every generated change through real CI before it reached a human reviewer. Legacy code comprehension was another barrier: 40% of our codebase was undocumented tribal knowledge, so we annotated high-risk areas and made the agent conservative around critical paths. Orchestrating 7+ steps — from Jira fetch to MR creation — required a state machine with failure recovery, idempotency, and human escalation on repeated failures.

---

*Файл подготовлен для portfolio/LinkedIn. Используйте любой вариант или комбинируйте.*
