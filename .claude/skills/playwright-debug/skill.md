---
name: playwright-debug
description: Debugging workflow for failing or flaky Playwright tests. Use whenever browser tests fail in CI or locally, traces need analysis, locators are unstable, or a frontend flow is timing-sensitive.
---

# Playwright Debug

Use this skill when a Playwright test already exists but is unstable or broken.

## Workflow

1. Reproduce the failure with the narrowest test or spec.
2. Read the failing assertion and classify the failure:
   - locator contract
   - hidden async state
   - network dependency
   - auth/session state
   - viewport/responsive issue
3. Use trace, screenshot, and DOM evidence before changing the test.
4. Fix the smallest real cause.
5. Re-run the affected scope only, then widen if needed.

## Preferred Fix Order

1. Improve the UI contract or accessibility hook if the app is the problem.
2. Replace brittle locators with semantic ones.
3. Add or tighten network mocking where third-party instability leaks into the test.
4. Move from implicit timing to web-first assertions.
5. Only then consider fixture or test restructuring.

## Good Outcomes

- Short root-cause statement.
- Minimal code fix.
- Deterministic rerun.
- Trace-backed explanation if the bug was subtle.

## Anti-Patterns

- Papering over flakiness with extra sleeps.
- Broad retries without finding the cause.
- Editing many tests at once when one shared helper is the real problem.

