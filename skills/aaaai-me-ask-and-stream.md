---
name: aaaai-me-ask-and-stream
description: Authenticate against AAA AI, then get an answer from its multi-expert pipeline — one-shot, streamed over SSE, inside a persistent chat, or through the OpenAI-compatible endpoint.
api: openapi/aaaai-me-openapi.json
operations:
  - "POST /api/auth/login (no operationId in the provider's spec)"
  - "POST /api/ask"
  - "POST /api/query"
  - "POST /api/query/stream"
  - "POST /api/chats"
  - "POST /api/chats/{chat_id}/messages"
  - "GET /v1/models"
  - "POST /v1/chat/completions"
method: generated
generated: '2026-09-19'
grounding: >-
  Every route above exists verbatim in openapi/aaaai-me-openapi.json (Swagger 2.0, AAAAI API 1.1.0,
  host web.aaaai.me). Body fields are the ones the spec declares. Auth behaviour is from the spec's
  ApiKeyAuth definition, the live 401 text and https://aaaai.me/auth.md. Nothing here was invented.
---

# Ask AAA AI a question

Base URL `https://web.aaaai.me`. JSON in, JSON out, except the SSE route.

## 0. Authenticate

The contract defines one scheme: header `X-User-Login` (apiKey). Without it, protected routes return
**401** `{"message":"Authentication required. Please login or provide X-User-Login header.","status":"error"}`.

- Browser-style: `POST /api/auth/login` with `{"login": "...", "password": "..."}` sets a `session`
  cookie (HttpOnly, 30 days). An empty body returns **400** `Login and password required`.
- Programmatic: send `X-User-Login: <value>` on every call. The docs say keys are created in the
  product under Settings -> API keys; the format is not published, so do not guess it.
- A **403** with a `subscribe_url` field means the workspace is unpaid. See the
  `aaaai-me-buy-pro-as-agent` skill; do not retry the same call in a loop.

## 1. Pick the shape of the call

| Need | Route | Body |
|---|---|---|
| One answer, no history | `POST /api/ask` | `{"query": "..."}` |
| One answer, optional image, optional chat | `POST /api/query` | `{"query": "...", "chat_id": <int>, "image": "<base64>", "human_like": <bool>}` — `query` required |
| Tokens as they arrive | `POST /api/query/stream` | same as `/api/query`; response is `text/event-stream` |
| A persistent thread | `POST /api/chats` then `POST /api/chats/{chat_id}/messages` | `{"query": "...", "conversation_history": [...], "human_like": <bool>, "image": "..."}` |
| Your existing OpenAI client | `GET /v1/models`, `POST /v1/chat/completions` | `{"model": "...", "messages": [...], "max_tokens": <int>}` |

`chat_id` is an **integer**. `/api/query/stream` is the only route the spec marks as an SSE stream;
the OpenAI-compatible route does not declare a `stream` flag, so assume a single JSON response there.

## 2. Rules that keep you out of trouble

- **No idempotency key exists.** A retried `POST /api/chats` makes a second chat. Create once, keep the id.
- **No pagination.** `GET /api/chats` returns whatever it returns; do not send `page`/`cursor`.
- **Errors are `{"message","status":"error"}`** with no code field; branch on the HTTP status.
- **No rate-limit headers** are published; back off on 5xx yourself.
- Attachments go to `POST /api/chats/{chat_id}/attachments` (file upload) before the message that refers to them.
- Web search is a per-message toggle in the UI; the API bodies above expose no such flag, so do not add one.
