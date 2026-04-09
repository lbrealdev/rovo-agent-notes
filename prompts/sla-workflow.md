# SLA Workflow Prompts

Prompts for SLA-aware ticket workflows in Jira Service Management.

**Use when:** Handling SLA expirations by cloning/continuing work in a new ticket.

---

## Ticket Cloning Workflow

Use this when a ticket's SLA is at risk and work needs to continue in a new ticket.

### 1) Clone Ticket (Same Project)

Clone the original ticket to the same project, keeping the description but adding a reference to the original.

```
/create-work-items
- Clone <TICKET-KEY> to the same project
- Assign to me
- Preserve the existing description and append "Cloned from: [original ticket URL]" to it
```

### 2) Update Original Ticket

Add a comment to the original ticket pointing to the new clone, then resolve it.

```
/update-work-items
- Add a comment to the original ticket with: "Work continues in [new ticket URL]" — use Jira inline link format: [KEY|URL]
- Resolve the original ticket
```

### 3) Move New Ticket to In Progress

Add a customer reply comment and move the newly created (cloned) ticket to "In Progress".

```
/update-work-items
Add "Continuation of the work that was being done [original ticket]" as a "Reply to customer" comment — use Jira inline link format: [KEY|URL] — and move ticket from "Waiting for Support" to "In Progress"
```
