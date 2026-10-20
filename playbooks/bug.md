# Playbook: Bug Investigation & Remediation

## Input Flexibility
Bug descriptions, stack traces, and reproduction steps can be supplied directly in the user's chat prompt or via `.ai/local/[TICKET_ID]/`. Creating local files is strictly optional.

## Phase 1: Discovery & Investigation
1. Analyze the bug description and reproduction steps directly from the user's prompt (or from `.ai/local/[TICKET_ID]/ticket.md` if provided).
2. Trace the execution path:
   `User Action / UI Event` -> `Component State / Hook` -> `API Client Query` -> `Backend Route / DB`
3. Review any error messages, console logs, or stack traces provided in chat or in `.ai/local/[TICKET_ID]/logs.md`.
4. Document Expected vs. Actual behavior directly in chat (or save to `.ai/local/[TICKET_ID]/[TICKET_ID]-analysis.md`) using [.ai/blueprints/bug-report.md](file:///.ai/blueprints/bug-report.md).
5. **PROCEED** to Phase 2.

## Phase 2: Gap & Root-Cause Audit
1. Verify if the bug is due to:
   - Type mismatches or unexpected `null`/`undefined` responses from APIs.
   - Race conditions in React state or stale TanStack Query cache.
   - Unhandled edge cases in form inputs or routing parameters.
   - CSS layout breakage across responsive screen sizes.
2. Present open questions directly in chat (or save to `.ai/local/[TICKET_ID]/[TICKET_ID]-gaps.md`) using [.ai/blueprints/gap-analysis.md](file:///.ai/blueprints/gap-analysis.md).
3. **PROCEED** to Phase 3.

## Phase 3: Blast Radius Assessment & Fix Proposal
1. Propose the minimal, robust, regression-free fix.
2. Assess potential blast radius: Does fixing this component affect other views using the same shared UI primitive or query hook?
3. Present the proposed fix directly in chat (or save to `.ai/local/[TICKET_ID]/[TICKET_ID]-implementation.md`) using [.ai/blueprints/implementation-report.md](file:///.ai/blueprints/implementation-report.md).
4. **STOP.** Wait for engineer confirmation. Do not edit source code without approval.

## Phase 4: Applied Execution (Fix & Verify)
1. Apply the full workable fix to the affected files.
2. Run type-checking (`pnpm typecheck`) and relevant tests to guarantee zero regressions.
3. If applicable, record an Architectural Decision Record (ADR) in `.ai/adr/` if this alters a pattern.