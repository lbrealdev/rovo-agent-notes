# SLA Management Prompts

Prompts for managing SLA-related scenarios in Jira Service Management.

**Use when:** Handling SLA expirations, signaling work continuity, or searching ticket notes.

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

---

## 2) SLA Expiring During Team Absence

Use this when you need to identify and handle tickets with SLA expiring while the team is away.

```text
You are helping me manage Jira Service Management tickets in the <PROJECT> project.

Context: The team is away during the following period(s):
<INSERT-AWAY-DATES> (e.g., December 23, 2024 – January 2, 2025)

Step 1: Use Jira JQL to find open tickets whose SLA ("Time to resolution") falls within or overlaps the away period.

Use JQL like:
project = <PROJECT>
AND statusCategory != Done
AND "Time to resolution" >= <START-DATE>
AND "Time to resolution" <= <END-DATE>
ORDER BY "Time to resolution" ASC

Step 2: Return a table with columns:
Key, Summary, Status, Assignee, "Time to resolution" (SLA expiry), Priority.

Step 3: For each ticket, suggest one of:
- Reassign to coverage/on-call
- Extend SLA (if possible)
- Draft customer reply acknowledging delay
- Escalate

Do NOT update any tickets. This is read-only with suggestions unless I confirm.
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
AND text ~ "<PATTERN>"
ORDER BY updated DESC

Step 2: Return a table with columns:
Key, Summary, Status, Assignee, Last Comment Match (snippet showing the matched text), Updated.

Step 3: Group results if helpful (e.g., by status, assignee, or recency).

Do NOT update any tickets. This is read-only.
```

---

## JQL Templates

### Tickets with SLA in Date Range

```jql
project = <PROJECT>
AND statusCategory != Done
AND "Time to resolution" >= <START-DATE>
AND "Time to resolution" <= <END-DATE>
ORDER BY "Time to resolution" ASC
```

### Tickets with Text in Comments

```jql
project = <PROJECT>
AND text ~ "<PATTERN>"
ORDER BY updated DESC
```
