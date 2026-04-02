# Ticket Analysis Prompts

Prompts for analyzing tickets and determining if action is required or if they can be closed as informational.

**Use when:** You need to quickly assess tickets and identify closure candidates.

---

## 1) Analyze Ticket(s) and Suggest Closure

One-shot analysis to determine if tickets are informational-only and can be closed.

```text
/update-work-items
Analyze ticket(s) <TICKET-KEY(S)> in <PROJECT>:
- Summarize each issue in 3-5 bullet points
- Classify as: Action Required or Informational
- For informational tickets: draft closing comment and suggest status/resolution

Return: Key | Summary | Classification | Draft Comment | Suggested Status
```

---

## 2) Filter Informational Tickets (AWS Example)

Find and process notification-style tickets that typically require no action.

**Use case:** AWS notifications (Health, Budgets, CloudWatch alarms) that are often informational-only.

```text
/update-work-items
In <PROJECT>, find AWS notification-type tickets (Health, Budgets, CloudWatch alarms):

Use JQL:
project = <PROJECT> AND (summary ~ "AWS" OR description ~ "AWS") AND (summary ~ "notification" OR description ~ "notification" OR description ~ "AWS Health" OR description ~ "CloudWatch Alarm" OR description ~ "AWS Budgets") ORDER BY created DESC

For each ticket:
- Show: Key, Summary, Status, Assignee, Created
- Classify: Informational-only or Requires follow-up
- For informational tickets: draft closing comment and suggest status/resolution

Limit to 20 most recent. Read-only unless I confirm changes.
```

---

## JQL Templates

### AWS Notification Filter

```jql
project = <PROJECT> AND (summary ~ "AWS" OR description ~ "AWS") AND (summary ~ "notification" OR description ~ "notification" OR description ~ "AWS Health" OR description ~ "CloudWatch Alarm" OR description ~ "AWS Budgets") ORDER BY created DESC
```

### Alternative: Broader No-Action Search

```jql
project = <PROJECT> AND (summary ~ "notification" OR description ~ "notification" OR description ~ "no action" OR cf[11662] ~ "no action") ORDER BY created DESC
```

---

## Tips

- Always review the suggested comment before posting - verify it matches your tone and the specific situation
- When unsure if a ticket is informational-only, default to requiring follow-up
- Use the AWS example as a template for other notification sources (monitoring tools, automated alerts, etc.)
