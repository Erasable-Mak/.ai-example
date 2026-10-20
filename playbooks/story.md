# Playbook: Feature Story Implementation

## Input Flexibility
Requirements can be supplied directly in the user's chat prompt or via `.ai/local/[TICKET_ID]/ticket.md`. Creating local files is strictly optional.

## Phase 1: Requirements Mapping
1. Evaluate user stories, functional specs, and acceptance criteria directly from the chat prompt (or from `.ai/local/[TICKET_ID]/ticket.md` if provided).
2. Determine which layer and module owns the work:
   - **Frontend UI / Feature Components**: `apps/web/src/features/<feature>/`
   - **Shared UI / Primitives**: `apps/web/src/shared/ui/`
   - **Client API / Queries**: `apps/web/src/shared/api/` or `apps/web/src/features/<feature>/api/`
   - **Backend Route / Controller**: `apps/api/src/routes/<domain>.ts`
   - **Database Schema & Models**: `packages/db/src/schema.ts`
   - **Shared Core Types & Roles**: `packages/core/src/`
3. Map component hierarchy, props, interfaces, and state dependencies.
4. Present your architectural roadmap directly in chat (or save to `.ai/local/[TICKET_ID]/[TICKET_ID]-analysis.md`) using [.ai/blueprints/story-plan.md](file:///.ai/blueprints/story-plan.md).
5. **PROCEED** to Phase 2.

## Phase 2: Gap & Requirement Audit
1. Audit acceptance criteria against existing codebase components and design tokens.
2. Check for missing API endpoints, missing data fields, ambiguous UI interactions, or unhandled states (loading, error, empty).
3. Present open questions and ambiguities directly in chat (or save to `.ai/local/[TICKET_ID]/[TICKET_ID]-gaps.md`) using [.ai/blueprints/gap-analysis.md](file:///.ai/blueprints/gap-analysis.md).
4. **PROCEED** to Phase 3.

## Phase 3: Component & Architecture Proposal
1. Draft the explicit TypeScript interfaces, component props, and hook signatures.
2. Outline the state management approach (TanStack Query for server state, React hooks for local state).
3. Ensure adherence to the design system (CSS variables, tokens, spacing, responsive layout).
4. Outline the verification plan (Playwright E2E and component tests).
5. Present the implementation proposal directly in chat (or save to `.ai/local/[TICKET_ID]/[TICKET_ID]-implementation.md`) using [.ai/blueprints/implementation-report.md](file:///.ai/blueprints/implementation-report.md).
6. **STOP.** Present the proposal to the developer for confirmation. Do not edit source files without approval.

## Phase 4: Applied Execution (Full Workable Code)
1. Write **full workable code** (zero `// TODO`s, complete typing, full imports, proper error/empty/loading states).
2. Wire routes into the application shell (`apps/web/src/app/` or `main.tsx`).
3. Run verification (`pnpm typecheck`, `pnpm test`).
4. Document the completed feature and user journey.