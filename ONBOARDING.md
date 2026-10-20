# Developer Onboarding: AI Architecture Engine

Welcome! This guide gets you up and running with the AI assistant in **2 minutes**.

---

## 1. What is the `.ai/` directory?

The `.ai/` engine is your pair-programming architect. It is configured to know our full stack—especially our **TypeScript + React Frontend**—and helps you design, plan, and build features fast.

### Core Guarantees:
1. **Full Workable Code:** The AI will never write `// TODO: implement later` or lazy mock stubs. It writes complete, compilable, production-ready code with full types, styling, and state management (loading, error, empty).
2. **Safety First:** The AI will never edit source code directly without your explicit permission. It plans first, and only codes when you confirm.
3. **Dynamic Retargeting:** Working on another folder or project? Simply tell the AI:  
   `Update this .ai as per this project: [FOLDER_NAME]` and it will adapt its context instantly.
4. **Persistent History:** All conversation history is tracked in `.ai/history/` with a rolling **1500-line limit** per file (`chat-001.md`, `chat-002.md`, etc.).

---

## 2. How to Work (Two Flexible Ways)

### Option A: Direct Chat Prompt (Fastest & Zero Files Needed)
You do not need to create any files in `.ai/local/`! You can simply type your request directly into the chat:
```text
Load .ai/rules.md and .ai/context.md. Build a StatusBadge component in apps/web/src/features/dashboard/ with states: active, pending, archived. Follow full workable code rules.
```
The AI will immediately plan, design, and wait for your confirmation to implement.

### Option B: Local Ticket File (Optional / For Complex Tasks with Attachments)
If you have a complex spec with screenshots or logs:
1. Create a folder: `.ai/local/[TICKET_ID]/` (see `.ai/local/EXAMPLE-001/` for reference).
2. Paste details into `ticket.md`, logs into `logs.md`, and screenshots in `attachments/`.
3. Ask the AI:
```text
Load .ai/rules.md and .ai/context.md. Analyze ticket [TICKET_ID] in .ai/local/[TICKET_ID]/ticket.md.
```

### Confirmation & Execution
When satisfied with any plan or proposal, tell the AI:
```text
Approved. Proceed to Phase 4 and write the full workable code.
```
The AI will implement the components, wire them up to `apps/web`, integrate the design tokens, and verify that `pnpm typecheck` passes!

---

## 3. Retargeting to Another Project
If you ever switch projects or work in a different folder, run:
```text
Update this .ai as per this project: [YOUR_PROJECT_FOLDER]
```
The AI will automatically inspect the new directory and re-tune `.ai/context.md` to match your new project.
