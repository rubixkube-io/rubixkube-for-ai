---
name: investigate
description: >-
  Deep investigation of a specific infrastructure issue. Use when the user
  asks why something is broken, wants to debug a service, pod, cloud resource,
  VM, or references an insight ID. Returns root cause, RCA findings, and linked
  remediation actions.
---

## When to Use This Skill

Load when the user asks:
- "Why is [service/pod/cloud resource/VM/namespace] broken?"
- "Investigate this error / crash / OOM"
- "What's the root cause of [issue]?"
- "Look into insight [ID]"
- "Debug the payment service" / "What's wrong with checkout?"

## Tool: `investigate`

Two modes — prefer `insight_id` when you have it:

### Mode 1: Direct lookup by ID (preferred)
Fetches the insight, its RCA report, and all linked remediation actions in a single call.

```
investigate(insight_id="<id from active_issues output>")
```

### Mode 2: Search by text
Searches insight messages, namespaces, types, and affected resources. Returns matching insights with their IDs.

```
investigate(search="payment service")
investigate(search="OOMKilled")
investigate(search="crashloopbackoff")
```

Use search when the user describes a symptom without an ID. Once you find the relevant insight, call again with its `insight_id` for full details.

## Reading the Output

The investigation report contains:
- **Insight** — severity, status, namespace/project, environment, affected resources, first/last seen
- **Root Cause Analysis** — root cause, contributing factors, impact description, remediation steps, rollback instructions (if RCA exists)
- **Related Actions** — open remediation tasks linked to this issue, with their `action_id`s

If "Root Cause Analysis: not yet generated" — RCA is still in progress. Check back or look at the insight details for initial signals.

## Chaining

- Found a `report_id` in the output? Use `rca-report` skill for the complete RCA document.
- See action items you want details on? Use `pending-actions` skill.
- Want environment-wide context? Use `cluster-health` skill with the `cluster_id` from the insight.
