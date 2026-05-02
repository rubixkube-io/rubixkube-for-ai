---
name: active-issues
description: >-
  List open infrastructure issues prioritized by severity. Use when the user
  asks what needs attention, wants to see current alerts, or is looking for
  problems in a specific environment, cloud account/project, VM estate,
  cluster, namespace, or project.
---

## When to Use This Skill

Load when the user asks:
- "What needs attention?" / "What's broken?"
- "Any critical alerts?" / "Show me high severity issues"
- "What's wrong in namespace/project X?" / "Issues in environment Y?"
- "What are the open issues?"

## Tool: `active_issues`

Returns open issues grouped by severity (critical → high → medium → low). Each result includes an `insight_id` for deep investigation.

Parameters (all optional):
- `cluster_id` (str) — scope to one connected environment. The API name is `cluster_id`, but it can represent Kubernetes, cloud, or VM environments.
- `namespace` (str) — scope to one namespace, cloud project/account namespace, or logical grouping when present
- `severity` (str) — filter to `critical`, `high`, `medium`, or `low`

```
active_issues()
active_issues(severity="critical")
active_issues(cluster_id="prod-cluster", namespace="payments")
active_issues(cluster_id="prod-cluster", severity="high")
```

## Reading the Output

Each issue line shows:
- `[insight_id]` — pass this to `investigate` for root cause + RCA + linked actions
- Severity label
- Message (truncated to 70 chars)
- Namespace/project and environment location
- "RCA available" or "No RCA" — if RCA available, full analysis exists

## Chaining

- See an issue worth investigating? Pass its `insight_id` to `investigate` skill.
- Want the full RCA report directly? Use `rca-report` skill with the `report_id` from `investigate` output.
- Looking for what to fix? Use `pending-actions` skill to see linked remediation tasks.
