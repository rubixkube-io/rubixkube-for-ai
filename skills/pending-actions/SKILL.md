---
name: pending-actions
description: >-
  List open remediation action items with priority and linked incident context.
  Use when the user asks what to work on, wants to see their action queue, or
  is tracking remediation progress for an incident.
---

## When to Use This Skill

Load when the user asks:
- "What should I work on?" / "What's on my plate?"
- "Show me open action items" / "What's pending?"
- "Actions for environment X" / "High priority items"
- "What's being worked on?" / "Remediation progress"

## Tool: `pending_actions`

Returns open actions grouped by priority (high → medium → low). Each action shows its linked insight or RCA ID so you can trace back to the originating incident.

Parameters (all optional):
- `cluster_id` (str) — scope to one connected environment. The API name is `cluster_id`, but it can represent Kubernetes, cloud, or VM environments.
- `priority` (str) — `high`, `medium`, or `low`
- `status` (str) — filter by status: `todo`, `assigned`, `in_progress`, `waiting`, `review`

```
pending_actions()
pending_actions(priority="high")
pending_actions(cluster_id="prod-cluster")
pending_actions(status="in_progress")
pending_actions(cluster_id="prod-cluster", priority="high")
```

## Reading the Output

Each action shows:
- `[action_id]` — unique identifier
- Title — what needs to be done
- Status — todo / assigned / in_progress / waiting / review
- Cluster (if scoped)
- "From: INSIGHT-[id]" or "From: RCA-[id]" — the originating incident

## Chaining

- Want full context on the linked incident? Use `investigate(insight_id=...)` with the linked ID.
- Need the complete RCA before acting? Use `rca-report` skill with the linked `report_id`.
- Not sure which environment to filter by? Use `platform_status` first to get environment IDs.
