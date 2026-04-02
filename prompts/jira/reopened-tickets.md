# Reopened Tickets Guide

Quick reference for comparing reopened tickets against their previous closure and similar resolved tickets.

**Use when:** A ticket was closed but reopened by the customer or team.

---

## TL;DR

1. Ask Rovo: *"What changed since closure?"* (compare same ticket)
2. Ask Rovo: *"Find similar closed tickets"* (pattern matching)
3. Review draft response before applying any changes

---

## Best Practice Workflow

### Step 1: Compare to Previous Closure

Use when a colleague closed it and it popped back open.

```text
I'm working a <PROJECT> ticket that was reopened: <TICKET-KEY>.

1) Summarize the last closure attempt:
   - who transitioned it to a closed/resolved state
   - what status/resolution it was set to
   - the last customer-visible comment used to close it
   - any internal notes around that time (if present)
   - timestamps (close + reopen)

2) Summarize why it was reopened:
   - the comment/request that triggered the reopen (customer-visible)
   - what changed in the ticket fields (status, resolution, assignee)

3) Give me a side-by-side comparison:
   "When it was closed" vs "Now"
   including: Status, Resolution, Latest customer message, Next action.
```

### Step 2: Find Similar Closed Tickets

Use when the reopened ticket might match a recurring pattern (AWS notification, known false positive, etc.).

```text
For <TICKET-KEY>, find up to 5 similar tickets that were resolved/closed in the last 30 days.

Method:
- Use JQL/text similarity based on the summary + key phrases in the description/comments.
- Prefer matches with the same request type/component/labels (if available).

For each similar ticket, return a table with:
| Key | Similarity reason | Final status+resolution | What was done | Final customer-visible reply (quoted) |

Then propose:
- Whether <TICKET-KEY> can be closed the same way (yes/no/unclear)
- A draft customer-visible closing reply consistent with the pattern
- Any checks I should do before closing (short checklist)
Do not update the ticket yet.
```

### Step 3: Batch Mode (Multiple Tickets)

```text
I have <N> reopened tickets: <TICKET-1>, <TICKET-2>, <TICKET-3>.

For each ticket:
1) Summarize the last closure attempt (who/when/status/resolution/last public reply).
2) Summarize the reopen trigger (what the customer said / what changed).
3) Classify as:
   - Reopen due to missing info
   - Reopen due to incomplete fix
   - Reopen due to customer confusion / comms
   - Likely duplicate/recurring/no-action pattern
4) For tickets in the last category, find 3 similar closed tickets and extract the exact closure wording used.

Return:
- One table per ticket with the comparison ("Closed then" vs "Now")
- A recommended next action and a draft reply (customer-visible).
Do not transition or comment yet.
```

---

## JQL Templates

### Find Similar Closed Tickets

```jql
project = <PROJECT>
AND statusCategory = Done
AND resolved >= -30d
AND text ~ "\"<keyword1>\"" AND text ~ "\"<keyword2>\""
ORDER BY resolved DESC
```

### Tickets Closed Then Reopened

```jql
project = <PROJECT>
AND statusCategory = Done
AND updated >= -7d
AND resolution CHANGED
```

---

## Taking Action

Once you've reviewed the comparison and drafts, use `/update-work-items` workflow to comment/transition/resolve—but **keep this as a second step** to avoid applying the wrong closure pattern.

---

## Tips

**Use Rovo "search/fetch" style questions** when you don't know the right JQL. Ask Rovo to search first, then refine to JQL.

---

## Sources

- [Chat Actions](https://support.atlassian.com/rovo/docs/chat-actions/)
- [Using Skills in a Chat](https://support.atlassian.com/rovo/docs/use-skills-in-a-chat/)
- [Rovo Search and Fetch](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/using-rovo-search-and-fetch-in-the-atlassian-remote-mcp-server/)
- [Using Ops Guide](https://support.atlassian.com/rovo/docs/using-ops-guide/)
