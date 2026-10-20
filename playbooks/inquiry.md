# Playbook: Technical Inquiry & Architectural Spike

**Goal:** Investigate a technical question, evaluate architectural options, and provide a documented recommendation without committing production code.

## Phase 1: Problem Demarcation
1. Analyze the core technical challenge, inquiry, or spike requirements directly from the user's prompt (or from `.ai/local/[TICKET_ID]/ticket.md` if provided).
2. Inspect the project codebase to map the existing landscape:
   - Component tree, state management patterns, routing in `apps/web`
   - API endpoints, data models, middleware in `apps/api`
   - Schema and relationships in `packages/db`
3. Document the exploration scope directly in chat (or in [.ai/local/[TICKET_ID]/[TICKET_ID]-analysis.md](file:///.ai/local/[TICKET_ID]/[TICKET_ID]-analysis.md)).
4. **PROCEED** to Phase 2.

## Phase 2: Gap Analysis
1. Audit constraints, browser compatibility, performance bottlenecks, and bundle size impacts.
2. Formulate open questions, ambiguities, and missing specifications.
3. Present your gap assessment directly in chat (or save to [.ai/local/[TICKET_ID]/[TICKET_ID]-gaps.md](file:///.ai/local/[TICKET_ID]/[TICKET_ID]-gaps.md)) using [.ai/blueprints/gap-analysis.md](file:///.ai/blueprints/gap-analysis.md).
4. **PROCEED** to Phase 3.

## Phase 3: Trade-Off Analysis & Recommended Architecture
1. Propose 2 to 3 distinct architectural approaches to answer the inquiry.
2. For each path, construct a comparative breakdown:
   - **Pros & Cons:** Performance, user experience, developer velocity, maintenance overhead.
   - **Blast Radius:** Affected components, refactoring scope, potential breaking changes.
3. Propose a clear, evidence-based engineering recommendation directly in chat (or in [.ai/local/[TICKET_ID]/[TICKET_ID]-implementation.md](file:///.ai/local/[TICKET_ID]/[TICKET_ID]-implementation.md)).
4. **STOP.** Present your design findings to the engineer. Wait for authorization before writing ADRs or code.

## Phase 4: ADR Capture & Proof-of-Concept
1. Finalize the recommendation based on developer feedback.
2. Draft a standardized Architectural Decision Record (ADR) under `.ai/adr/ADR-[TICKET_ID].md`.