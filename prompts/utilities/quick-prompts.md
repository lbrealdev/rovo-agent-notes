# Quick Prompts

Short conversational prompts for Rovo Agent.

**Use when:** Fast ticket queue reviews, daily standups, quick status checks.

---

## My Tickets

### List Tickets (Bullets)

```text
List my open <PROJECT> tickets as bullets (Key, Summary, Status, Time to resolution)
```

### List Tickets (Table)

```text
Show my open <PROJECT> tickets in a table (Key, Summary, Status, Time to resolution)
```

### Group by Status

```text
Group my <PROJECT> tickets by status (Waiting for support, In Progress, etc.) and show Time to resolution for each
```

### Prioritize by SLA

```text
Show my tickets sorted by SLA urgency (shortest first): Key, Summary, Status, Time to resolution
```

### Summarize

```text
Summarize my <PROJECT> tickets: how many at risk of SLA breach, how many need follow-up, how many waiting on customer
```

---

## Queue & Unassigned

### Weekly Summary

```text
It's Friday. Give me a brief summary of all my assigned issues to close the week: how many are resolved, how many still need action, any SLA at risk.
```

### Summary of Unassigned Issues (Bullets)

```text
Give me a bulleted summary of all open and unassigned issues (Key, Summary, Status, Time to resolution).
```

### Unassigned Issues in Table

```text
Show all open and unassigned issues in a table (Key, Summary, Status, Reporter, Created, Time to resolution).
```

---

## Ticket Utilities

### Improve Ticket Description

```text
Take this Jira issue description and align it to best-practice:

[PASTE DESCRIPTION]
```

### Create User Story Template

```text
Create a user story description template for <PROJECT> with: As a [role], I want [goal], so that [benefit]. Include acceptance criteria placeholders.
```

### Summarize Ticket Comments

```text
Summarize the comments on Jira issue <TICKET-KEY>: what questions were asked, what answers were given, and current status.
```

### Ignore Jira Context

```text
Ignore the Jira context for now; I want to talk about [topic] instead.
```
