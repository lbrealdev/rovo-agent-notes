# SLA Management Prompts

Prompts for managing SLA-related scenarios in Jira Service Management.

**Use when:** Handling SLA expirations, signaling work continuity, or searching ticket notes.

---

## SLA JQL Functions Reference

Jira SLA fields support specific functions for JQL queries. Note: SLA fields cannot be compared to absolute dates.

### Available Functions

| Function | Description | Example |
|----------|-------------|---------|
| `remaining()` | Time left until SLA expires | `remaining("Time to resolution") < 72` |
| `elapsed()` | Time since SLA started | `elapsed("Time to resolution") > 48` |
| `breached()` | Whether SLA has been breached (returns true/false) | `breached("Time to resolution") = true` |
| `withinCalendarHours()` | Check if SLA falls within specific calendar hours | `withinCalendarHours("Time to resolution", "09:00", "17:00")` |

### Important Notes

- SLA functions work with the SLA field name in quotes, e.g., `remaining("Time to resolution")`
- Values are typically expressed in hours when used with comparison operators
- `breached()` returns a boolean, not a duration

---

## 1) Signal Work Continuation (Ticket X → Ticket Y)

Use this when work on a ticket will continue in another ticket due to SLA expiry or other reasons.

```text
You are helping me manage Jira Service Management tickets in the <PROJECT> project.

Context:
- Original ticket: <TICKET-X>
- Continuation ticket: <TICKET-Y>

Task:
1. Show the Key, Summary, and current Status of both tickets.
2. Draft an informational comment for <TICKET-X> with:
   - A clear statement that work is continuing in <TICKET-Y>
   - Brief context of what's being continued
   - Timestamp reference
3. Show the draft comment for my review before posting.

Do NOT post the comment until I confirm.
```

### Clone Ticket (Same Project)

Use this when you need to duplicate a ticket within the same project, keeping the description but adding a reference to the original.

```
/update-work-items
1. Clone <TICKET-KEY> to the same project
2. Assign to me
3. Set status to "In Progress"
4. Preserve the existing description and append "Cloned from: [original ticket URL]" to it
```

---

## 2) SLA Expiring During Team Absence

Use this when you need to identify and handle tickets with SLA expiring while the team is away.

```text
You are helping me manage Jira Service Management tickets in the <PROJECT> project.

Context: The team is away during the following period(s):
<INSERT-AWAY-DATES> (e.g., December 23, 2024 – January 2, 2025)

Step 1: Calculate the total hours in the away period. Then use Jira JQL to find open tickets whose SLA will expire within that window.

Use JQL like:
project = <PROJECT>
AND statusCategory != Done
AND remaining("Time to resolution") < <HOURS-AWAY>
ORDER BY remaining("Time to resolution") ASC

Step 2: Return a table with columns:
Key, Summary, Status, Assignee, remaining("Time to resolution") (hours left), Priority.

Step 3: For each ticket, draft a closure plan:
- Draft an informational comment noting the case will be handled in a new ticket once the team returns
- Suggest an appropriate resolution status (e.g., "Resolved" or "Closed")
- Provide the draft comment text for my review

Do NOT update any tickets. This is read-only with draft comments unless I confirm.
```

---

## 3) Find Tickets with Note Pattern

Use this when you need to find tickets containing specific text in their comments or notes.

```text
You are helping me search Jira Service Management tickets in the <PROJECT> project.

Context: Find tickets containing the pattern "<PATTERN>" in their comments/notes.
(e.g., "escalated", "needs attention", "watch:", "SLA risk")

Step 1: Search ticket comments for the specified pattern.

Use JQL like:
project = <PROJECT>
AND comment ~ "<PATTERN>"
ORDER BY updated DESC

Step 2: Return a table with columns:
Key, Summary, Status, Assignee, Last Comment Match (snippet showing the matched text), Updated.

Step 3: Group results if helpful (e.g., by status, assignee, or recency).

Do NOT update any tickets. This is read-only.
```

---

## JQL Templates

### Tickets with SLA Expiring Soon

```jql
project = <PROJECT>
AND statusCategory != Done
AND remaining("Time to resolution") < <HOURS>
ORDER BY remaining("Time to resolution") ASC
```

### Tickets with Text in Comments

```jql
project = <PROJECT>
AND comment ~ "<PATTERN>"
ORDER BY updated DESC
```
