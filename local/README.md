# Local Developer Scratchpad

This directory is used for ticket-specific analysis, gap audits, and implementation plans.

## Directory Structure per Ticket

Each ticket or feature being worked on should have its own folder:

```text
.ai/local/[TICKET_ID]/
├── ticket.md       # Ticket description, user stories, acceptance criteria
├── logs.md         # Relevant console errors, stack traces, network payloads
└── attachments/    # UI mockups, screenshots, or error captures
```

## Quick Scaffolding Command

In PowerShell:
```powershell
New-Item -ItemType Directory -Force -Path .ai/local/[TICKET_ID]/attachments
New-Item -ItemType File -Force -Path .ai/local/[TICKET_ID]/ticket.md
New-Item -ItemType File -Force -Path .ai/local/[TICKET_ID]/logs.md
```

See `EXAMPLE-001/` for a complete reference example.
