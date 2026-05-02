# Changelog

All notable changes to the RubixKube AI plugin are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-05-03

Initial release for the Cursor and Claude Code marketplaces.

### Added

- 6 skills covering the core SRI workflows:
  - `infra-status` — platform overview and recent activity timeline
  - `active-issues` — prioritized list of open issues by severity
  - `investigate` — deep root-cause investigation with linked actions
  - `cluster-health` — full health view of a connected environment
  - `pending-actions` — open remediation tasks grouped by priority
  - `rca-report` — full evidence-backed root cause analysis report
- Hosted MCP server at `https://mcp.rubixkube.ai/mcp` exposing 7 tools:
  - `platform_status`, `active_issues`, `investigate`, `cluster_health`,
    `pending_actions`, `rca_details`, `recent_activity`
- Auth0-backed login flow shared with `console.rubixkube.ai`
- Self-hosting instructions and source under `server/`
- Kubernetes deployment manifests under `deployments/`
