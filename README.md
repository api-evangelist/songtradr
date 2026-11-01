# Songtradr

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

Songtradr is a Santa Monica, California B2B music company that builds licensing, rights and music-data infrastructure for brands, agencies, digital platforms, artists and rightsholders. Founded in 2014, it operates a global sync-licensing marketplace alongside acquired businesses including Bandcamp, 7digital, MassiveMusic, Big Sync Music and the AI music-metadata company Musicube. Its public developer surface is the Songtradr API — a JWT-authenticated REST API, documented with a live OpenAPI 3.1 description, that returns deep music metadata (musical features, genre predictions, tags, taggrams, tag strengths, contributors, similarity vectors) and drives auto-tagging: rightsholders upload audio through a presigned S3 link and Songtradr's models classify it against a taxonomy of 350+ descriptive tags across 30+ categories, then expose semantic search over the results. First-party API clients are published for Python, JavaScript/Node and Ruby.

**Areas:** Music · Music Licensing · Sync Licensing · Music Metadata · audio-tagging · Semantic Search · Machine Learning · Media · Entertainment · Rights Management · Audio

## Songtradr on APIs.io

Everything profiled for Songtradr is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/songtradr/](https://apis.io/providers/songtradr/)** — or go straight to one of the APIs or properties below.

### APIs (3)

- [Songtradr Allowed Values API](https://apis.io/apis/songtradr/songtradr-allowed-values-api/) — The allowed-values API from Songtradr — 1 operation(s) for allowed-values.
- [Songtradr Similarity Vector Controller API](https://apis.io/apis/songtradr/songtradr-similarity-vector-controller-api/) — The similarity-vector-controller API from Songtradr — 1 operation(s) for similarity-vector-controller.
- [Songtradr User API](https://apis.io/apis/songtradr/songtradr-user-api/) — The user API from Songtradr — 15 operation(s) for user.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [songtradr](https://apis.io/servers/songtradr/songtradr/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Songtradr Agentic Access](https://apis.io/agentic-access/songtradr/songtradr-agentic-access/)

#### Collections (3)

Postman and Open Collection request collections.

- [Songtradr Allowed Values API](https://apis.io/collections/songtradr/open-songtradr-allowed-values-api/)
- [Songtradr Similarity Vector Controller API](https://apis.io/collections/songtradr/open-songtradr-similarity-vector-controller-api/)
- [Songtradr User API](https://apis.io/collections/songtradr/open-songtradr-user-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Songtradr Api Overlay](https://apis.io/overlays/songtradr/songtradr-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Songtradr Authentication](https://apis.io/security/songtradr/songtradr-authentication/)
- [Songtradr Domain Security](https://apis.io/security/songtradr/songtradr-domain-security/)

#### Rate limits (1)

Published request limits.

- [Songtradr Rate Limits](https://apis.io/rate-limits/songtradr/songtradr-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.songtradr.com/)
- [Documentation](https://api.songtradr.com/swagger-ui.html)
- [Getting started](https://api.songtradr.com/swagger-ui.html)
- [API reference](https://api.songtradr.com/v3/api-docs)
- [Pricing](https://www.songtradr.com/pro)
- [Sign up](https://www.songtradr.com/signup/personal)
- [Support](https://support.songtradr.com/hc/en-us)
- [Blog](https://www.songtradr.com/blog)
- [Terms of service](https://www.songtradr.com/legals/termsofuse)
- [Privacy policy](https://www.songtradr.com/legals/privacypolicy)
- [GitHub](https://github.com/songtradr)

## API Evangelist rating

**Kin Score 34.3** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 49.0 |
| Contract governance | 4.5 |
| Operational transparency | 23.7 |
| Developer ergonomics | 49.4 |
| Access clarity | 6.6 |

**Agent readiness 31.5** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 15.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/songtradr/](https://apis.io/providers/songtradr/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Songtradr: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/songtradr/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
