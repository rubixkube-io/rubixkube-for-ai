---
name: tasks
description: >-
  Tasks are the Fixes and Follow-ups an RCA proposes or a person adds. List them, read
  one, create one, rename or reprioritise, move between statuses, assign. Use when the
  person asks what to work on, about action items or fixes, or wants to create, assign or
  close a Task.
---

## When to use

- "What should I work on?" / "Show me the open Tasks" / "What's assigned to me?"
- "Create a Task to raise the memory limit" / "Assign it to Sam" / "Mark it done"
- "Turn this RCA into Tasks"

## Tools

- `list_tasks(status="todo,in_progress", priority?, limit?)`: statuses todo, assigned,
  in_progress, waiting, review, completed, failed, cancelled; priority critical, high,
  medium, low. Each row has kind (fix or follow_up), assignee, links to incident and RCA,
  and the console link.
- `get_task(task_id)` for the description, links and history.
- `create_task(environment_id, title, priority, kind, description?, incident_id?, rca_id?,
  owner_email?)`. Link it to the incident and RCA it came from.
- `update_task(task_id, title?, priority?)`.
- `move_task(task_id, to, comment)`: the comment says why. Allowed moves are in the tool
  description; a wrong move is refused with the reason.
- `assign_task(task_id, owner_email?)`: a member's email, or empty to unassign.
- `list_comments(kind="task", id)` and `post_comment(kind="task", …)`.

## How to answer

Group by priority, then by status. Say who owns each Task. Before creating, moving or
assigning, show what you are about to do and wait for a yes: these are recorded under the
person's name. When turning an RCA into Tasks, check `list_tasks` first so you do not file
duplicates. The server offers this as the `turn_rca_into_tasks` prompt.
