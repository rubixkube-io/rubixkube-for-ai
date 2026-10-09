<div align="center">
  <img src="assets/logo.png" alt="RubixKube" width="120" height="120" />

  # RubixKube for AI

  **RubixKube from the AI tools you already use.**

  Read what broke, the root cause and the fix. Report or close incidents, run an RCA again,
  create and assign Tasks. Everything is recorded under your name, the same as in the console.

  [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

  Works with **Claude Code**, **Cursor**, **VS Code** and **Claude**.
</div>

---

## What you can ask

```
What needs attention?
Why is checkout crashing?
Show me the RCA for this incident
Report an incident: the payments DB failed over at 03:10
Turn this RCA into Tasks and assign the fix to Sam
Add a comment: we found the OOM in the worker at 03:12
```

RubixKube watches your infrastructure through observers, turns what breaks into
**Incidents**, investigates each one into an **RCA** and proposes **Tasks** (a Fix and
Follow-ups). The plugin gives your AI tool the same reads and changes the console has.

---

## Install

### Claude Code

```bash
/plugin marketplace add rubixkube-io/rubixkube-for-ai
/plugin install rubixkube@rubixkube
```

Or only the MCP server, without the skills and the agent:

```bash
claude mcp add --transport http rubixkube https://mcp.rubixkube.ai/mcp
```

### Cursor

Settings, Plugins, Browse Marketplace, search **RubixKube**, Install. Or add the MCP server
to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "rubixkube": {
      "type": "http",
      "url": "https://mcp.rubixkube.ai/mcp"
    }
  }
}
```

### VS Code, Claude and any other MCP client

Point it at `https://mcp.rubixkube.ai/mcp` (HTTP transport). The RubixKube console's Apps
page has one-click links for Cursor, VS Code and Claude.

### Sign-in

The first time a tool is used, your editor opens a browser window to sign in with your
RubixKube account, the same as [console.rubixkube.ai](https://console.rubixkube.ai). You stay
signed in; the server refreshes the session in the background.

---

## Tools

Reads:

| Tool | What it answers |
|---|---|
| `platform_status` | One overview: sources and health, open incidents by severity, Tasks waiting, RCAs from the last day |
| `list_environments` | The organization's sources (clusters, VMs, cloud accounts, connected tools) and their environment labels |
| `environment_snapshot` | The latest infrastructure snapshot of one source |
| `list_incidents`, `get_incident` | Incidents, open by default, with the RCA id when the RCA is done |
| `get_incident_resolution` | What fixed an incident, or the candidates while it waits for an answer |
| `list_rcas`, `get_rca` | Root cause analyses, one line each or in full with evidence |
| `list_tasks`, `get_task` | Tasks (Fixes and Follow-ups) with status, priority, owner and links |
| `list_comments` | The comment thread on an incident, Task or RCA |
| `similar_incidents` | Earlier incidents on the same fingerprint or resource, from the knowledge graph |
| `what_changed` | Deploys, config and scaling changes in the minutes before an incident |

Changes, recorded under your name:

| Tool | What it does |
|---|---|
| `report_incident` | Report an incident; the RCA runs in the background, fetch it a few minutes later |
| `edit_incident`, `close_incident` | Correct or close an incident |
| `answer_incident_resolution` | Say what fixed a resolved incident |
| `retry_rca` | Run the RCA again |
| `create_task`, `update_task`, `move_task`, `assign_task` | Create, rename, move and assign Tasks |
| `post_comment` | Comment on an incident, Task or RCA |

Every answer is written for a model: the console's status words (Cause found, RCA failed,
Waiting), the `INC-` short id and a console link, times as "12 minutes ago", the source's
environment labels, and a `next` line on each incident, RCA and Task naming the tool to call.

Prompts (slash commands in your tool): `what_needs_attention`, `investigate_incident`,
`turn_rca_into_tasks`, `morning_summary`. Resources you can attach as context:
`rubixkube://environments`, `rubixkube://incidents/open`, `rubixkube://incidents/{id}`,
`rubixkube://rcas/{id}`, `rubixkube://tasks/open`.

---

## Skills and agent

Installed as a plugin, seven skills tell your assistant when and how to use the tools:
`status`, `incidents`, `investigate`, `environments`, `tasks`, `rca`, `changes`. Claude Code
also gets `rubixkube-investigator`, a read-only agent that walks one incident (incident,
RCA, evidence, comments, snapshot) and reports back without changing anything.

---

## Requirements

- A RubixKube account at [console.rubixkube.ai](https://console.rubixkube.ai)
- Network access to `https://mcp.rubixkube.ai`

## Links

- **Console**: [console.rubixkube.ai](https://console.rubixkube.ai)
- **Docs**: [docs.rubixkube.ai](https://docs.rubixkube.ai)
- **Website**: [rubixkube.ai](https://rubixkube.ai)
- **Issues**: [github.com/rubixkube-io/rubixkube-for-ai/issues](https://github.com/rubixkube-io/rubixkube-for-ai/issues)

## License

MIT, see [LICENSE](LICENSE).
