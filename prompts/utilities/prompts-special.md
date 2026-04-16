# Special Prompts

Lean multi-line prompts that combine multiple Rovo actions efficiently.

**Use when:** You need to perform several actions on a ticket at once.

---

## 1) Assign + Comment

Assign a ticket to yourself and add a customer reply.

```text
/update-work-items
Assign <TICKET-KEY> to me (<YOUR-USER>).
Add a customer-visible comment: "Ticket under review. We'll update you shortly."
```

---

## 2) Status Change + Comment

Move a ticket to a new status and update the customer.

```text
/update-work-items
Transition <TICKET-KEY> to "In Progress".
Add a customer-visible comment: "We're looking into this now."
```

---

## 3) Search + Assign + Comment

Find unassigned tickets, then assign and reply to all.

```text
/update-work-items
Find all tickets in <PROJECT> where assignee is EMPTY and created >= -24h.
Assign each to me (<YOUR-USER>).
Add a customer-visible comment: "Ticket under review. We'll update you shortly."
If more than 20 tickets match, stop and ask me to narrow the scope.
```

---

## 4) Status + Resolution + Close

Move a ticket to Done with a resolution and closure message.

```text
/update-work-items
Transition <TICKET-KEY> to "Done".
Set resolution to "Resolved".
Add a customer-visible comment: "This issue has been resolved. Closing ticket."
```

---

## 5) Bulk Action

Apply the same action to multiple tickets.

```text
/update-work-items
For tickets <TICKET-1>, <TICKET-2>, <TICKET-3>:
1) Assign each to me (<YOUR-USER>).
2) Add a customer-visible comment: "Ticket under review. We'll update you shortly."
Show confirmation list before applying changes.
```

---

## 6) JQL + Update

Find matching tickets using JQL, then apply changes.

```text
/update-work-items
Use JQL to find tickets in <PROJECT> with:
- assignee = currentUser()
- statusCategory != Done
- updated >= -7d

For each ticket:
1) Show a table: Key, Summary, Status, Time to resolution.
2) Suggest which tickets to prioritize (top 5).
3) After I confirm, update the status to "In Progress" and add a customer comment.
```

---

## Reference

**Available Rovo commands:**
- `/update-work-items` - update fields, assign, comment, transition
- `/create-work-items` - create new tickets

**Skills used:**
- Jira JQL
- Assign work item
- Comment on work item
- Transition work item

**Documentation:**
- [Chat Actions](https://support.atlassian.com/rovo/docs/chat-actions/)
- [Use Skills in a Chat](https://support.atlassian.com/rovo/docs/use-skills-in-a-chat/)
