# Bolt (bolt-eu)

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

### Bolt Fleet API

Partner-gated fleet integration for companies operating driver fleets on the Bolt ride-hailing platform. Fleet owners generate API credentials (Client ID and Secret) under Settings > API in the Bolt Fleet Portal, but Bolt publishes no public endpoint documentation - no endpoints are modeled here.

- **Human URL:** [https://fleets.bolt.eu/](https://fleets.bolt.eu/)

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
