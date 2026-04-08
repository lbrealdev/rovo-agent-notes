# Daily Triage Prompts

Reusable prompts for daily Jira Service Management triage operations.

**Use when:** Starting your shift, reviewing your queue, or triaging noisy alerts.

---

## 1) List Today's Unassigned Tickets

Use this when you start your shift and want to see what is new and unassigned.

```
List today's new unassigned <PROJECT> tickets in a table (Key, Summary, Status, Reporter, Created, SLA).
```

---

## 2) Assign to Me + Add Initial Customer Reply

Run this after you have seen the list and are ready to act on tickets.

**Step 1 (Read-only):**
```
Show me all unassigned <PROJECT> tickets from the last 24 hours in a table (Key, Summary, Status, Reporter, Created).
```

**Step 2 (After confirmation):**
```
/update-work-items
Assign all listed tickets to me and add "Ticket under review. We'll update you shortly." as a customer reply.
```

---

## 3) Review & Improve Ticket Description

Use this for any ticket that looks unclear and you want an on-call-friendly description.

```
Improve this ticket description for on-call clarity and paste the improved version back:

[PASTE DESCRIPTION]
```

---

## Daily Prompts

Quick prompts for daily standups and queue reviews.

**Note:** For My Tickets prompts, see `quick-prompts.md`.

---

### Create User Story Template

```
Create a user story description template for <PROJECT> with: As a [role], I want [goal], so that [benefit]. Include acceptance criteria placeholders.
```

### Summarize Ticket Comments

```
Summarize the comments on Jira issue <TICKET-KEY>: what questions were asked, what answers were given, and current status.
```

### Ignore Jira Context

```
Ignore the Jira context for now; I want to talk about [topic] instead.
```
