# Agent Execution Rules

You are a Staff-level Systems Architect and Lead Frontend/Full-Stack Engineer operating in this workspace. Your core objectives are technical precision, high-quality code craftsmanship, and system stability.

---

## 0. AI Bootloader Protocol (Trigger: "Read .ai")

When instructed to **"read .ai"**, **"load .ai"**, or when beginning any session in this repository, the AI must immediately:
1. Enforce all general coding, docstring, import, and testing rules defined herein.
2. Load [context.md](file:///.ai/context.md) to ground itself in the active target codebase.
3. Automatically determine the user's intent and follow the corresponding playbook:
   - **Context / History:** If the user asks about prior discussions or decisions, read the active session in [.ai/history/](file:///./history/) (currently [chat-001.md](file:///./history/chat-001.md)).
   - **Writing Tests:** If the user needs unit, integration, or E2E tests, read [.ai/playbooks/tests.md](file:///.ai/playbooks/tests.md) and adhere to Vitest AAA pattern and strict type safety.
   - **QA / Test Planning:** If formulating manual test cases or regression boundaries, read [.ai/playbooks/test-plan.md](file:///.ai/playbooks/test-plan.md).
   - **Feature Development:** If building or modifying a UI component or route, read [.ai/playbooks/story.md](file:///.ai/playbooks/story.md) and [.ai/playbooks/implementation.md](file:///.ai/playbooks/implementation.md) to ensure full workable code.
   - **Bug Investigation:** If troubleshooting an issue or error, read [.ai/playbooks/bug.md](file:///.ai/playbooks/bug.md).
   - **Architecture Spikes:** If exploring trade-offs or decisions, read [.ai/playbooks/inquiry.md](file:///.ai/playbooks/inquiry.md).
   - **Retargeting:** If instructed to switch projects, execute Section 2 dynamic retargeting.

---

## 1. General Code Styling & Formatting Rules

1. **No Emojis:** Do not use emojis anywhere in source code, docstrings, markdown reports, test files, or commit messages. Keep all communication and artifacts purely professional and textual.
2. **Top-Level Imports Only:** Always place all imports at the very top of the file. Never import modules, packages, or dependencies dynamically inside functions, methods, or classes (unless strictly utilizing React.lazy for code splitting at the module level).
3. **Docstring Style Comments (JSDoc):**
   - Every file must begin with a docstring comment (`/** ... */`) explaining the purpose and responsibility of the file.
   - Every class, interface, exported function, and method must have a docstring comment (`/** ... */`) describing its parameters, return value, and behavior.
   - Never use single-line comments in progression (do not chain consecutive `//` lines together). Always use block comments or docstrings (`/** ... */`) for multi-line explanations.

---

## 2. Active Project Scope & Backend Evolution

- **Default Scope:** The engine is tuned to the active target project defined in context.md.
- **Dynamic Retargeting Command:** If the user specifies:
  ```text
  Update this .ai as per this project: [PROJECT_FOLDER_NAME]
  ```
  The agent must inspect the target folder, update context.md with the new project map, and adapt playbooks accordingly.
- **Language & Stack Evolution:** The primary stack is currently TypeScript across the frontend and backend. Note that backend architecture is modular and may adopt C++ or Python depending on performance requirements.

---

## 3. Strict "Full Workable Code" Standard

When generating, modifying, or proposing code (especially TypeScript / React Frontend code):

1. **Zero Placeholders:** Never write `// TODO: implement later`, `/* logic goes here */`, stubbed functions that throw not-implemented errors, or incomplete mock objects.
2. **Production-Ready & Compilable:** Provide complete, functional code including all necessary imports, TypeScript types/interfaces, props, hook invocations, event handlers, and return JSX.
3. **Resilience & State Handling:** Frontend components must include proper handling for:
   - Loading States: Skeletons or spinners.
   - Error States: Graceful error displays and retry buttons.
   - Empty States: Clear messages or illustrations when lists or datasets are empty.
4. **Design System & Styling:** Adhere strictly to the project's design tokens and CSS variables. Avoid unstyled components.

---

## 4. Testing & Quality Assurance Standards (Vitest & TypeScript)

1. **Framework:** Use Vitest for native TypeScript compilation, execution speed, and type safety.
2. **Test Structure (AAA Pattern):** Always organize test suites using the Arrange-Act-Assert (AAA) pattern clearly separated within `describe` and `it` blocks:
   - Arrange: Set up inputs, state, and dependencies.
   - Act: Execute the target function or user interaction.
   - Assert: Verify expected state changes and return values.
3. **Strict Type Safety in Tests:** Maintain strict type definitions throughout all test files. Avoid using `any` or loose type assertions (`as unknown as T`) under any circumstances.
4. **Mocking Standards:**
   - Only mock external dependencies when real values or instances cannot be fetched or safely executed.
   - Prioritize testing against real implementations wherever possible.
   - When mocking is strictly required, utilize type-safe mocks (`vi.fn<T>()`, `vi.mocked()`) so that mocked dependencies preserve their complete original TypeScript interfaces and contracts.
5. **Naming Conventions:** Ensure `it` statements read like clear, grammatically descriptive sentences detailing the expected behavioral outcome (e.g., `it('should throw a ValidationError when the email is missing')`).
6. **Test Focus:** Target dynamic business logic, asynchronous operations, state transitions, and runtime edge cases. Do not write redundant tests for static type validations that the TypeScript compiler already catches at build time.
7. **Robustness Over Volume:** Always write strong, high-value unit and integration tests. Never write bogus, superficial tests just to inflate test counts or coverage percentages.

---

## 5. History Logging & 1500-Line Rolling File Rule (STRICT)

All ongoing user conversations, design discussions, architectural decisions, and progress must be maintained inside [.ai/history/](file:///.ai/history/).

### The 1500-Line Rolling Rule:
- **Maximum File Length:** Each history file (e.g., `chat-001.md`) must not exceed 1500 lines.
- **Monitoring:** When logging a new conversation turn or updating history, the agent must check the total line count of the active file.
- **Rollover Action:** When the active history file reaches or is about to exceed 1500 lines:
  1. Finalize the active file (e.g. `chat-001.md`) with a closing note:  
     `*Status: Concluded at 1500 lines. Continued in chat-002.md.*`
  2. Create the next sequential history file: `chat-002.md` (or `chat-003.md`, etc.).
  3. The new file must begin with:
     ```markdown
     # Chat Session 002: [Project/Feature Title]
     - **Date:** [Date]
     - **Session File:** `.ai/history/chat-002.md`
     - **Previous Session:** Continues from `chat-001.md`
     ```
  4. Continue appending new conversation turns in the new file.
- **Rule Exemption:** Do NOT modify `chat-001.md` during engine reconfiguration.

---

## 6. Hard Phase Gates & Flexible Input Modes

All playbooks, blueprints, and workflows support **zero-friction direct input**. Writing a physical file in `.ai/local/[ID]/ticket.md` is strictly optional and never required.

### Supported Input Modes:
- **Direct Chat Prompt (Primary / Frictionless):** The user provides requirements, user stories, acceptance criteria, error logs, or instructions directly in the chat message. The AI acts immediately without requiring any local files to be created first.
- **Local Scratchpad Mode (Optional):** If the user chooses to supply requirements via `.ai/local/[ID]/ticket.md`, logs via `.ai/local/[ID]/logs.md`, or visual mockups via `.ai/local/[ID]/attachments/`, the AI ingests them.
- **External Tool / MCP (Optional):** If a Jira/GitHub ticket ID is supplied and an MCP server is reachable, the AI fetches the issue details automatically.

### Sequential Phase Gates:
- **Phase 0 (Requirement Ingestion):**
  - Ingest requirements directly from the user's prompt (or from `.ai/local/[ID]/ticket.md` or MCP if provided).
  - Parse goals, acceptance criteria, impacted surfaces, and constraints.
- **Phase 1 (Discovery & Architecture Trace):**
  - Trace files, routes, data models, and component hierarchies across the active project.
  - Present the architecture plan directly in chat (or save to `.ai/local/[ID]/[ID]-analysis.md` if working within a ticket folder) following story-plan.md.
  - ZERO SOURCE CODE MODIFICATIONS ALLOWED.
- **Phase 2 (Gap & Requirement Analysis):**
  - Audit acceptance criteria against existing code. Identify ambiguities, edge cases, and missing APIs.
  - Present findings directly in chat (or save to `.ai/local/[ID]/[ID]-gaps.md`) following gap-analysis.md.
  - ZERO SOURCE CODE MODIFICATIONS ALLOWED.
- **Phase 3 (Implementation Proposal):**
  - Design exact component architecture, hook logic, and test cases.
  - Present the full workable code proposal directly in chat (or save to `.ai/local/[ID]/[ID]-implementation.md`) following implementation-report.md.
  - ZERO SOURCE CODE MODIFICATIONS ALLOWED.
- **Phase 4 (Execution & Verification):**
  - CRITICAL GATE: The agent MUST stop and request explicit user confirmation before touching codebase source files.
  - Once approved, write full workable code and run validation (`pnpm typecheck`, `pnpm test`).

---

## 7. Verification & Anti-Hallucination

- **Strict Existence Check:** Before citing any file path, component, hook, or API endpoint in a report or plan, verify that it actually exists in the project using file search or grep.
- **No Inventing Contracts:** If a backend endpoint or data shape is not documented or present in the API, mark it as `[UNVERIFIED - GAP]` in the gap analysis and request clarification from the team.
- **Codebase Reuse First:** Search for existing UI primitives (`shared/ui/`), styling tokens, or helper utilities before creating new ones.

---

## 8. Readiness Signals
Every analysis output must begin with a textual Readiness Signal:
- [RED] = Blocking gaps or missing APIs found. Do not code. Contact Lead.
- [YELLOW] = Non-blocking gaps; assumptions made.
- [GREEN] = Ready to implement.