---
name: playwright-e2e
description: Playwright end-to-end testing patterns for the Svobodno web app and Telegram Mini App web fallback. Use whenever you add, edit, or review Playwright tests, browser flows, fixtures, auth state, or network mocking.
---

# Playwright E2E

Use this skill for reliable browser-level tests.

## Goals

- Test real user flows, not implementation details.
- Keep tests deterministic and debuggable.
- Prefer web fallback and browser-hosted flows over trying to automate Telegram itself.

## Baseline Rules

- Use Playwright Test.
- Prefer semantic locators:
  - `getByRole`
  - `getByLabel`
  - `getByPlaceholder`
  - text-based locators when the UI contract is textual
- Use web-first assertions with `expect(...)`, not manual sleeps.
- Avoid brittle CSS/XPath selectors unless there is no durable user-facing contract.

## Test Design

### Scope

Focus on product flows such as:

- map screen renders
- venue markers or venue list content appear
- point popup opens
- venue page opens
- booking CTA and booking form flows
- basic auth/session restoration behavior

### Isolation

- Mock unstable third-party APIs or external integrations when the test target is not that integration itself.
- Reuse `storageState` for authenticated scenarios when it reduces noise.
- Keep each test independent.

### Browser Matrix

- Default to Chromium first.
- Add mobile viewport coverage when the layout or interaction is mobile-sensitive.
- Broaden to more browsers only when the project needs that confidence.

## Debuggability

- Enable traces for local debugging or CI failures when needed.
- Prefer concise fixtures over hidden global state.
- If a flow is flaky, narrow the failure to one DOM contract, one network dependency, or one timing boundary.

## Anti-Patterns

- `waitForTimeout` as normal control flow.
- Assertions against raw CSS classes when role/text contracts exist.
- One huge end-to-end test covering the whole product.
- Tests that depend on real external map or auth providers unless the task is explicitly an integration smoke test.

## Done Checklist

- Locators are semantic.
- Assertions are web-first.
- External instability is mocked or controlled.
- The test name matches the user flow.
- Failure output is actionable with trace or screenshot support.

