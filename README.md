# Bridge (bridge-mls)

Bridge (Bridge Interactive / Bridge Data Output) is a Zillow Group company that runs the Bridge Platform — a RESO Platinum-certified MLS data distribution service used by Multiple Listing Services and brokerages across the US and Canada. The Bridge RESO Web API exposes normalized listing data (Property, Member, Office, OpenHouse, Media, Room, UnitType) via OData 4.0 at api.bridgedataoutput.com/api/v2/OData, with a parallel native Bridge Web API serving the same resources as flat JSON. A Webhooks API delivers real-time listing change events with PKI-signed payloads. Bridge also distributes Zillow Group Data — parcels, assessments, and ZHVI/ZORI economic feeds — through the same API surface.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bridge-mls/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bridge-mls/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Real Estate
- MLS
- RESO
- Listings
- Property Data
- Brokers
- Data Distribution

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Bridge RESO Web API

RESO Platinum-certified Web API providing OData 4.0-compliant access to MLS listing data normalized to the RESO Data Dictionary. Resources include Property, Member, Office, OpenHouse, Media, Room, UnitType, and other RESO-defined entities. Supports $filter, $select, $expand, $orderby, $top (page size), and $count OData query options, plus Bridge extensions like the unselect parameter and the maxpagesize header (default 10, max 200). Data is refreshed every 10 minutes or less per MLS feed. Bridge is preparing datasets for RESO Data Dictionary 2.0 certification.

- **Human URL:** [https://bridgedataoutput.com/docs/platform/API/reso-web-api](https://bridgedataoutput.com/docs/platform/API/reso-web-api)
- **Base URL:** `https://api.bridgedataoutput.com/api/v2/OData`

#### Tags

- Real Estate
- MLS
- RESO
- OData
- Listings

#### Properties

- [Documentation](https://bridgedataoutput.com/docs/platform/API/reso-web-api)
- [Documentation](https://bridgedataoutput.com/docs/explorer/reso-web-api)
- [Documentation](https://bridgedataoutput.com/docs/explorer/mls-data)
- [OpenAPI](openapi/bridge-reso-web-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/bridge-reso-web-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-reso-web-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/bridge-property-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/bridge-member-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/bridge-mls-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Bridge Web API

Bridge's native (non-OData) RESTful Web API serving the same normalized MLS resources (Properties, Members, Offices, OpenHouses, Rooms, UnitTypes, and off-market data where licensed) as flat JSON. Provides a simpler request/response shape than the OData endpoint while preserving RESO Data Dictionary field naming. Media is returned as an object on the Property record and is hosted on a CDN. Requires a server token or access token issued by Bridge per dataset.

- **Human URL:** [https://bridgedataoutput.com/docs/platform/API/bridge](https://bridgedataoutput.com/docs/platform/API/bridge)
- **Base URL:** `https://api.bridgedataoutput.com/api/v2`

#### Tags

- Real Estate
- MLS
- Listings
- JSON

#### Properties

- [Documentation](https://bridgedataoutput.com/docs/platform/API/bridge)
- [OpenAPI](openapi/bridge-web-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/bridge-web-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-web-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bridge Webhooks API

Manage webhook endpoints that receive real-time POST events from Bridge for listing create/update/delete and other dataset changes, eliminating the need to poll the Web API. Endpoints require an HTTPS URL with a valid X.509 certificate; Bridge issues a PKI public key (PEM) for payload signature verification. Events are delivered as application/json; endpoints must respond 200 quickly. Failed deliveries are retried with exponential backoff for up to two days. Webhooks begin in a disabled state for testing before activation.

- **Human URL:** [https://bridgedataoutput.com/docs/platform/API/webhooks](https://bridgedataoutput.com/docs/platform/API/webhooks)
- **Base URL:** `https://api.bridgedataoutput.com/api/v2`

#### Tags

- Real Estate
- Webhooks
- Events
- Real-time

#### Properties

- [Documentation](https://bridgedataoutput.com/docs/platform/API/webhooks)
- [Postman Collection](collections/bridge-reso-web-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-reso-web-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/bridge-web-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-web-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/bridge-webhooks-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-webhooks-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Zillow Group Data (ZG Data) API

Zillow Group Data feeds delivered through Bridge — parcels, assessments, transactions, and Zillow Group Econ Data (ZHVI, ZORI, market metrics) — accessible via the same OData/RESO Web API surface as MLS data. Licensed separately from MLS feeds.

- **Human URL:** [https://bridgedataoutput.com/zgdata](https://bridgedataoutput.com/zgdata)
- **Base URL:** `https://api.bridgedataoutput.com/api/v2/OData`

#### Tags

- Real Estate
- Public Records
- Property Data
- Parcels

#### Properties

- [Documentation](https://bridgedataoutput.com/zgdata)
- [Documentation](https://bridgedataoutput.com/docs/explorer/zillow-group-econ-data)
- [Postman Collection](collections/bridge-reso-web-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-reso-web-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/bridge-web-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-web-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/bridge-webhooks-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bridge-webhooks-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.bridgeinteractive.com)
- [Portal](https://bridgedataoutput.com)
- [Documentation](https://bridgedataoutput.com/docs/platform/)
- [Getting Started](https://bridgedataoutput.com/docs/platform/Introduction/Signing-up-with-Bridge-API)
- [Sandbox](https://bridgedataoutput.com/docs/explorer/reso-web-api)
- [Sandbox](https://bridgedataoutput.com/docs/explorer/mls-data)
- [Sign Up](https://bridgedataoutput.com/login)
- [Documentation](https://www.bridgeinteractive.com/developers/bridge-api/)
- [Documentation](https://www.bridgeinteractive.com/developers/data-access/)
- [Documentation](https://www.bridgeinteractive.com/developers/zillow-group-data/)
- [Documentation](https://www.bridgeinteractive.com/resources/api-documentation/)
- [Changelog](https://updates.bridgedataoutput.com/)
- [Changelog](https://www.bridgeinteractive.com/bridge-platform-updates/)
- [Support](https://bridgedataoutput.com/help)
- [Support](mailto:support@bridgeinteractive.com)
- [About Us](https://www.bridgeinteractive.com/about/)
- [Contact Form](https://www.bridgeinteractive.com/contact/)
- [Privacy Policy](https://www.bridgeinteractive.com/privacy-policy/)
- [Terms of Service](https://www.bridgeinteractive.com/terms-of-use/)
- [LinkedIn](https://www.linkedin.com/company/bridge-interact)
- [Documentation](https://www.reso.org/)
- [Documentation](https://www.reso.org/data-dictionary/)
- [Documentation](https://www.reso.org/reso-web-api/)
- [Documentation](https://www.reso.org/certification/)
- [Plans](plans/bridge-mls-plans-pricing.yml)
- [Rate Limits](rate-limits/bridge-mls-rate-limits.yml)
- [Fin Ops](finops/bridge-mls-finops.yml)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
