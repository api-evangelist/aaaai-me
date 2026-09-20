---
name: aaaai-me-schedule-and-goals
description: Schedule recurring AAA AI agent work as cron jobs, trigger one on demand, watch the background goal jobs it spawns, and stop or delete cleanly.
api: openapi/aaaai-me-openapi.json
operations:
  - "POST /api/cron/jobs (no operationId in the provider's spec)"
  - "GET /api/cron/jobs"
  - "GET /api/cron/jobs/{job_id}"
  - "POST /api/cron/jobs/{job_id}/trigger"
  - "GET /api/goal-jobs"
  - "GET /api/goal-jobs/{job_id}"
  - "POST /api/goal-jobs/{job_id}/stop"
  - "DELETE /api/cron/jobs/{job_id}"
method: generated
generated: '2026-09-19'
grounding: >-
  Routes and body fields (label, schedule, request, enabled, work_until_goal) and the schedule example
  "0 9 * * *" are quoted from openapi/aaaai-me-openapi.json. The cron -> goal-job link is an inference
  from the work_until_goal field description and is labelled as such. Nothing else was invented.
---

# Schedule recurring work

Base URL `https://web.aaaai.me`; `X-User-Login` header or session cookie on every call.

## 1. Create the job

`POST /api/cron/jobs`
```json
{"label": "morning digest", "schedule": "0 9 * * *", "request": "<the natural-language task>", "enabled": true, "work_until_goal": false}
```
`schedule` is a cron expression (spec example `0 9 * * *`). `work_until_goal` is described as
"Continue with tools and recovery until verified completion" — set it only when the task has a
checkable end state, because it lets the run keep going and use tools until it decides it is done.

The 200 is "Created job". **No idempotency key exists**: a retried POST schedules a duplicate. Create
once, then `GET /api/cron/jobs` to confirm before creating again.

## 2. Inspect and run on demand

- `GET /api/cron/jobs` — list; `GET /api/cron/jobs/{job_id}` — one job.
- `POST /api/cron/jobs/{job_id}/trigger` — "Run cron job now". Use this to test the request text
  once before leaving it on a schedule.

## 3. Watch the work it produces

`GET /api/goal-jobs` — "List background goal jobs for the current user"; `GET /api/goal-jobs/{job_id}`
for status. (Inference, not a documented link: a `work_until_goal` run appears here.)

## 4. Stop and clean up

- `POST /api/goal-jobs/{job_id}/stop` halts a running goal job. This is the only reversal on this
  surface; anything the job already did through tools is not undone.
- `DELETE /api/cron/jobs/{job_id}` removes the schedule. There is no restore; re-create if needed.
- Set `enabled: false` (via a fresh POST is not an update — the contract has no PUT/PATCH on cron
  jobs) — so pausing means delete + re-create.

## Rules

- No pagination on either list; no rate-limit headers published.
- Errors are `{"message","status":"error"}`; 401 = missing `X-User-Login`; 403 with `subscribe_url` = unpaid workspace.
