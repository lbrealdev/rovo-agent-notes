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
1. Clone <TICKET-KEY> to the same project
2. Assign to me
3. Preserve the existing description and append "Cloned from: [original ticket URL]" to it
```

### 2) Update Original Ticket

Add a comment to the original ticket pointing to the new clone, then resolve it.

```
/update-work-items
1. Add a comment to <TICKET-KEY> with: "Work continues in [new ticket URL]"
2. Resolve <TICKET-KEY>
```

### 3) Move New Ticket to In Progress

Move the newly created (cloned) ticket from "Waiting for Support" to "In Progress".

```
/update-work-items
Change the status of <NEW-TICKET> from "Waiting for Support" to "In Progress"
```
