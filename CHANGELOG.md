# Changelog

All notable changes to the RubixKube plugin are documented here. The format is based on
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and versions follow
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.2.0] - 2026-10-10

### Added

- `search_knowledge`: find a service, host, person or resource in the knowledge graph, with
  what it connects to (incidents, RCAs, changes).
- `ask_knowledge`: a plain-words question answered from the organization's recorded history.
- A `knowledge` skill that says when to use them, and the investigator agent uses them.

## [2.1.0] - 2026-10-10

Answers are written for the model that reads them, not copied from the API.

### Added

- `similar_incidents`: earlier incidents on the same fingerprint or resource, from the
  knowledge graph.
- `what_changed`: deploys, config and scaling changes in the minutes before an incident.
- `platform_status` opens with one headline sentence and an attention list.
- Every incident, RCA and Task carries a `next` line naming the tool to call.

### Changed

- Status words are the console's: Cause found, RCA failed, RCA running, Waiting, To do,
  In progress. Ids come with the `INC-` short form and a console link. Times read as
  "12 minutes ago". A source's row carries its environment labels and whether it is
  connected.
- Incident and RCA pages no longer carry the markdown copy of the report or embeddings.
- Writes answer with what changed and who did it.
- An environment can be named by its name as well as its id.

## [2.0.0] - 2026-10-10

The plugin now matches the RubixKube console: the same words (Incident, RCA, Task,
Environment) and the same changes a person can make there.

### Added

- Writes, all recorded under the signed-in person's name: `report_incident`,
  `edit_incident`, `close_incident`, `answer_incident_resolution`, `retry_rca`,
  `create_task`, `update_task`, `move_task`, `assign_task`, `post_comment`.
- Reads: `list_environments`, `environment_snapshot`, `list_incidents`, `get_incident`,
  `get_incident_resolution`, `list_rcas`, `get_rca`, `list_tasks`, `get_task`,
  `list_comments`, `platform_status`.
- Prompts (slash commands in Claude Code, Cursor and VS Code): `what_needs_attention`,
  `investigate_incident`, `turn_rca_into_tasks`, `morning_summary`.
- Resources you can attach as context: `rubixkube://environments`,
  `rubixkube://incidents/open`, `rubixkube://incidents/{id}`, `rubixkube://rcas/{id}`,
  `rubixkube://tasks/open`.
- A read-only `rubixkube-investigator` agent for Claude Code.
- Sign-in stays signed in: the server refreshes your session in the background instead of
  asking you to sign in again every day.

### Changed

- Skills renamed and rewritten: `status`, `incidents`, `investigate`, `environments`,
  `tasks`, `rca`, `changes` replace `infra-status`, `active-issues`, `investigate`,
  `cluster-health`, `pending-actions`, `rca-report`.
- Tools renamed: `active_issues` is `list_incidents`, `cluster_health` is
  `environment_snapshot` plus `list_environments`, `pending_actions` is `list_tasks`,
  `rca_details` is `get_rca`, `investigate` is `get_incident` plus `get_rca`,
  `recent_activity` is covered by `platform_status` and `list_rcas`.

### Removed

- The server code is no longer in this repository. The plugin only needs the URL.

## [1.0.0] - 2026-05-03

Initial release for the Cursor and Claude Code marketplaces: six skills and a hosted MCP
server with seven read-only tools.
