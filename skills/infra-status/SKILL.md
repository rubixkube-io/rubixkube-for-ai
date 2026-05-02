---
name: infra-status
description: >-
  RubixKube platform overview and recent activity timeline. Use when the user
  asks about overall system status, what's happening in production, post-deploy
  checks, or wants a summary of recent incidents.
---

## When to Use This Skill

Load when the user asks:
- "What's going on in prod?" / "How's the platform?"
- "Anything broken?" / "Is everything healthy?"
- "What happened in the last [N] hours?"
- "Post-deploy check" / "Morning standup summary"
- "Give me an overview of the environment"

## Tools

### `platform_status`
Single-shot dashboard — call this first for any overview request.

Returns: connected environments with health status, active issue counts by severity, total RCA reports, open action count, and active namespaces/projects where available.

```
platform_status()
```

No parameters required. Always available.

### `recent_activity`
Timeline of events — use when the user wants to know *what changed*, not just current state.

Parameters:
- `hours` (int, default 2) — lookback window. Increase for "what happened today?" (8h) or "this week" (168h).
- `cluster_id` (str, optional) — scope to a specific connected environment. The API name is `cluster_id`, but RubixKube environments can include Kubernetes clusters, cloud projects/accounts, and VM estates.

```
recent_activity(hours=2)
recent_activity(hours=8, cluster_id="prod-cluster")
```

## Chaining

- Got active issues from `platform_status`? Use `active_issues` skill for a filtered list.
- See an environment that looks degraded? Use `cluster_health` skill with its `cluster_id`.
- User wants to dig into a specific incident? Use `investigate` skill with an `insight_id`.
