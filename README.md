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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Songtradr is a Santa Monica, California B2B music company that builds licensing, rights and
music-data infrastructure for brands, agencies, digital platforms, artists and rightsholders.
Founded in 2014, it operates a global sync-licensing marketplace alongside acquired businesses
including Bandcamp, 7digital, MassiveMusic, Big Sync Music and the AI music-metadata company
Musicube.

Its public developer surface is the **Songtradr API** — a JWT-authenticated REST API described by a
live OpenAPI 3.1 document at `https://api.songtradr.com/v3/api-docs` (rendered at
`https://api.songtradr.com/swagger-ui.html`). It returns deep music metadata — musical features,
genre predictions, tags, taggrams, tag strengths, contributors and similarity vectors — and drives
auto-tagging: rightsholders upload audio through a presigned S3 link, Songtradr's models classify
it, and the results become semantically searchable. Rate limited to 120 requests per minute.

- Website: https://www.songtradr.com/
- API reference: https://api.songtradr.com/swagger-ui.html
- OpenAPI: https://api.songtradr.com/v3/api-docs
- GitHub: https://github.com/songtradr
- Support: https://support.songtradr.com/hc/en-us

## Clients

| Language | Package | Version |
|---|---|---|
| Python | [songtradr-api-client-python](https://pypi.org/project/songtradr-api-client-python/) | 3.0.0 |
| JavaScript | [songtradr-api-client](https://www.npmjs.com/package/songtradr-api-client) | 3.0.1 |
| Ruby | [songtradr_api_client_ruby](https://rubygems.org/gems/songtradr_api_client_ruby) | 2.1.0 |

## Notes

No GraphQL, no MCP server, no A2A agent card, no webhooks or event stream, no `/.well-known/`
documents, no status page, no published deprecation policy and no compliance/trust program were
found on the public surface. Errors use the Spring Boot envelope rather than RFC 9457, and there is
no idempotency contract.
