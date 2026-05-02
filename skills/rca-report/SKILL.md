---
name: rca-report
description: >-
  Full root cause analysis report for a specific incident. Use when the user
  asks for the complete RCA, wants remediation steps, rollback instructions,
  or evidence for a known incident. Requires a report_id.
---

## When to Use This Skill

Load when the user asks:
- "Show me the RCA" / "Give me the full root cause analysis"
- "What was the investigation for [incident]?"
- "Remediation steps for [issue]"
- "Show me the rollback instructions"
- "What evidence did the system find?"

## Tool: `rca_details`

Requires `report_id`. Get it from:
- `investigate(insight_id=...)` output — the RCA section shows the `report_id`
- `active_issues` output — issues marked "RCA available" have a linked report
- `cluster_health` output — recent RCAs section shows `report_id`s for a connected environment

```
rca_details(report_id="<id>")
```

**Never guess an ID.** Always get `report_id` from a prior tool call.

## Reading the Output

The full RCA document includes:
- **Metadata** — severity, confidence %, completeness %, environment/cluster, namespace/project, timestamp
- **Root Cause** — the definitive finding
- **Contributing Factors** — secondary causes that enabled or worsened the incident
- **Impact** — what was affected and how severely
- **Affected Services** — list of services involved
- **Timeline** — chronological sequence of events
- **Remediation Steps** — numbered, ordered steps to resolve the issue
- **Rollback** — how to revert if remediation causes new problems
- **Evidence** — data sources and observations that support the analysis
- **Action Items** — recommended follow-up tasks with priority and due dates
- **Full Markdown Report** — complete narrative (if available, first 3000 chars shown)

## Chaining

- Have action items from this RCA? Use `pending-actions` skill to see their current status.
- Want to investigate a related issue? Use `investigate` skill with an `insight_id`.
