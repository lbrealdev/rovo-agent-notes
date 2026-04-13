# AGENTS.md

Repository for Rovo (Atlassian AI assistant) prompts and JQL queries for Jira Service Management.

## Critical JQL Syntax Rules

**SLA fields cannot use date comparisons.**
```jql
-- WRONG (will not work):
"Time to resolution" >= "2026-04-03"
-- CORRECT - use SLA functions:
remaining("Time to resolution") < 72
```

**Available SLA functions:**
- `remaining("Time to resolution")` - hours until SLA expires
- `elapsed("Time to resolution")` - hours since SLA started
- `breached("Time to resolution")` - true/false, has SLA been breached
- `withinCalendarHours("Time to resolution", "09:00", "17:00")` - within business hours

**Searching comments:**
```jql
-- Use "comment ~" not "text ~":
comment ~ "<PATTERN>"
```

## Repository Structure

```
prompts/
├── jira/
│   ├── daily-triage.md       # Triage, assign, prioritize tickets
│   ├── ticket-analysis.md   # Analyze and close tickets
│   ├── sla-management.md    # SLA-aware prompts (has JQL reference)
│   └── reopened-tickets.md  # Handle reopened tickets
├── prompts-special.md       # Multi-action prompts
└── proofreading.md          # Message polishing
guides/                      # Documentation
queries/jql/                # Reusable JQL templates
```

## Placeholder Format

Prompts use `<UPPERCASE-WITH-HYPHENS>`:
- `<PROJECT>` - Jira project key (e.g., SUP, IT)
- `<TICKET-KEY>` - Ticket ID (e.g., SUP-123)
- `<YOUR-USER>` - Jira username
- `<PATTERN>` - Search pattern
- `<HOURS-AWAY>` - Hours in away period

## Prompt Conventions

- Prompts include read-only steps first, update steps after explicit confirmation
- Guardrails: "If more than 20 tickets, stop and ask"
- Use `/update-work-items` prefix for prompts that modify tickets

## Markdown Conventions

### Code Blocks for Prompts

All prompt text must be wrapped in triple backticks for easy copy-paste:

```markdown
```text
Your multi-line prompt text here...
```
```

Use language specifiers:
- `text` for plain text prompts
- `jql` for JQL queries
