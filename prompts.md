# AI Starter Prompts

---

## 1. Universal Project Commands

### Retarget the AI Engine to Any Project
Use this command whenever you change repositories or folders in the workspace:
```text
Update this .ai as per this project: [PROJECT_FOLDER_NAME]
```
*(The AI will scan the folder's `package.json`, tech stack, and structure, and update `.ai/context.md` dynamically).*

### Direct In-Chat Task (Zero Files Needed - Recommended)
```text
Load .ai/rules.md and .ai/context.md. Build [FEATURE_OR_COMPONENT_NAME] in apps/web with requirements: [PASTE YOUR REQUIREMENTS HERE].
```

### Optional Ticket Scratchpad Mode
```text
Load .ai/rules.md and .ai/context.md. Analyze ticket [TICKET_ID] in .ai/local/[TICKET_ID]/ticket.md and prepare the implementation plan.
```

---

## 2. The 4-Phase Progressive Workflow

### Phase 1: Discovery & Architecture Trace
Traces files, component hierarchies, routes, and data flows. Zero code generated.
```text
Run Phase 1 for ticket [TICKET_ID]. Trace relevant components in apps/web and generate .ai/local/[TICKET_ID]/[TICKET_ID]-analysis.md.
```

### Phase 2: Gap & Acceptance Criteria Audit
Audits ACs, edge cases, missing API contracts, and UX edge states.
```text
Run Phase 2 for ticket [TICKET_ID]. Audit acceptance criteria and generate .ai/local/[TICKET_ID]/[TICKET_ID]-gaps.md.
```

### Phase 3: Structural Assessment & Implementation Proposal
Outlines the exact TypeScript component definitions, hooks, state, and styles without editing source files.
```text
Run Phase 3 for ticket [TICKET_ID]. Draft the full workable code plan in .ai/local/[TICKET_ID]/[TICKET_ID]-implementation.md.
```

### Phase 4: Applied Execution (Write Full Workable Code)
Applies the changes to the codebase and verifies compilation (`pnpm typecheck`).
```text
Approved. Proceed to Phase 4 (Execution) and implement full workable code for ticket [TICKET_ID].
```

---

## 3. Specialized Frontend & Full-Stack Prompts

### 1. Full Workable Frontend Component Builder
> **Use case:** Build a production-ready React component with complete types and zero placeholders.
```text
Load .ai/rules.md and .ai/context.md. Act as a Principal Frontend Engineer. Build the [COMPONENT_NAME] feature in apps/web/src/features/[FEATURE]/. Adhere strictly to the "Full Workable Code" standard: provide complete TypeScript interfaces, full hook implementations, loading/error/empty states, and style with project design tokens. Do not leave any TODOs or placeholders.
```

### 2. Frontend Performance & Re-Render Audit
> **Use case:** Optimize complex pages, lists, or React Query cache behavior.
```text
Load .ai/rules.md and .ai/context.md. Analyze [COMPONENT_PATH]. Inspect for unnecessary re-renders, stale TanStack Query cache usage, missing useMemo/useCallback optimizations, or layout thrashing. Provide a concrete optimization plan and refactor the component.
```

### 3. Bug Hunting & Root Cause Analysis
> **Use case:** Track down a bug, regression, or broken state.
```text
Load .ai/rules.md and .ai/context.md. Investigate bug in [FILE_OR_FLOW]. Review error logs in .ai/local/[ID]/logs.md, trace the state flow from API call to component render, identify the root cause, and propose a robust, regression-free fix.
```

### 4. Playwright E2E Test Authoring
> **Use case:** Write end-to-end user journey tests for new frontend features.
```text
Load .ai/rules.md and .ai/context.md. Write a Playwright E2E test in apps/web/e2e/[TEST_NAME].spec.ts verifying the user flow for [FEATURE]. Include happy path, validation errors, and empty states.
```
