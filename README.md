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

AAA AI (Autonomous Agents Automations; product spelling AAAAI) is a Montenegro-based multi-agent AI platform: a workspace at web.aaaai.me that routes questions through a panel of expert models, runs visual workflows with human-approval nodes, pairs desktop agents on a user's own machines, and adds Meet — voice and video calls with live AI notes. Sold as a $20/month Pro cloud plan or self-hosted.

What this profile found (2026-09-19):

- **Contract** — a real Swagger 2.0 document, "AAAAI API" 1.1.0, 102 operations, at `https://web.aaaai.me/api/spec.json` (the URL the Flasgger UI at `/apidocs` loads). Every provider discovery file names `/apispec_1.json` instead, which is a 404. Saved verbatim in `openapi/`.
- **Discovery layer** — aaaai.me serves an RFC 9727 api-catalog, OAuth 2.0 / OpenID / RFC 9728 metadata, ai-plugin.json, an MCP server card, an agentskills.io index, agent-payments.json, llms.txt and the ai-visibility.org.uk file set. Several targets do not exist: the MCP transport URL is a GET-only catalog of third-party stdio servers (POST tools/list -> 405), `/api/mcp` is a 404, and the declared JWKS is a 404. Details in `well-known/`, `mcp/`, `conformance/`.
- **Not an A2A card** — `/.well-known/agent.json` (how this company reached the harvest via a2aregistry.org) is a site manifest with name, url and links only; it fails the AgentCard shape test, so no `a2a/` artifact exists here.
- **Agent commerce** — a documented crypto checkout API lets an agent buy Pro for a workspace email; see `plans/` and `skills/aaaai-me-buy-pro-as-agent.md`.

Links:

- Website: https://aaaai.me/
- Workspace / API host: https://web.aaaai.me/
- API reference (Swagger UI): https://web.aaaai.me/apidocs
- Docs: https://aaaai.me/docs.html
- Agent auth guide: https://aaaai.me/auth.md
- Pricing: https://aaaai.me/pay/
