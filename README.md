# rovo-agent-notes

Personal documentation for Rovo Agent prompts, tips, and daily operations.

---

## Table of Contents

### Guides
- [Document Summaries](guides/document-summaries.md)
  - [Summarize Documentation](guides/document-summaries.md#summarize-documentation)
  - [Summarize Procedure](guides/document-summaries.md#summarize-procedure)

### Jira Prompts
- [Daily Triage](prompts/jira/daily-triage.md)
  - [List Today's Unassigned Tickets](prompts/jira/daily-triage.md#1-list-todays-unassigned-tickets)
  - [Assign to Me + Add Initial Customer Reply](prompts/jira/daily-triage.md#2-assign-to-me--add-initial-customer-reply)
  - [Review & Improve Ticket Description](prompts/jira/daily-triage.md#3-review--improve-ticket-description)
  - [My Assigned Tickets, Sorted by Urgency/SLA](prompts/jira/daily-triage.md#4-my-assigned-tickets-sorted-by-urgencysla)
  - [Filter "Likely No-Action" Alert-Style Tickets](prompts/jira/daily-triage.md#5-filter-likely-no-action-alert-style-tickets)
  - [JQL Quick Reference](prompts/jira/daily-triage.md#jql-quick-reference)
  - [Daily Prompts](prompts/jira/daily-triage.md#daily-prompts)
- [Ticket Analysis](prompts/jira/ticket-analysis.md)
  - [Close AWS Health Notification Tickets](prompts/jira/ticket-analysis.md#1-close-aws-health-notification-tickets)
  - [Filter Informational Tickets](prompts/jira/ticket-analysis.md#2-filter-informational-tickets-aws-example)
  - [JQL Templates](prompts/jira/ticket-analysis.md#jql-templates)
  - [Tips](prompts/jira/ticket-analysis.md#tips)
  - [Summary Templates](prompts/jira/ticket-analysis.md#summary-templates)
- [Reopened Tickets](prompts/jira/reopened-tickets.md)
  - [TL;DR](prompts/jira/reopened-tickets.md#tldr)
  - [Best Practice Workflow](prompts/jira/reopened-tickets.md#best-practice-workflow)
  - [Taking Action](prompts/jira/reopened-tickets.md#taking-action)
  - [Tips](prompts/jira/reopened-tickets.md#tips)
- [SLA Management](prompts/jira/sla-management.md)
  - [SLA JQL Functions Reference](prompts/jira/sla-management.md#sla-jql-functions-reference)
  - [Signal Work Continuation](prompts/jira/sla-management.md#1-signal-work-continuation-ticket-x--ticket-y)
  - [SLA Expiring During Team Absence](prompts/jira/sla-management.md#2-sla-expiring-during-team-absence)
  - [Find Tickets with Note Pattern](prompts/jira/sla-management.md#3-find-tickets-with-note-pattern)

### Other Prompts
- [Special Commands](prompts/prompts-special.md)
  - [Assign + Comment](prompts/prompts-special.md#1-assign--comment)
  - [Status Change + Comment](prompts/prompts-special.md#2-status-change--comment)
  - [Search + Assign + Comment](prompts/prompts-special.md#3-search--assign--comment)
  - [Status + Resolution + Close](prompts/prompts-special.md#4-status--resolution--close)
  - [Bulk Action](prompts/prompts-special.md#5-bulk-action)
  - [JQL + Update](prompts/prompts-special.md#6-jql--update)
- [Proofreading](prompts/proofreading.md)
  - [General Proofreading](prompts/proofreading.md#general-proofreading)
  - [Client Messages](prompts/proofreading.md#client-messages-projectaws-context)
  - [Message Templates](prompts/proofreading.md#message-templates)

### JQL Queries
- [My Tickets JQL](queries/jql/my-tickets.md)
  - [My Open Tickets](queries/jql/my-tickets.md#my-open-tickets)
  - [My Open Tickets (Assignee Only)](queries/jql/my-tickets.md#my-open-tickets-assignee-only)
  - [My Tickets by SLA](queries/jql/my-tickets.md#my-tickets-by-sla)

---

## Repository Structure

```
.
├── guides/
│   ├── document-summaries.md    # Summarize Confluence/AWS docs
│   └── .md
├── prompts/
│   ├── jira/
│   │   ├── daily-triage.md      # Daily triage operations
│   │   ├── reopened-tickets.md  # Handle reopened tickets
│   │   ├── ticket-analysis.md  # Analyze & close tickets
│   │   └── .md
│   ├── prompts-special.md       # Lean multi-line prompts
│   └── proofreading.md         # Message proofreading
└── queries/
    └── jql/
        └── my-tickets.md       # JQL queries for my tickets
```

---

## Quick Links

| Category | File | Purpose |
|----------|------|---------|
| Daily Work | `prompts/jira/daily-triage.md` | List, assign, prioritize tickets |
| Analysis | `prompts/jira/ticket-analysis.md` | Analyze and close informational tickets |
| Special Commands | `prompts/prompts-special.md` | Multi-action prompts with Rovo commands |
| Reopened Tickets | `prompts/jira/reopened-tickets.md` | Handle reopened tickets |
| Proofreading | `prompts/proofreading.md` | Polish messages before sending |
| Documentation | `guides/document-summaries.md` | Summarize Confluence/AWS docs |
| JQL | `queries/jql/my-tickets.md` | Reusable JQL queries |

---

## Getting Started

1. Copy prompts from the relevant category
2. Replace `<PROJECT>`, `<TICKET-KEY>`, `<YOUR-USER>` placeholders
3. Paste into Rovo Chat
4. Review output before applying any changes

---

## Contributing

This is a personal knowledge base. Feel free to adapt prompts for your own use.
