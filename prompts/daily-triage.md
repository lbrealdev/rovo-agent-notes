# Daily Triage Prompts

Reusable prompts for daily Jira Service Management triage operations.

**Use when:** Starting your shift, reviewing your queue, or triaging noisy alerts.

---

## 1) List Today's Unassigned Tickets

Use this when you start your shift and want to see what is new and unassigned.

```text
You are helping me triage Jira Service Management tickets in the <PROJECT> project.

Step 1: Use Jira JQL to find all work items that:
- are unassigned (assignee is EMPTY)
- were created in the last 24 hours
- are not in a Done/Closed status

Use JQL like:
project = <PROJECT>
AND assignee is EMPTY
AND created >= -24h
AND statusCategory != Done
ORDER BY created DESC

Step 2: Return the result in a table with columns:
Key, Summary, Status, Reporter, Created, SLA (if available).

Do NOT update or modify any tickets. This is read-only.
```

---

## 2) Assign to Me + Add Initial Customer Reply

Run this after you have seen the list and are ready to act on tickets.

```text
/update-work-items
You are helping me process Jira Service Management tickets in the <PROJECT> project.

Scope:
Use Jira JQL to find work items that:
- are unassigned (assignee is EMPTY)
- were created in the last 24 hours
- are not in a Done/Closed status

JQL to use:
project = <PROJECT>
AND assignee is EMPTY
AND created >= -24h
AND statusCategory != Done
ORDER BY created DESC

Task:
1) First, show me a table of the matching tickets:
   Key, Summary, Status, Reporter, Created.
2) After I explicitly confirm in chat, for each listed ticket:
   - Assign it to me (<YOUR-USER>).
   - Add a customer-visible comment (reply to customer) with this exact text:
     "Ticket under review. We'll update you shortly."

Guardrails:
- If more than 20 tickets match, stop and ask me to narrow the scope instead of updating all of them.
- If no tickets match, respond with "No tickets found."
```

---

## 3) Review & Improve Ticket Description

Use this for any ticket that looks unclear and you want an on-call-friendly description.

```text
You are helping me improve a Jira Service Management ticket description for on-call engineers in the <PROJECT> project.

For the ticket description I paste below:
1) Grade the current description from 0-10 for clarity and completeness for an on-call engineer.
2) Briefly explain the grade in 2-4 bullet points.
3) Suggest an improved ticket description that:
   - is clear and concise,
   - includes what the problem is, impact, and any known workarounds,
   - can be pasted directly back into the ticket.

Here is the current description:
"""
[PASTE TICKET DESCRIPTION HERE]
"""
```

---

## 4) My Assigned Tickets, Sorted by Urgency/SLA

Use this to see what you personally need to care about first.

```text
You are helping me prioritize my Jira Service Management work in the <PROJECT> project.

Step 1: Use Jira JQL to find work items that:
- are assigned to me (assignee = currentUser() or specifically <YOUR-USER>),
- are not in a Done/Closed status,
- are currently open (exclude any final resolved/closed states).

Use JQL like:
project = <PROJECT>
AND assignee = currentUser()
AND statusCategory != Done
ORDER BY "Time to resolution" ASC, created ASC

Step 2: Return the result in a table with these columns:
Key, Summary, Status, Reporter, Created, "Time to resolution" (or main SLA field), Priority.

Step 3: Based on the SLA/priority and status, suggest the top 5 tickets I should work on next, with 1-2 bullet points each explaining why.
```

---

## 5) Filter "Likely No-Action" Alert-Style Tickets

Use this when tickets include noisy alerts (e.g., AWS notifications, automated monitors) and you want to separate FYI from needs action.

```text
You are helping me triage noisy Jira Service Management tickets in the <PROJECT> project, especially automated alerts (like AWS or monitoring notifications).

Step 1: From <PROJECT>, find work items created in the last 24 hours that:
- are assigned to me or unassigned,
- are not in a Done/Closed status.

Step 2: Based on their summaries and descriptions, classify each ticket into:
- "Action required" - clear problem or customer impact.
- "Likely informational" - status/health/notification with no obvious operator action.
- "Unclear" - needs human review to decide.

Step 3: Return three tables:

A) Action required:
   Columns: Key, Summary, Status, Reporter, Created, Brief reason why it needs action.

B) Likely informational:
   Columns: Key, Summary, Status, Reporter, Created, Why it is probably FYI only.

C) Unclear:
   Columns: Key, Summary, Status, Reporter, Created, What extra info is missing.

Important:
- Do NOT close or update any tickets. This is classification only.
- When unsure, prefer "Unclear" over "Likely informational".
```

---

## JQL Quick Reference

### Unassigned Tickets Created Today

```jql
project = <PROJECT>
AND assignee is EMPTY
AND created >= -24h
AND statusCategory != Done
ORDER BY created DESC
```

### My Open Tickets by SLA

```jql
project = <PROJECT>
AND assignee = currentUser()
AND statusCategory != Done
ORDER BY "Time to resolution" ASC, created ASC
```

---

## Daily Prompts

Quick prompts for daily standups and queue reviews.

**Note:** For My Tickets prompts, see `quick-prompts.md`.

---

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
