<div align="center">
  <img src="../assets/logo.png" alt="RubixKube" width="120" height="120" />

  # RubixKube for Claude Code

  **Site Reliability Intelligence in your terminal.**

  Investigate incidents, review evidence-backed root cause analyses, and track remediation across Kubernetes, AWS, GCP, Linux VMs, and hybrid platforms — without leaving your terminal.

  [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](../LICENSE)
  [![Claude Code](https://img.shields.io/badge/Claude%20Code-Plugin-orange?logo=anthropic)](https://code.claude.com)
</div>

---

## What you can do

Ask questions in plain English and Claude Code will pull live signal from your RubixKube tenant.

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

### From the Claude Code Marketplace

```bash
/plugin install rubixkube
```

### From this repository directly

```bash
/plugin marketplace add rubixkube/rubixkube-for-ai
/plugin install rubixkube@rubixkube
```

### MCP only (no skills)

```bash
claude mcp add --transport http rubixkube https://mcp.rubixkube.ai/mcp
```

### From source

```bash
git clone https://github.com/rubixkube/rubixkube-for-ai.git
/install-plugin file://$(pwd)/rubixkube-for-ai
```

---

## Authentication

The first time you use a RubixKube tool, Claude Code opens a browser window to log in with your RubixKube account — the same login as [console.rubixkube.ai](https://console.rubixkube.ai). The session persists after the first sign-in.

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

Skills guide Claude on when and how to use each tool automatically. Invoke them with `/` or just ask naturally:

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
- Claude Code 2.0+
- Network access to `https://mcp.rubixkube.ai`

---

## Links

- **Console**: [console.rubixkube.ai](https://console.rubixkube.ai)
- **Docs**: [docs.rubixkube.ai](https://docs.rubixkube.ai)
- **Website**: [rubixkube.ai](https://rubixkube.ai)
- **Issues**: [github.com/rubixkube/rubixkube-for-ai/issues](https://github.com/rubixkube/rubixkube-for-ai/issues)

---

## License

MIT — see [LICENSE](../LICENSE).
