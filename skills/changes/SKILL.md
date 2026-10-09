---
name: changes
description: >-
  Changes to incidents, recorded under the person's name: report a new incident, correct
  one, close one, answer what fixed it, run the RCA again, comment. Use when the person
  wants to create or close an incident, retry an RCA, or leave a note for the team.
---

## When to use

- "Report an incident: checkout is slow" / "Create an incident for the DB failover"
- "Close INC-…" / "It was the rollback that fixed it" / "Run the RCA again"
- "Add a comment: we found the OOM at 03:12"

## Tools

- `report_incident(environment_id, message, severity, where?, description?)`. The answer
  carries the new incident id, the console link and a note that the RCA runs in the
  background: check `get_incident` after a few minutes, then `get_rca`.
- `edit_incident(incident_id, message?, severity?, affects?)`: only what changes.
- `close_incident(incident_id)` when it is resolved.
- `get_incident_resolution` then `answer_incident_resolution(incident_id, choice, note?)`:
  choice is a candidate number, `no_change` if it recovered on its own, or `other` with a note.
- `retry_rca(incident_id)` for a failed or poor RCA. It goes back in the queue; the new RCA
  takes a few minutes.
- `post_comment(kind, id, body, reply_to?)` on an incident, Task or RCA. Markdown. Write for
  the team: findings and evidence, not the chat.

## Rules

Every write is recorded under the signed-in person's name, so confirm before each one:
show the exact title, severity and environment (or the comment text) and wait for a yes.
Never close an incident because it looks quiet; close it when the person says it is
resolved. Do not promise an RCA result; say when to check back.
