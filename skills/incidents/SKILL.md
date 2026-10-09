---
name: incidents
description: >-
  List and read incidents: what the observers detected or people reported, open or
  resolved, by severity, status or environment. Use when the person asks what's broken,
  about alerts, about a specific incident id or console link, or wants incidents in one
  environment.
---

## When to use

- "What's broken?" / "Any critical incidents?" / "Open incidents in staging"
- "Show me INC-… " or a `console.rubixkube.ai/incidents/<id>` link
- "Which incidents are waiting for an answer?"

## Tools

- `list_incidents(open_only=true, severity?, status?, environment_id?, limit?)`. Open by
  default, including resolved incidents still waiting for someone to say what fixed them.
  `severity`: critical, high, medium, low. `status`: NEW, QUEUED_FOR_RCA, RCA_IN_PROGRESS,
  RCA_COMPLETED, RESOLVED, IGNORED. `environment_id` takes an id or a name from
  `list_environments`.
- `get_incident(incident_id)` for one incident in full: events, status history, `rca_id`
  when the RCA is done, the proposed fix.
- `get_incident_resolution(incident_id)` for what the platform thinks fixed it, and the
  numbered candidates while it waits for an answer.
- `list_comments(kind="incident", id)` for what people already wrote.

## How to answer

Lead with severity and status. Give the incident id and the console link so the person can
open it. If `rca_id` is empty, the RCA is still running or has not started: say so and offer
to check again later (`get_incident`) rather than guessing the cause. For changes (close,
edit, retry the RCA, comment) use the `changes` skill.
