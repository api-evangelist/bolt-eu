# Bolt (bolt-eu)

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

Bolt (bolt.eu) is the Estonian mobility super-app operating ride-hailing, ride booking, scooter and e-bike rentals, car-sharing, and food and grocery delivery across 50+ countries in Europe and Africa. This is **not** Bolt the US checkout/payments company (bolt.com).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bolt-eu/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bolt-eu/refs/heads/main/apis.yml)

## Access Model - Read This First

If you came here looking for a **ride-booking API**: Bolt does not offer one. Bolt's own support documentation states, in answer to rider API requests, *"Unfortunately, we don't offer any public or private APIs at the moment."* Business ride booking happens through the [Ride Booker](https://bolt.eu/en/business/ride-booker/) web tool and private travel-platform partnerships (for example, corporate travel platforms that have integrated Bolt Business directly) - not through a public API surface.

What Bolt **does** document, at [developer.bolt.eu](https://developer.bolt.eu/), is the delivery side of the platform:

- **Bolt Food API** - restaurant POS integration (menus, orders, dine-in, availability)
- **Bolt Stores API** - grocery/retail warehouse and PIM integration (products, prices, stock, categories)
- **Bolt Delivery API** - the combined restaurant + grocery provider surface

All three are **partner-gated**: every request is HMAC-SHA256 signed with an integrator ID and secret that Bolt issues when a partner test account is created, and Bolt Support must enable access. The endpoint inventories in `openapi/` are taken verbatim from Bolt's official Redocly specs; request/response schemas are summarized rather than reproduced in full (marked `x-schemas-summarized: true`).

A **Fleet API** also exists for companies operating driver fleets - credentials (Client ID and Secret) are generated under Settings > API in the [Fleet Portal](https://fleets.bolt.eu/) - but its endpoints are not publicly documented, so no endpoints are modeled for it here.

## Tags

- Ride Booking
- Ride Hailing
- Mobility
- Transportation
- Food Delivery
- Micromobility
- Delivery
- Super App

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Bolt Food API

Partner-gated API for restaurants integrating point-of-sale systems with the Bolt Food delivery application - push and manage menus, accept, reject, and fulfill orders, handle dine-in orders created by waiters, and control store availability. Bolt calls partner-hosted webhooks for order, courier, and deduction events.

- **Human URL:** [https://developer.bolt.eu/food/main/](https://developer.bolt.eu/food/main/)
- **Base URL:** `https://node.bolt.eu/delivery-provider-pos`

#### Properties

- [Documentation](https://developer.bolt.eu/food/main/)
- [OpenAPI](openapi/bolt-eu-food-openapi.yml)
- [Postman Collection](collections/bolt-eu.postman_collection.json) - Bolt's official collection, downloaded from the developer portal

### Bolt Stores API

Partner-gated API for grocery and retail stores integrating warehouses and PIM systems with Bolt Food / Bolt Market - import products, prices, and discount price lists, manage category trees, layouts, options, fees, timetables, and menu publishing, update stock, and fulfill orders picked by item. SFTP-based catalog upload is also offered as a simplified path.

- **Human URL:** [https://developer.bolt.eu/stores/main/](https://developer.bolt.eu/stores/main/)
- **Base URL:** `https://node.bolt.eu/delivery-provider-pos`

#### Properties

- [Documentation](https://developer.bolt.eu/stores/main/)
- [OpenAPI](openapi/bolt-eu-stores-openapi.yml)
- [Postman Collection](collections/bolt-eu.postman_collection.json)

### Bolt Delivery API

Combined delivery-provider surface covering both the restaurant (Bolt Food) and grocery (Bolt Market) sides of the platform - menu integration, order acceptance and fulfillment, dine-in orders, provider scheduling, warehouse stock, and the full PIM suite, with outbound webhooks for order and courier lifecycle events.

- **Human URL:** [https://developer.bolt.eu/delivery/main/](https://developer.bolt.eu/delivery/main/)
- **Base URL:** `https://node.bolt.eu/delivery-provider-pos`

#### Properties

- [Documentation](https://developer.bolt.eu/delivery/main/)
- [OpenAPI](openapi/bolt-eu-delivery-openapi.yml)
- [Postman Collection](collections/bolt-eu.postman_collection.json)


#### Properties

- [Portal](https://fleets.bolt.eu/)
- [Documentation](https://bolt.eu/en/support/articles/360012344613/)

## Common Properties

- [GitHub Organization](https://github.com/bolteu)
- [LinkedIn](https://www.linkedin.com/company/bolt-eu)
- [Website](https://bolt.eu)
- [Documentation](https://developer.bolt.eu/)
- [Plans](plans/bolt-eu-plans-pricing.yml)
- [Blog](https://bolt.eu/en/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
