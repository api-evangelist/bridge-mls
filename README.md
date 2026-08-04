# Bridge (bridge-mls)

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
