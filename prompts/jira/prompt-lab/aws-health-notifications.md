# AWS Health Notification Ticket Finder

Find AWS Health notification tickets assigned to me that require no action.

**Use when:** Identifying informational AWS notifications that can be quickly resolved.

**Workflow:** Two-step process - first review tickets (read-only), then apply changes after confirmation.

---

## Step 1: Find Tickets (Read-only)

```
In <PROJECT>, find tickets that are assigned to me and open, contain "aws_health" in the description, and are informational-only AWS notifications requiring no action.

Use JQL:
project = <PROJECT> AND assignee = currentUser() AND status != "Resolved" AND description ~ "aws_health" ORDER BY created DESC

Display results in a table with these columns:
| Key | Summary | Status | SLA | Time to SLA | Created |
```

---

## Step 2: Apply Changes (After Confirmation)

```
/update-work-items
For the tickets listed above:
- Add comment: "AWS Health notification received. No action required."
- Change status to "Resolved" or "Closed"
```

### Step 2 - Rovo-crafted Message (Alternative)

```
/update-work-items
For the tickets listed above:
- Review each AWS Health notification and add an appropriate comment explaining why no action is required (e.g., past incident, informational only, etc.)
- Change status to "Resolved" or "Closed"
```

---

## Workflow for AWS Health Notifications

1. Ticket opened from AWS Health notification
2. Assigned with initial note (first-response SLA)
3. Review the AWS Health notification
4. If past incident/notification only:
   - Add comment noting it's an AWS notification
   - Change status to "Resolved" or "Closed"

---

## JQL Template

```jql
project = <PROJECT> AND assignee = currentUser() AND status != "Resolved" AND description ~ "aws_health" ORDER BY created DESC
```
