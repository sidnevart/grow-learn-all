---
name: initiative-radar
description: Evaluate and shape business or technical initiatives before implementation. Use whenever a new idea, growth initiative, architecture change, optimization, or process improvement is proposed.
---

# Initiative Radar

Use this skill to avoid random scope growth and to keep initiatives measurable.

## When To Use

- New business feature ideas.
- Technical platform or architecture initiatives.
- Reliability, performance, or process improvement proposals.
- Requests that can consume significant time but have unclear ROI.

## Required Output

For each initiative, produce exactly these blocks:

1. `Problem`
- What concrete issue is being solved.
- Who is affected.

2. `Expected Impact`
- Business/operational metric expected to improve.
- Time horizon for observing effect.

3. `Technical Impact`
- Main systems/components affected.
- Expected engineering complexity.

4. `Cost And Risk`
- Delivery cost (low/medium/high).
- Main risks and failure modes.

5. `Recommendation`
- One of: `do`, `park`, `drop`.
- Single-sentence rationale.

6. `Next Experiment`
- Smallest validation step with clear acceptance signal.

## Integration Rules

- Write accepted or parked initiatives to `.codex/memory-bank/initiative-backlog.md`.
- If recommendation is `do`, add an execution slice to `.codex/memory-bank/TODO.md`.
- Keep entries concise and decision-focused.

## Anti-Patterns

- Starting implementation before recommendation and experiment are defined.
- Logging broad ideas without owner, impact, or next step.
- Declaring initiatives as "important" without measurable outcome.
