# AAA AI

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

AAA AI (Autonomous Agents Automations; product spelling AAAAI) is a Montenegro-based multi-agent AI platform operated by Kirill Pokidov: a workspace at web.aaaai.me that routes questions through a panel of expert models with debate and verification modes, runs visual workflows with human-approval nodes across a catalog of integrations, pairs desktop "agents" on a user's own machines, and adds Meet — voice and video calls with live AI notes. Sold as a $20/month Pro cloud plan (card, crypto or SBP) or self-hosted. The API is a 102-operation Swagger 2.0 contract on web.aaaai.me (chat, streaming queries, an OpenAI-compatible /v1/chat/completions, approvals, cron jobs, goal jobs, experts, settings) authenticated by an X-User-Login header, plus a documented crypto checkout API that lets an agent buy the subscription autonomously. The static site aaaai.me publishes an unusually complete agent-discovery layer — RFC 9727 api-catalog, OAuth/OIDC/RFC 9728 metadata, ai-plugin.json, an MCP server card, an agentskills.io index, agent-payments.json, llms.txt and the full ai-visibility.org.uk file set — several of whose targets (the named OpenAPI URL, the MCP endpoint, the JWKS) do not exist.

**Areas:** Artificial Intelligence · Agents · Multi-Agent · LLM Orchestration · Meetings · Voice · Video · Workflows · MCP · Agentic Commerce · OpenAI-Compatible · Self-Hosted

## AAA AI on APIs.io

Everything profiled for AAA AI is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/aaaai-me/](https://apis.io/providers/aaaai-me/)** — or go straight to one of the APIs or properties below.

### APIs (17)

- [AAA AI Agent Checkout (Billing) API](https://apis.io/apis/aaaai-me/aaaai-agent-checkout-api/) — The provider-documented purchase surface for autonomous agents, described in https://aaaai.me/pay.md and machine-readably in…
- [AAA AI Agents API](https://apis.io/apis/aaaai-me/aaaai-me-agents-api/) — The Agents API from AAA AI — 3 operation(s) for agents.
- [AAA AI Approvals API](https://apis.io/apis/aaaai-me/aaaai-me-approvals-api/) — The Approvals API from AAA AI — 3 operation(s) for approvals.
- [AAA AI Auth API](https://apis.io/apis/aaaai-me/aaaai-me-auth-api/) — Authentication
- [AAA AI Chat API](https://apis.io/apis/aaaai-me/aaaai-me-chat-api/) — Chat and queries
- [AAA AI Code API](https://apis.io/apis/aaaai-me/aaaai-me-code-api/) — Code-only generation (Cursor / CLI / IDE)
- [AAA AI Cognitive Scaling API](https://apis.io/apis/aaaai-me/aaaai-me-cognitive-scaling-api/) — Cognitive scaling status and control
- [AAA AI Cron API](https://apis.io/apis/aaaai-me/aaaai-me-cron-api/) — The Cron API from AAA AI — 3 operation(s) for cron.
- [AAA AI Debug API](https://apis.io/apis/aaaai-me/aaaai-me-debug-api/) — Debug and development
- [AAA AI Deep Agent API](https://apis.io/apis/aaaai-me/aaaai-me-deep-agent-api/) — The Deep Agent API from AAA AI — 3 operation(s) for deep agent.
- [AAA AI Dynamic Experts API](https://apis.io/apis/aaaai-me/aaaai-me-dynamic-experts-api/) — Dynamic expert creation and management
- [AAA AI Experts API](https://apis.io/apis/aaaai-me/aaaai-me-experts-api/) — Expert system management
- [AAA AI Health API](https://apis.io/apis/aaaai-me/aaaai-me-health-api/) — Health and status
- [AAA AI Nodes API](https://apis.io/apis/aaaai-me/aaaai-me-nodes-api/) — The Nodes API from AAA AI — 2 operation(s) for nodes.
- [AAA AI Settings API](https://apis.io/apis/aaaai-me/aaaai-me-settings-api/) — Platform and expert settings
- [AAA AI User API](https://apis.io/apis/aaaai-me/aaaai-me-user-api/) — Current user and avatar
- [AAA AI Video API](https://apis.io/apis/aaaai-me/aaaai-me-video-api/) — Video sessions

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [aaaai-me-mcp.yml](https://apis.io/servers/aaaai-me/aaaai-me-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Aaaai Me Agentic Access](https://apis.io/agentic-access/aaaai-me/aaaai-me-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Aaaai Me Openapi Overlay](https://apis.io/overlays/aaaai-me/aaaai-me-openapi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Aaaai Me Authentication](https://apis.io/security/aaaai-me/aaaai-me-authentication/)
- [Aaaai Me Domain Security](https://apis.io/security/aaaai-me/aaaai-me-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Aaaai Me Scopes](https://apis.io/scopes/aaaai-me/aaaai-me-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Aaaai Me Plans Pricing](https://apis.io/plans/aaaai-me/aaaai-me-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Aaaai Me Rate Limits](https://apis.io/rate-limits/aaaai-me/aaaai-me-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://aaaai.me/)
- [Documentation](https://aaaai.me/docs.html)
- [Getting started](https://aaaai.me/auth.md)
- [API reference](https://web.aaaai.me/apidocs)
- [Pricing](https://aaaai.me/pay/)
- [Sign up](https://aaaai.me/register.html)
- [Changelog](https://aaaai.me/news/feed.xml)
- [Blog](https://aaaai.me/blog.html)
- [Terms of service](https://aaaai.me/terms-and-conditions.html)
- [Privacy policy](https://aaaai.me/privacy.html)

## API Evangelist rating

**Kin Score 53.1** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 85.7 |
| Contract quality | 42.0 |
| Contract governance | 18.2 |
| Operational transparency | 15.8 |
| Developer ergonomics | 66.1 |
| Access clarity | 65.8 |

**Agent readiness 44.5** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | yes |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 42.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/aaaai-me/](https://apis.io/providers/aaaai-me/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for AAA AI: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/aaaai-me/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
