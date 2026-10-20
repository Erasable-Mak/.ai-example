# Workspace Architecture Context

> **Active Target Project:** `[PROJECT_NAME]` (configured dynamically for your repository)  
> **Dynamic Configuration:** To retarget or update context for any project folder, execute:  
> `Update this .ai as per this project: [FOLDER_PATH_OR_NAME]`

---

## 1. Project Overview & Structure

This engine is designed to support modern TypeScript full-stack applications, microservices, and monorepos.

### Standard Monorepo / Directory Map

```text
[PROJECT_ROOT]/
├── apps/
│   ├── web/        # Frontend: React 19 / Modern React, TypeScript, Vite, React Router, TanStack Query
│   └── api/        # Backend Services: Fastify / Node, TypeScript (or C++/Python)
├── packages/
│   ├── core/       # Shared domain types, interfaces, roles, permissions
│   ├── db/         # Database schema (Drizzle / Prisma / ORM), migrations, vector embeddings
│   └── ui/         # Shared component library and design tokens
├── docs/
│   ├── design/     # Design system, tokens, CSS variables, screen specs
│   └── architecture/ # System design, ADRs, product specs
└── deploy/         # Docker Compose, Helm, CI/CD pipelines
```

---

## 2. Frontend Architecture (`apps/web` or `src/`)

> **Primary Focus:** High-quality, production-ready **TypeScript Frontend** development with **full workable code** (zero placeholders, complete functional components).

### Core Stack
- **Framework & Runtime:** React 19 / Modern React
- **Language:** TypeScript (`strict: true`)
- **Build Tool:** Vite (`@vitejs/plugin-react`)
- **Routing:** React Router DOM (or project-native router)
- **Data Fetching & Server State:** TanStack React Query (v5)
- **Icons & Graphics:** Lucide React / SVG primitives
- **Testing:** Playwright (E2E) and Vitest (Component/Unit)

### Recommended Internal Structure (`src/`)
```text
src/
├── app/            # App shell, root routing, global providers
├── features/       # Domain feature modules:
│   ├── [feature]/      # Feature components, hooks, local state, and API queries
├── layouts/        # Layout wrappers (ConsoleLayout, AuthLayout, DashboardLayout)
├── shared/         # Reusable cross-feature assets:
│   ├── ui/             # Design-system atomic components (Button, Modal, Input, Badge)
│   ├── styles/         # CSS token imports, global styling
│   ├── api/            # Typed API client, fetch helpers, query keys
│   ├── lib/            # Utilities, formatting, date helpers
│   └── config/         # Environment variables & constants
└── main.tsx        # Application root entrypoint
```

### Frontend Engineering Standards
1. **Full Workable Code:** Never output partial templates, stubbed functions, or `// TODO` placeholders. Code must be completely wired with props, state, error/loading fallbacks, and typed API calls.
2. **Design System & Styling:** Utilize CSS custom properties defined in your design system (e.g. `--color-surface`, `--color-accent`, `--font-sans`, `--radius-md`). Maintain consistent aesthetics, clean spacing, and dark/light mode compatibility.
3. **Strict Typing:** All components, props, hooks, and API responses must have explicit TypeScript types or interfaces. Avoid `any`.
4. **State Management:** Use TanStack Query for remote server state and React local state (`useState`, `useReducer`, `useContext`) for UI state.

---

## 3. Backend & Data Layer (`apps/api` & `packages/db`)

### Backend Services (`apps/api`)
- Fastify / Node + TypeScript (or C++ / Python depending on performance and runtime requirements).
- Context-driven request pipeline (authenticates session, sets active tenant context).
- Structured route modules with strict runtime payload validation (TypeBox / Zod).

### Database & Knowledge Schema (`packages/db`)
- Type-safe ORM (Drizzle / Prisma) over PostgreSQL or relational database.
- Vector search extensions (`pgvector`) for semantic retrieval when applicable.
- Clean entity models, foreign key relationships, and migration scripts.

---

## 4. Retargeting the Engine to Any Project

This `.ai` engine is fully generic. To retarget the engine to another folder or repository in the workspace, use:

```text
Update this .ai as per this project: [FOLDER_PATH_OR_NAME]
```

When triggered, the AI will:
1. Scan the specified directory for `package.json`, project configs, language files, and architecture.
2. Update this `context.md` file with the new directory map, tech stack, and build scripts.
3. Align `rules.md` and playbooks with the target project's conventions.