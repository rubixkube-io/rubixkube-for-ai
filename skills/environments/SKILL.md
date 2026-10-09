---
name: environments
description: >-
  The organization's sources (Kubernetes clusters, VMs, cloud accounts, connected tools),
  their health, the environments they are labelled with, and the latest infrastructure
  snapshot of one source. Use when the person asks what is connected, how one
  environment is doing, or needs an environment id for another tool.
---

## When to use

- "What's connected?" / "Which environments do we have?"
- "How's the prod cluster?" / "What's running on the staging VM?"
- Any other tool needs an `environment_id`.

## Tools

- `list_environments()`: id, name, kind (kubernetes, vm, aws, gcp, azure, or a connected
  tool), status, last heartbeat, and the environment labels (staging, production).
- `environment_snapshot(environment_id)`: the latest snapshot of one source. Nodes,
  workloads and their status for Kubernetes; host metrics, processes and services for a VM.
  Call once per investigation, not repeatedly.

## How to answer

Name sources by their name, not their id, and say which environment label they carry.
A source whose last heartbeat is old is likely disconnected: say so plainly. For incidents
in one environment, pass its id or name to `list_incidents`.
