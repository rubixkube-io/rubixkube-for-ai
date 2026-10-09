---
name: rca
description: >-
  Root cause analyses: the report RubixKube writes for an incident, with the timeline,
  impact, root cause, contributing factors, remediation and rollback steps, proposed Tasks
  and evidence. Use when the person asks for the RCA, the root cause, the postmortem, or
  recent RCAs.
---

## When to use

- "Show me the RCA for INC-…" / "What was the root cause?" / "Recent postmortems"
- A `console.rubixkube.ai/rcas/<id>` link

## Tools

- `list_rcas(environment_id?, limit?)`: recent RCAs with the root cause in one line each.
- `get_rca(rca_id)`: the full report. Get the id from `list_rcas` or an incident's `rca_id`.
- `list_comments(kind="rca", id)` for feedback people left on it.

## Timing

An RCA runs in the background after an incident is created and usually takes a few minutes.
If `get_incident` shows no `rca_id`, say the RCA is not ready and check again later. If the
RCA failed, offer `retry_rca` (the `changes` skill).

## How to answer

Keep the RCA's structure: root cause, contributing factors, impact, remediation, rollback.
Quote the evidence for each claim. Separate what the RCA found from what you infer. Mention
the Tasks it proposed and whether they exist already (`list_tasks`).
