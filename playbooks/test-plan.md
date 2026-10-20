# Playbook: QA Test Plan (--mode=test_plan)

**Goal:** Formulate manual QA scenarios, user interaction test data, and a regression verification plan.

## Phase 1: Functional Flow Trace
1. Review feature requirements directly from the user's prompt (or from `.ai/local/[TICKET_ID]/ticket.md` if provided).
2. Trace the user journey:
   - Screen / Page -> User Actions -> State Transitions -> API Requests -> Success / Error Toast
3. Identify impacted UI surfaces and regression boundaries.

## Phase 2: QA Scenarios & Regression Matrix
1. For each requirement, build a scenario table:
   | TC ID | Scenario | Pre-conditions | User Steps | Test Data | Expected Outcome | Pass/Fail Criteria |
2. Cover:
   - **Happy Path:** Standard user flows, form entries, button clicks, page transitions.
   - **Negative Paths:** Validation errors, invalid input types, unauthorized access (401/403).
   - **Edge Cases:** Network timeouts, slow connections, rapid double-clicks, empty state views.
   - **Responsive Views:** Desktop, tablet, mobile viewports.
3. Provide concrete test data sets (valid / invalid / boundary inputs).
4. Output the plan directly in chat (or in `.ai/local/[TICKET_ID]/[TICKET_ID]-testplan.md`) strictly following [.ai/blueprints/test-plan.md](file:///.ai/blueprints/test-plan.md).
