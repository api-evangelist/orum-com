# Orum

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

Orum is an AI-powered sales calling and performance platform — a parallel dialer, a virtual
salesfloor, a coaching suite, and AI data agents — marketed as "The Calling Performance System for
Sales Teams." It integrates with Salesforce, HubSpot, Outreach, Salesloft, Gong Engage and Apollo.

**Not orum.io.** This profile is **orum.com**. The `all/orum` repository is a different company
entirely — orum.io, a payments-infrastructure provider doing FedNow/RTP/ACH money movement and
bank-account verification. Same name, unrelated businesses.

**No request API as of 2026-08-13.** Orum publishes no OpenAPI, no API reference, no documentation
host, no GraphQL, no SDKs, no CLI, no MCP server, no A2A agent card and no `llms.txt`;
`docs.orum.com`, `developers.orum.com`, `api.orum.com` and `app.orum.com` do not resolve. `apis: []`
in `apis.yml` is deliberate — nothing has been scaffolded or generated for this provider, and every
probe is recorded under `x-evidence`.

**One machine-facing contract: outbound webhooks — and they *are* documented.** The 2026-08-04 pass
recorded webhooks as "sold as an add-on but not publicly documented." That was wrong, and this pass
corrects it. Orum publishes a full webhook reference in its help center
([ART-463-webhooks](https://support.orum.com/en-US/orum/article/ART-463-webhooks), HTTP 200, no
credentials): one event `call-disposition-added`, an `{event, payload, test}` envelope, 13 documented
call properties, HMAC-SHA256 base64 signing in an `x-webhook-signature: t={timestamp},s={sig}` header
over `{timestamp}.{body}`, a return-2xx-before-processing contract with a ~15 second timeout, 8
retries over 30 minutes with exponential backoff and jitter, no historical replay, and three egress
IPs. It is captured in `asyncapi/orum-com-webhooks.yml`. The reference exists; its **discoverability**
is the real defect — the article appears in none of the help center's eight directories, and the only
public path to it is the 2025-04-14 launch blog post, whose link returns a 502.

**Also found this pass:** the GitHub org is [`orumhq`](https://github.com/orumhq) (the earlier probe
of `orumcom` 404'd), holding four public repos — three forks of third-party VoIP tooling and one
hiring-exercise mock server, no SDK and no spec; a first-party Chrome/Edge extension on the Chrome Web
Store (v0.1.1, 2026-02-25); a dated 20-entry product-update feed; Auth0-backed SSO supporting SAML,
OpenID Connect and OAuth 2.0; and a machine-readable Atlassian Statuspage at
`status.orum.com/api/v2/summary.json`. Orum publishes a status page, a trust portal, a
responsible-disclosure policy (`security@orum.com`, no safe harbour), and SOC 2 Type 2 plus ISO
27001/27017/27018/27701 attestations. It serves **no** `/.well-known/` document from any host it
controls — the one `security.txt` that answers 200 is Atlassian's, on the Statuspage subdomain, and is
not credited to Orum.

Source: surfaced by an API Evangelist conversation on 2026-08-04 — https://www.orum.com/
