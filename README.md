# rovo-agent-notes

Personal documentation for Rovo Agent prompts, tips, and daily operations.

---

## Table of Contents

### Guides
- [Document Summaries](guides/document-summaries.md)
  - [Summarize Documentation](guides/document-summaries.md#summarize-documentation)
  - [Summarize Procedure](guides/document-summaries.md#summarize-procedure)

### Jira Prompts
- [Daily Triage](prompts/daily-triage.md)
  - [List Today's Unassigned Tickets](prompts/daily-triage.md#1-list-todays-unassigned-tickets)
  - [Assign to Me + Add Initial Customer Reply](prompts/daily-triage.md#2-assign-to-me--add-initial-customer-reply)
  - [Review & Improve Ticket Description](prompts/daily-triage.md#3-review--improve-ticket-description)
  - [My Assigned Tickets, Sorted by Urgency/SLA](prompts/daily-triage.md#4-my-assigned-tickets-sorted-by-urgencysla)
  - [Filter "Likely No-Action" Alert-Style Tickets](prompts/daily-triage.md#5-filter-likely-no-action-alert-style-tickets)
  - [JQL Quick Reference](prompts/daily-triage.md#jql-quick-reference)
  - [Daily Prompts](prompts/daily-triage.md#daily-prompts)
- [Ticket Analysis](prompts/ticket-analysis.md)
  - [Close AWS Health Notification Tickets](prompts/ticket-analysis.md#1-close-aws-health-notification-tickets)
  - [Filter Informational Tickets](prompts/ticket-analysis.md#2-filter-informational-tickets-aws-example)
  - [JQL Templates](prompts/ticket-analysis.md#jql-templates)
  - [Tips](prompts/ticket-analysis.md#tips)
  - [Summary Templates](prompts/ticket-analysis.md#summary-templates)
- [Reopened Tickets](prompts/reopened-tickets.md)
  - [TL;DR](prompts/reopened-tickets.md#tldr)
  - [Best Practice Workflow](prompts/reopened-tickets.md#best-practice-workflow)
  - [Taking Action](prompts/reopened-tickets.md#taking-action)
  - [Tips](prompts/reopened-tickets.md#tips)
- [SLA Management](prompts/sla-management.md)
  - [SLA JQL Functions Reference](prompts/sla-management.md#sla-jql-functions-reference)
  - [Signal Work Continuation](prompts/sla-management.md#1-signal-work-continuation-ticket-x--ticket-y)
  - [SLA Expiring During Team Absence](prompts/sla-management.md#2-sla-expiring-during-team-absence)
  - [Find Tickets with Note Pattern](prompts/sla-management.md#3-find-tickets-with-note-pattern)

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
├── workbench/                   # Experimental prompts (in testing)
│   └── aws-health-notifications.md
├── guides/
│   ├── document-summaries.md    # Summarize Confluence/AWS docs
│   └── .md
├── prompts/
│   ├── daily-triage.md         # Daily triage operations
│   ├── reopened-tickets.md     # Handle reopened tickets
│   ├── ticket-analysis.md      # Analyze & close tickets
│   ├── sla-management.md       # SLA-aware prompts
│   ├── prompts-special.md      # Lean multi-line prompts
│   ├── quick-prompts.md        # Quick conversational prompts
│   └── proofreading.md         # Message proofreading
└── queries/
    └── jql/
        └── my-tickets.md       # JQL queries for my tickets
```

**Note:** `workbench/` contains prompts being actively developed and tested. Once stable, they may be promoted to `prompts/`.

---

## Getting Started

1. Copy prompts from the relevant category
2. Replace `<PROJECT>`, `<TICKET-KEY>`, `<YOUR-USER>` placeholders
3. Paste into Rovo Chat
4. Review output before applying any changes

---

## Contributing

This is a personal knowledge base. Feel free to adapt prompts for your own use.
