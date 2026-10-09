---
name: investigate
description: >-
  Walk one incident end to end: what happened, the RCA and its evidence, what people
  found, what to do next. Use when the person asks why something is broken, wants the
  root cause, or says "investigate" or "debug" about a service, pod, VM or incident.
---

## When to use

- "Why is checkout crashing?" / "Investigate this OOM" / "What's the root cause of INC-…?"
- "Debug the payment service" (find the incident first with `list_incidents`)

## Steps

1. `get_incident(incident_id)`. If the person named a service rather than an id, call
   `list_incidents` and pick the matching one; ask if two fit.
2. If the incident has an `rca_id`: `get_rca(rca_id)`. Read the root cause, contributing
   factors, impact, remediation and rollback steps, and the evidence behind each finding.
3. `what_changed(incident_id)`: deploys, config and scaling changes in the hour before.
   A change right before the incident is the first suspect.
4. `similar_incidents(incident_id)`: earlier incidents on the same fingerprint or resource,
   and how they were resolved.
5. `list_comments(kind="incident", id)` for what the team already found.
6. If the RCA is missing or thin: `environment_snapshot(environment_id)` for the current
   state of that source, using the incident's `environment` (a name works).

## How to answer

In this order: what broke and where; the root cause as the RCA states it, with the evidence
it cites (quote it, do not paraphrase into certainty); the Tasks already proposed (from the
RCA or `list_tasks`); what you would do next, in one or two steps.

Each answer ends with a `next` line; follow it rather than guessing the next call.
If there is no RCA yet, say so. If the RCA failed, offer `retry_rca` (see the `changes`
skill). Never guess a cause the evidence does not support. Ask before any write.

The server also offers this as the `investigate_incident` prompt.
