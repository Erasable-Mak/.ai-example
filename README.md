# AI Architecture Engine v2.0
> Autonomous, safety-gated AI assistant engine preconfigured for modern TypeScript/React applications and easily retargetable to any project.

> **IMPORTANT SETUP INSTRUCTION:**  
> Before using this repository in your workspace, **rename this folder from `.ai-example` to `.ai`** (placed directly in the root of your project repository).  
> The AI bootloader, playbooks, and commands expect the directory to be named `.ai` in your repository root.

---

## 0. AI Bootloader & Intent Routing (Trigger: "Read .ai")

When the user says **"read .ai"**, **"load .ai"**, or starts any task in this repository, the AI must immediately:
1. Load [rules.md](file:///./rules.md) for non-negotiable coding, docstring, testing, and safety constraints.
2. Load [context.md](file:///./context.md) to understand the active codebase structure and tech stack.
3. Route to the appropriate playbook based on the user's goal:

| User Goal | Files to Read | Output / Action Target |
|---|---|---|
| **Catch up on context / session history** | [.ai/history/](file:///./history/) (read latest `chat-00X.md`) | Resumes context from prior architectural discussions. |
| **Write or update automated tests** | [.ai/playbooks/tests.md](file:///./playbooks/tests.md) & [.ai/blueprints/test-report.md](file:///./blueprints/test-report.md) | Vitest test suites adhering to AAA pattern and strict type safety. |
| **Formulate manual / QA test plans** | [.ai/playbooks/test-plan.md](file:///./playbooks/test-plan.md) & [.ai/blueprints/test-plan.md](file:///./blueprints/test-plan.md) | End-to-end scenario matrices and regression boundaries. |
| **Implement a new feature or component** | [.ai/playbooks/story.md](file:///./playbooks/story.md) & [.ai/playbooks/implementation.md](file:///./playbooks/implementation.md) | Full workable code with zero TODOs or placeholders. |
| **Debug an issue or regression** | [.ai/playbooks/bug.md](file:///./playbooks/bug.md) & [.ai/blueprints/bug-report.md](file:///./blueprints/bug-report.md) | Root cause analysis and minimal blast-radius fix. |
| **Technical spikes & architecture spikes** | [.ai/playbooks/inquiry.md](file:///./playbooks/inquiry.md) & [.ai/adr/](file:///./adr/) | Trade-off breakdown and ADR drafting. |
| **Switch / retarget to another project folder** | [.ai/context.md](file:///./context.md) (Section 4) | Re-scans target folder and adapts engine dynamically. |

---

## 1. Quick Commands

### Active Project Work
To analyze any feature, bug, or ticket (e.g. `FEAT-101`), run:
```text
Load .ai/rules.md and .ai/context.md. Analyze ticket FEAT-101 and draft full workable TypeScript code.
```

### Retargeting to Another Project Folder
To reconfigure the `.ai` engine for another project or folder in this workspace, simply ask:
```text
Update this .ai as per this project: [PROJECT_FOLDER_NAME]
```
*(The AI will scan the target folder's package.json, tech stack, and structure, and update `.ai/context.md` automatically).*

---

## 2. Core Principles & Standards

1. **Full Workable Code Standard:**  
   The AI writes **production-ready, complete code**. No `// TODO`, no partial snippets, and no placeholders. Every component has complete imports, typed interfaces, state handling (loading/error/empty), and styled JSX.

2. **No Emojis:**  
   Zero emojis across all code, docstrings, reports, and communications.

3. **Strict 1500-Line History Rolling Rule:**  
   Conversation history is persisted in [`.ai/history/`](file:///./history/). Each history file has a strict **1500-line limit**. When a file reaches ~1500 lines, the AI automatically rolls over and creates the next file (`chat-002.md`, `chat-003.md`, etc.), preserving an unbroken audit trail.

4. **Phase-Gated Safety:**  
   The AI will never edit your source code without permission. It traces the architecture (Phase 1), audits gaps (Phase 2), designs the implementation (Phase 3), and **pauses to request approval** before executing changes (Phase 4).

---

## 3. Directory Inventory

```text
.ai/
├── README.md               # [THIS FILE] Master engine documentation and intent router
├── ONBOARDING.md           # 2-minute developer onboarding guide
├── rules.md                # Execution rules, safety gates, full workable code & history limits
├── context.md              # Technical stack mapping (and retargeting guide)
├── prompts.md              # Daily engineering prompts for frontend, bugs, and design reviews
├── history/                # Persistent conversation logs (1500 lines per chat-00X.md)
│   └── chat-001.md         # Active session history
├── playbooks/              # Execution blueprints for different ticket categories
│   ├── story.md            # Feature planning, component contracts, and frontend wiring
│   ├── bug.md              # Defect analysis, root-cause verification, and fix verification
│   ├── inquiry.md          # Architecture spikes, trade-off analysis, and ADR generation
│   ├── implementation.md   # Full workable code generation guidelines
│   ├── tests.md            # Vitest unit tests and Playwright E2E guidelines
│   └── test-plan.md        # Formulating manual test plans and regression charts
├── blueprints/             # Standardized markdown templates for AI reports
│   ├── story-plan.md
│   ├── gap-analysis.md
│   ├── bug-report.md
│   ├── implementation-report.md
│   ├── test-plan.md
│   └── test-report.md
├── local/                  # Developer scratchpad (local tickets)
│   └── [TICKET_ID]/        # Ticket-specific folder containing generated reports
└── adr/                    # Architecture Decision Records
```

---

## 4. Active Stack Reference

- **Frontend (`apps/web` or `src/`):** React 19, TypeScript 5.9, Vite 8, React Router 7, TanStack Query 5, Lucide React.
- **Backend (`apps/api` or `server/`):** Fastify 5 / Node 22, TypeScript, JWT auth. (Note: backend architecture is modular and can adopt C++ or Python based on workload needs).
- **Database & Storage:** PostgreSQL + Drizzle ORM + vector embeddings / relational storage.
- **Design System:** CSS variables, design tokens, responsive components.
- **Test Runners:** Vitest (unit/integration), Playwright (E2E).
