---
name: status
description: >-
  One overview of what RubixKube sees: sources and their health, open incidents by
  severity, Tasks waiting for someone, RCAs finished in the last day. Use when the
  person asks what's going on, what needs attention, how production is, or wants a
  morning summary.
---

## When to use

- "What's going on?" / "What needs attention?" / "How's prod?"
- "Morning summary" / "Anything new since yesterday?"
- Before a deploy or after one, to see the baseline.

## Tools

1. `platform_status` first. It returns the organization's sources (environments), open
   incidents counted by severity with the newest five, Tasks waiting by priority, and RCAs
   from the last 24 hours.
2. `list_incidents` for the full open list when the person wants detail, `list_tasks` for
   Tasks, `list_rcas` for recent RCAs.

## How to answer

Rank by what a person should do first: critical and high incidents without an RCA or with a
failed RCA, then incidents resolved but waiting for "what fixed it", then Tasks in todo with
critical or high priority. One line each: what, where (environment), since when, the next
step, the console link from the tool output. End with what can wait. If an RCA is missing,
say "no RCA yet"; do not invent a cause.

## Words

Incident (not issue or insight), RCA, Task (a Fix or a Follow-up), Environment, Organization.
