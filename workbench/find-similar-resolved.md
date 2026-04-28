# Find Similar Resolved Tickets

Use when: You have a ticket In Progress and want to find similar tickets you've already resolved to apply past patterns.

---

## Main Prompt

```text
I'm working on ticket <TICKET-KEY> (currently In Progress).

Please search for tickets I previously resolved (within last 90 days) that are related to this one.

Use the summary and description of <TICKET-KEY> to find matches based on content similarity.

For each related resolved ticket found:
- Show: Key, Summary, Status, Resolution
- Show: My final comment/resolution note
- Explain: Why it's related (matching keywords/concepts)

Limit to 10 most relevant matches.
```

---

## With Resolution Draft

```text
I'm working on ticket <TICKET-KEY> (currently In Progress).

Please search for tickets I previously resolved (within last 90 days) that are related to this one.

Use the summary and description of <TICKET-KEY> to find matches based on content similarity.

For each related resolved ticket found:
- Show: Key, Summary, Status, Resolution
- Show: My final comment/resolution note
- Explain: Why it's related (matching keywords/concepts)

Limit to 10 most relevant matches.

Then:
- Compare <TICKET-KEY> with the most similar resolved ticket side-by-side
- Identify patterns/lessons from the resolved ticket that apply
- Draft a resolution comment for <TICKET-KEY> based on those patterns
```

---

## JQL Templates

### My Resolved Tickets (Last 90 Days)

```jql
project = <PROJECT>
AND assignee = currentUser()
AND statusCategory = Done
AND resolved >= -90d
ORDER BY resolved DESC
```

### By Keyword (Manual Search)

```jql
project = <PROJECT>
AND assignee = currentUser()
AND statusCategory = Done
AND (summary ~ "<KEYWORD>" OR description ~ "<KEYWORD>")
AND resolved >= -90d
ORDER BY resolved DESC
```

---

## Tips

- This prompt works well for API-generated tickets (like AWS Health notifications) where the reporter is always the same
- Rovo will match based on content similarity in summary and description
- Always review the draft comment before posting to ensure accuracy
- For AWS Health tickets, common keywords: "AWS Health", "notification", "event", specific service names

---

## Example

**Current ticket:** <TICKET-KEY> (AWS Health notification - S3 bucket policy change)

**Prompt:**
```text
I'm working on ticket <TICKET-KEY> (currently In Progress).

Please search for tickets I previously resolved (within last 90 days) that are related to this one.

Use the summary and description of <TICKET-KEY> to find matches based on content similarity.

For each related resolved ticket found:
- Show: Key, Summary, Status, Resolution
- Show: My final comment/resolution note
- Explain: Why it's related (matching keywords/concepts)

Limit to 10 most relevant matches.

Then:
- Compare <TICKET-KEY> with the most similar resolved ticket side-by-side
- Identify patterns/lessons from the resolved ticket that apply
- Draft a resolution comment for <TICKET-KEY> based on those patterns
```
