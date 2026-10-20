# Ticket: EXAMPLE-001 - Incident Status Filter and Dynamic Badge Component

- **Project:** Web Application
- **Target Surface:** Frontend (`apps/web` or `src/`)
- **Type:** Feature Story
- **Priority:** High
- **Assignee:** Unassigned

---

## 1. Description & User Story

As an engineer or incident manager reviewing items in the web console, I want to filter records by their current status and see clear, color-coded status badges on each card so that I can immediately identify active versus resolved items.

---

## 2. Acceptance Criteria

1. **AC1 - Status Badge Component:**
   - Create a reusable, type-safe `StatusBadge` component in `apps/web/src/features/dashboard/ui/StatusBadge.tsx` (or `shared/ui/`).
   - Supports statuses: `investigating`, `mitigated`, `resolved`.
   - Uses design system CSS tokens for pill styling, background colors, and typography.

2. **AC2 - Filter Controls & Server State:**
   - Add a tab or dropdown filter control to the incident list view in `apps/web/src/features/dashboard/`.
   - Selecting a filter status passes the filter parameter to the TanStack React Query hook.
   - Handles loading states with skeleton components while data is refetching.

3. **AC3 - Empty & Error State Handling:**
   - If no incidents match the selected filter, display a clean empty state card with a clear message and a button to reset the filter.
   - If an API error occurs, display an error banner with a retry trigger.

4. **AC4 - Type Safety & Standards:**
   - Strict TypeScript definitions with zero `any`.
   - Top-level imports only.
   - File and component docstrings included.
   - Automated test suite written with Vitest following the Arrange-Act-Assert (AAA) pattern.
