---
name: aaaai-me-approvals-loop
description: Run work on a paired AAA AI device agent and route destructive commands through the human approvals queue — create, poll, resolve — instead of executing them blind.
api: openapi/aaaai-me-openapi.json
operations:
  - "GET /api/nodes (no operationId in the provider's spec)"
  - "POST /api/tools/invoke"
  - "POST /api/approvals"
  - "GET /api/approvals/{approval_id}"
  - "GET /api/approvals"
  - "POST /api/approvals/{approval_id}/resolve"
method: generated
generated: '2026-09-19'
grounding: >-
  Routes, the tool enum, body fields and the X-Agent-Token header name are quoted from
  openapi/aaaai-me-openapi.json. The purpose of the loop ("review agent operations before execution")
  is from the provider's June 2026 release note. Nothing here was invented.
---

# Act on a device through the approvals loop

AAA AI runs "agents" on a user's own machines (macOS/Linux/Windows agent packages) and lets the
platform drive them. Destructive actions are meant to pause for a human. This is that path.

## 1. Find a paired agent

`GET /api/nodes` — "List connected nodes (agents/devices)". If none is listed, stop: `POST /api/tools/invoke`
runs "on the user's linked/remote agent" and there is nothing to run on. (`DELETE /api/nodes/{node_id}` unpairs.)

## 2. Invoke a single tool

`POST /api/tools/invoke` with `tool` from the contract's enum:
`run_shell_command`, `run_dev_server`, `stop_dev_server`, `list_dev_servers`, `web_ui_test`,
`read_file`, `write_file`, `list_dir`, `amazon_checkout`, `browser`
plus the fields that tool needs (`command`, `path`, `script`, `url`, `urls[]`, `params{}`, `timeout` default 60).
The response is "Tool result (stdout, stderr, returncode)".

Treat `run_shell_command`, `write_file`, `amazon_checkout` and `browser` as consequential: nothing in
the API reverses them, and `amazon_checkout` can spend money. Prefer the approvals route below for any
of them unless the user has explicitly pre-approved that exact action.

## 3. Queue an approval instead of executing

`POST /api/approvals` with `{"agent_id": "<node id>", "command": "<what you intend to run>"}` and the
header **`X-Agent-Token`** (named in the operation summary: "Create approval (agent when destructive +
no TTY)"). The 200 returns an `approval_id`.

## 4. Poll, do not spin

`GET /api/approvals/{approval_id}` — "Get approval status (agent polling)". Poll at a human timescale
(tens of seconds); no rate limit is published, so be conservative. `GET /api/approvals?status=pending|approved|rejected`
lists the queue for a dashboard.

## 5. A human resolves

`POST /api/approvals/{approval_id}/resolve` with `{"approved": true|false}`. Only after `approved`
do you run the command (step 2). A rejection is the reversal: there is no undo once the command has run.

## Rules

- Auth is `X-User-Login` or the session cookie on every call; **401** otherwise.
- No idempotency key: creating the same approval twice queues two approvals. Create once, poll the id.
- Errors are `{"message","status":"error"}` — branch on HTTP status.
