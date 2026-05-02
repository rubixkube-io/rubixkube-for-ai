---
name: cluster-health
description: >-
  Complete health view of a specific RubixKube environment: infrastructure
  details, resource status, workload counts, active issues, and recent RCAs.
  Use when the user asks about a named environment, cloud project/account, VM
  estate, Kubernetes cluster, or specific cluster_id.
---

## When to Use This Skill

Load when the user asks:
- "How's prod doing?" / "Check staging"
- "What's the status of environment X?"
- "Show me the [cluster/project/account] environment"
- "Is [prod/staging/GCP project/AWS account] healthy?"

## Tool: `cluster_health`

Requires `cluster_id`. In RubixKube this identifier may represent a Kubernetes cluster, cloud project/account, VM environment, or other connected environment. If the user says "prod" or "staging" without an ID, call `platform_status` first to get the environment list and IDs.

```
cluster_health(cluster_id="prod-cluster-id")
```

## Getting the cluster_id

If unknown:
1. Call `platform_status()` — returns connected environments with IDs and names
2. Match the user's name ("prod", "staging", project/account name) to an environment
3. Call `cluster_health(cluster_id="<matched id>")`

## Reading the Output

The report includes:
- **Cluster metadata** — status, version, type, region, resource totals
- **Nodes** — name, status, roles (up to 10 shown)
- **Resources** — workloads, cloud resources, VMs, services, and active namespaces/projects where available
- **Active issues** — severity breakdown (critical/high/medium/low counts)
- **Recent RCAs** — last 5 RCA reports with title and confidence score

## Chaining

- See active issues in the environment? Use `active_issues(cluster_id=...)` for the full list.
- Want to investigate a specific issue? Use `investigate` skill with an `insight_id`.
- Recent RCA with a known ID? Use `rca-report` skill for the complete analysis.
