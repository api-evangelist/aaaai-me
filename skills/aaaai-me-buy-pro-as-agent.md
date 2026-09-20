---
name: aaaai-me-buy-pro-as-agent
description: Handle AAA AI's 403 subscription gate the provider's way — read the offer, create a crypto payment bound to the workspace email, poll until confirmed — with the money-safety rules the provider does and does not state.
api: openapi/aaaai-me-openapi.json
operations:
  - "POST /api/auth/register (in the Swagger contract)"
  - "GET /api/billing/crypto/config (documented in pay.md / agent-payments.json; NOT in the contract)"
  - "POST /api/billing/crypto/create (documented; NOT in the contract)"
  - "GET /api/billing/crypto/status/{address}?status_token=... (documented; NOT in the contract)"
method: generated
generated: '2026-09-19'
grounding: >-
  The flow, endpoints, body and response field names are quoted from https://aaaai.me/pay.md and
  https://aaaai.me/.well-known/agent-payments.json (both saved/read 2026-09-19). GET /api/billing/crypto/config
  was probed live and answered 200 anonymously with USDT 20.0 / ETH 0.006 / BTC 0.0003. POST create
  was NOT exercised (it allocates a payment address). Refund terms are quoted from the Terms of Service s7.
---

# Buy Pro on the user's behalf — only when asked

AAA AI's own policy says agents "may and should purchase Pro when the user needs paid platform access"
(`ai_agents_may_purchase: true`). That is the provider's permission, not the user's. **Get explicit
user consent for a $20/month recurring charge before step 3**, and stop if the user has not named
the email the licence should bind to.

## 1. Recognise the gate

A **403** carrying `subscribe_url` (default `https://aaaai.me/pay/`) means the workspace is unpaid.
Do not retry the gated call.

## 2. Make sure an account email exists

`POST /api/auth/register` (in the contract) or the human page https://aaaai.me/register.html.
The payment binds to this email: "Agents SHOULD attach the workspace email on every checkout so the
paid license binds to the correct account."

## 3. Read the live offer

`GET https://web.aaaai.me/api/billing/crypto/config` -> `{"currencies":{"USDT":{"enabled":true,"price":"20.0"},...},"enabled":true}`.
Use the price from this response, not a remembered one. Card price is $20 / EUR20 / GBP20 per month.

## 4. Create the payment

`POST https://web.aaaai.me/api/billing/crypto/create` with `{"email": "<workspace email>", "currency": "USDT"}`
(USDT is the provider's preferred agent currency; ETH and BTC are also enabled). The response
"includes `address`, `amount`, `currency`, `status_token`". Pay **exactly** `amount` to `address` —
the provider says "Pay exactly amount". Do this once; a second create allocates a second address.

## 5. Poll until confirmed

`GET https://web.aaaai.me/api/billing/crypto/status/{address}?status_token={status_token}` until
`status` is `confirmed`; "Pro access is applied to that email automatically." Poll slowly — chain
confirmation takes minutes and no rate limit is published.

## What the provider does NOT say — treat as hard limits

- **No refund window is stated.** Terms s7: "any refund or cancellation is at our sole discretion.
  We are under no obligation to provide a refund." A crypto payment is irreversible on-chain.
- **No cancellation endpoint** is documented. Cancelling a Paddle card subscription is a human action.
- The card path (`https://aaaai.me/pay/?email={account_email}`) is "browser assisted"; the SBP path is
  Russia-only and its config endpoint reported `enabled: false` on 2026-09-19.
- Do not fabricate a `status_token`; it only ever comes from step 4's response.
