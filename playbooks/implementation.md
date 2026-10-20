# Playbook: Implementation Code Proposals (--mode=implementation)

**Goal:** Produce exact, high-quality code blocks. In Phase 3, code is drafted in the implementation proposal (in chat or in `.ai/local/`). Once approved in Phase 4, full workable code is applied to the codebase.

## Input Flexibility
Specifications can be provided directly in the chat prompt or via `.ai/local/[TICKET_ID]/ticket.md`. Local file creation is strictly optional.

## Phase 1: Code Map & Reuse Check
1. Fetch requirements directly from the user's prompt (or from `.ai/local/[TICKET_ID]/ticket.md` if provided).
2. Build a verified Code Map for the active project. For each file, verify existence via file search or grep before adding to the map.
3. **Reuse-First (MANDATORY):** Before proposing any new UI component, hook, or utility, search existing modules (`apps/web/src/shared/ui/`, `apps/web/src/shared/lib/`). If found, reuse or extend—never duplicate.

## Phase 2: Proposed Full Workable Code
1. For each change in the Code Map, provide the complete, compilable code block:
   - **Frontend Components (`apps/web` or `src/`):** React 19 / Modern React, TypeScript (`strict`), CSS variables from project design tokens, TanStack Query hooks, Lucide icons.
   - **Backend Services (`apps/api`):** Fastify 5 route handlers, typebox/zod validation schemas, context integration.
   - **Database (`packages/db`):** Drizzle ORM schema declarations, pgvector embedding columns, migrations.
2. **Zero Placeholder Rule:** Provide full workable code. No `// TODO: add implementation`, no incomplete interfaces, no missing imports.
3. Include the exact file path, imports, exported symbols, and test scenarios.
4. Output the proposal directly in chat (or in `.ai/local/[TICKET_ID]/[TICKET_ID]-implementation.md`) strictly following [.ai/blueprints/implementation-report.md](file:///.ai/blueprints/implementation-report.md).
