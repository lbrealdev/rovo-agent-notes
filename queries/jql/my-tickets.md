# My Tickets JQL Queries

Reusable JQL queries for finding your tickets.

---

## My Open Tickets

```jql
project = <PROJECT>
AND statusCategory != Done
AND (assignee = currentUser() OR reporter = currentUser())
ORDER BY priority DESC, updated DESC
```

## My Open Tickets (Assignee Only)

```jql
project = <PROJECT>
AND assignee = currentUser()
AND statusCategory != Done
ORDER BY updated DESC
```

## My Tickets by SLA

```jql
project = <PROJECT>
AND assignee = currentUser()
AND statusCategory != Done
ORDER BY "Time to resolution" ASC, priority DESC
```
