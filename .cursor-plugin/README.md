<div align="center">
  <img src="../assets/logo.png" alt="RubixKube" width="120" height="120" />

  # RubixKube for Cursor

  **Site Reliability Intelligence inside Cursor.**

  Investigate incidents, review evidence-backed root cause analyses, and track remediation across Kubernetes, AWS, GCP, Linux VMs, and hybrid platforms — without leaving your editor.

  [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](../LICENSE)
  [![Cursor](https://img.shields.io/badge/Cursor-Plugin-black?logo=cursor)](https://cursor.com/marketplace)
</div>

---

## What you can do

Ask questions in plain English and Cursor will pull live signal from your RubixKube tenant.

```
What's going on in prod right now?
Any critical alerts in the last 2 hours?
Why is the payment service crashing?
Show me the RCA for INSIGHT-abc123
What should I work on first?
```

Behind the scenes, the plugin loads **6 skills** that route those questions to **7 MCP tools** backed by your live cluster, cloud, and VM data.

---

## Install

### From the Cursor Marketplace

1. Open **Settings → Plugins → Browse Marketplace**
2. Search for **RubixKube**
3. Click **Install**

### MCP only (no skills)

Add to `.cursor/mcp.json` in your project or user config:

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

### From source

```bash
git clone https://github.com/rubixkube-io/rubixkube-for-ai.git
ln -s "$(pwd)/rubixkube-for-ai" ~/.cursor/plugins/local/rubixkube
```

Restart Cursor after installing.

---

## Authentication

The first time you use a RubixKube tool, Cursor opens a browser window to log in with your RubixKube account — the same login as [console.rubixkube.ai](https://console.rubixkube.ai). The session persists after the first sign-in.

---

## Tools

| Tool | What it answers |
|---|---|
| `platform_status` | Overall dashboard — environments, active issues by severity, RCA count, open actions |
| `active_issues` | Prioritized list of open issues, filterable by environment, namespace, severity |
| `investigate` | Deep dive — root cause + RCA + linked actions for a specific issue |
| `cluster_health` | Full view of one connected environment — infra snapshot, workloads, issues, recent RCAs |
| `pending_actions` | Open remediation tasks, filterable by environment, priority, status |
| `rca_details` | Complete RCA report — root cause, contributing factors, remediation, rollback, evidence |
| `recent_activity` | Timeline of recent insights, RCAs, and action updates |

---

## Skills

Skills guide Cursor's AI on when and how to use each tool automatically. Invoke them with `/` or just ask naturally:

| Skill | Trigger phrases |
|---|---|
| `/infra-status` | "What's going on?", "How's prod?", "Post-deploy check", "Recent activity" |
| `/active-issues` | "What's broken?", "Any critical alerts?", "Open issues in project X" |
| `/investigate` | "Why is X broken?", "Investigate this error", "Debug the payment service" |
| `/cluster-health` | "How's prod?", "Check staging", "Status of environment X" |
| `/pending-actions` | "What should I work on?", "Show action items", "What's pending?" |
| `/rca-report` | "Show me the RCA", "Root cause analysis for X", "Full investigation report" |

---

## Requirements

- A RubixKube account at [console.rubixkube.ai](https://console.rubixkube.ai) (free tier available)
- Cursor 0.45+
- Network access to `https://mcp.rubixkube.ai`

---

## Links

- **Console**: [console.rubixkube.ai](https://console.rubixkube.ai)
- **Docs**: [docs.rubixkube.ai](https://docs.rubixkube.ai)
- **Website**: [rubixkube.ai](https://rubixkube.ai)
- **Issues**: [github.com/rubixkube-io/rubixkube-for-ai/issues](https://github.com/rubixkube-io/rubixkube-for-ai/issues)

---

## License

MIT — see [LICENSE](../LICENSE).
