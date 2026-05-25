# Bridge (bridge-mls)

Bridge (Bridge Interactive / Bridge Data Output) is a Zillow Group company that operates the Bridge Platform — a RESO Platinum-certified MLS data distribution service used by Multiple Listing Services and brokerages across the US and Canada. The Bridge RESO Web API exposes normalized listing data (Property, Member, Office, OpenHouse, Media, Room, UnitType) via OData 4.0 at `api.bridgedataoutput.com/api/v2/OData`, with a parallel native Bridge Web API serving the same resources as flat JSON. A Webhooks API delivers real-time listing change events with PKI-signed payloads. Bridge also distributes Zillow Group Data — parcels, assessments, and ZHVI/ZORI economic feeds — through the same API surface.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/bridge-mls/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - Real Estate, MLS, RESO, Listings, Property Data, Brokers, Data Distribution

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Bridge RESO Web API

RESO Platinum-certified Web API providing OData 4.0-compliant access to MLS listing data normalized to the RESO Data Dictionary. Resources include Property, Member, Office, OpenHouse, Media, Room, UnitType. Supports `$filter`, `$select`, `$expand`, `$orderby`, `$top` (page size), and `$count` plus Bridge extensions (`unselect`, `maxpagesize`). Data refreshed every 10 minutes or less per MLS.

**Base URL:** `https://api.bridgedataoutput.com/api/v2/OData`  •  `https://api.bridgedataoutput.com/api/v3/OData`

- [Documentation](https://bridgedataoutput.com/docs/platform/API/reso-web-api)
- [Explorer](https://bridgedataoutput.com/docs/explorer/reso-web-api)
- [OpenAPI](openapi/bridge-reso-web-api-openapi.yml)
- [JSON Schema — Property](json-schema/bridge-property-schema.json)
- [JSON Schema — Member](json-schema/bridge-member-schema.json)
- [JSON-LD](json-ld/bridge-mls-context.jsonld)
- [Naftiko Capability — Property](capabilities/reso-web-api-property.yaml)
- [Naftiko Capability — Member](capabilities/reso-web-api-member.yaml)
- [Naftiko Capability — Office](capabilities/reso-web-api-office.yaml)
- [Naftiko Capability — OpenHouse](capabilities/reso-web-api-openhouse.yaml)
- [Naftiko Capability — Media](capabilities/reso-web-api-media.yaml)
- [Naftiko Capability — Metadata](capabilities/reso-web-api-metadata.yaml)

### Bridge Web API

Native (non-OData) RESTful Web API serving the same RESO-normalized resources as flat JSON. Simpler request/response shape than OData while preserving RESO Data Dictionary field naming.

**Base URL:** `https://api.bridgedataoutput.com/api/v2`

- [Documentation](https://bridgedataoutput.com/docs/platform/API/bridge)
- [OpenAPI](openapi/bridge-web-api-openapi.yml)
- [Naftiko Capability — Listings](capabilities/bridge-web-api-listings.yaml)

### Bridge Webhooks API

Manage webhook endpoints that receive real-time POST events for listing changes. Endpoints require an HTTPS URL with a valid X.509 certificate; Bridge issues a PEM PKI public key for payload signature verification. Failed deliveries retry with exponential backoff for up to two days.

- [OpenAPI](openapi/bridge-webhooks-api-openapi.yml)
- [Naftiko Capability — Webhooks](capabilities/webhooks-endpoints.yaml)

### Zillow Group Data (ZG Data) API

Parcels, assessments, transactions, and Zillow Group Econ Data (ZHVI, ZORI, market metrics) delivered through the same OData/RESO Web API surface as MLS data. Licensed separately.

- [Documentation](https://bridgedataoutput.com/zgdata)
- [Documentation — ZG Econ Data](https://bridgedataoutput.com/docs/explorer/zillow-group-econ-data)
- [Naftiko Capability — Parcels](capabilities/zg-data-parcels.yaml)

## Authentication

Per-dataset access token issued by Bridge. Pass as `?access_token={token}` query parameter (RESO Web API and Bridge Web API) or as `Authorization: Bearer {token}`. HTTPS is required.

## Plans, Rate Limits, FinOps

- [Plans & Pricing](plans/bridge-mls-plans-pricing.yml) — Test dataset (free) and MLS-licensed dataset (contact)
- [Rate Limits](rate-limits/bridge-mls-rate-limits.yml) — Page size default 10, max 200; `$expand` default cap 10
- [FinOps](finops/bridge-mls-finops.yml) — Per-dataset license model; no per-call metering

## Examples

- [List Properties](examples/bridge-list-properties-example.json)

## Common Resources

- [Bridge Platform Documentation](https://bridgedataoutput.com/docs/platform/)
- [Sign Up with Bridge API](https://bridgedataoutput.com/docs/platform/Introduction/Signing-up-with-Bridge-API)
- [Bridge Data Output Login](https://bridgedataoutput.com/login)
- [Platform Updates / Changelog](https://updates.bridgedataoutput.com/)
- [Bridge Interactive — About](https://www.bridgeinteractive.com/about/)
- [RESO Data Dictionary](https://www.reso.org/data-dictionary/)
- [RESO Web API Specification](https://www.reso.org/reso-web-api/)
- Support: support@bridgeinteractive.com

## Maintainers

- Kin Lane — [apievangelist.com](https://apievangelist.com) — info@apievangelist.com
