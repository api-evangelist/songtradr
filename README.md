# Songtradr

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
