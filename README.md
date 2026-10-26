# Telr (telr)

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

Telr is a Dubai-headquartered online payment gateway operating across the MENA region (UAE, Saudi Arabia, Bahrain, Jordan), supporting 120+ currencies and 30 languages. Its HTTPS/JSON gateway exposes a Hosted Payment Page, a Remote (direct) card and wallet API, repeat-billing agreements, mobile SDKs, and a newer REST Payments API - all PCI DSS v4.0 Level 1 and NESA certified.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/telr/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/telr/refs/heads/main/apis.yml)

## Tags

- Payments
- Payment Gateway
- FinTech
- MENA
- UAE

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### Telr Hosted Payment Page API

Redirect-based hosted checkout. POST order.json with method=create to receive a process.html payment URL branded with your logo/CSS, then method=check to poll order status. Store id + authentication key are passed in the JSON body; no PCI scope required.

- **Human URL:** [https://docs.telr.com/reference/how-the-hosted-payment-page-works](https://docs.telr.com/reference/how-the-hosted-payment-page-works)
- **Base URL:** `https://secure.telr.com/gateway`

#### Tags

- Payments
- Hosted Checkout
- Redirect

#### Properties

- [Documentation](https://docs.telr.com/reference/how-the-hosted-payment-page-works)
- [API Reference](https://docs.telr.com/reference/createorder)
- [OpenAPI](openapi/telr-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/telr.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Telr Remote API

Server-to-server direct API (remote.json) giving full control of the checkout UI by capturing card details on your own site. Supports sale/auth/capture/refund/void transactions with ecom, moto, and cont classes; requires appropriate PCI scope for raw card data.

- **Human URL:** [https://docs.telr.com/reference/post_gateway-remote-json](https://docs.telr.com/reference/post_gateway-remote-json)
- **Base URL:** `https://secure.telr.com/gateway`

#### Tags

- Payments
- Direct
- Server to Server

#### Properties

- [Documentation](https://telr.com/support/knowledge-base/remote-api-integration-guide/)
- [API Reference](https://docs.telr.com/reference/post_gateway-remote-json)
- [OpenAPI](openapi/telr-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/telr.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Telr Digital Wallets API

Wallet transactions (Apple Pay, Google Pay, Samsung Pay) submitted through remote.json with an encrypted wallet token or decrypted network token, or enabled on the hosted payment page. Same store + authkey body authentication.

- **Human URL:** [https://docs.telr.com/reference/post_remote_applepay](https://docs.telr.com/reference/post_remote_applepay)
- **Base URL:** `https://secure.telr.com/gateway`

#### Tags

- Apple Pay
- Google Pay
- Samsung Pay

#### Properties

- [Documentation](https://docs.telr.com/reference/payment-pages-v2-applepay-integration)
- [API Reference](https://docs.telr.com/reference/post_remote_applepay)
- [OpenAPI](openapi/telr-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/telr.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Telr Repeat Billing API

Create, amend, forecast, and cancel recurring repeat-billing agreements against stored cards (manageagreement.json), supporting card change, future cancel dates, and subscription/instalment schedules.

- **Human URL:** [https://docs.telr.com/reference/repeat-billing](https://docs.telr.com/reference/repeat-billing)
- **Base URL:** `https://secure.telr.com/gateway`

#### Tags

- Recurring
- Subscriptions
- Agreements

#### Properties

- [Documentation](https://docs.telr.com/reference/repeat-billing)
- [API Reference](https://docs.telr.com/reference/post_gateway-manageagreement-json)
- [OpenAPI](openapi/telr-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/telr.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Telr Payments REST API

Newer REST order API (/api/v1/orders) authenticated with HTTP Basic auth (store id : API key). Create orders with SALE/AUTH/VERIFY transaction types, up to two webhooks, and hypermedia _links; retrieve status by order ref.

- **Human URL:** [https://docs.telr.com/reference/createorder](https://docs.telr.com/reference/createorder)
- **Base URL:** `https://secure.telr.com/api/v1`

#### Tags

- Payments
- REST
- Orders

#### Properties

- [API Reference](https://docs.telr.com/reference/createorder)
- [API Reference](https://docs.telr.com/reference/getorder)
- [OpenAPI](openapi/telr-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/telr.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Telr Mobile API and SDKs

Mobile integration that drives the Hosted Payment Page inside a web view, offloading PCI-DSS scope and 3-D Secure handling. Native SDKs are published for Android, iOS, Flutter, and React Native.

- **Human URL:** [https://docs.telr.com/reference/mobile-api-integration-guide](https://docs.telr.com/reference/mobile-api-integration-guide)
- **Base URL:** `https://secure.telr.com/gateway`

#### Tags

- Mobile
- Web View
- SDK

#### Properties

- [Documentation](https://docs.telr.com/reference/mobile-api-integration-guide)
- [Documentation](https://docs.telr.com/reference/introduction-to-mobile-sdks)
- [OpenAPI](openapi/telr-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Telr Accounts and Split Payments API

Marketplace / split-payment Service API for sub-merchant onboarding, multi-split payments, debit/credit of sub-merchant accounts, payouts, and transaction reconciliation. Authenticated with HTTP Basic auth (merchant id : API key).

- **Human URL:** [https://docs.telr.com/reference/split-payment](https://docs.telr.com/reference/split-payment)
- **Base URL:** `https://secure.telr.com/api/v1`

#### Tags

- Marketplace
- Split Payments
- Payouts

#### Properties

- [Documentation](https://docs.telr.com/reference/split-payment)
- [API Reference](https://docs.telr.com/reference/authentication)

### Telr QuickLink and E-Invoicing API

Remote creation of QuickLink payment links and e-invoices with extra data fields, for merchants who collect payment without a full checkout integration.

- **Human URL:** [https://docs.telr.com/reference/introduction-to-e-invoicing](https://docs.telr.com/reference/introduction-to-e-invoicing)
- **Base URL:** `https://secure.telr.com/gateway`

#### Tags

- Invoicing
- Payment Links
- E-Invoice

#### Properties

- [Documentation](https://docs.telr.com/reference/introduction-to-e-invoicing)
- [API Reference](https://docs.telr.com/reference/remote-creation-of-invoices)

### Telr Click to Pay (C2P) API

EMV Secure Remote Commerce (Click to Pay) checkout, available as a seamless integration or through the remote JSON API for tokenized card-on-file payments.

- **Human URL:** [https://docs.telr.com/reference/introduction-c2p](https://docs.telr.com/reference/introduction-c2p)
- **Base URL:** `https://secure.telr.com/gateway`

#### Tags

- Click to Pay
- Tokenization
- EMV SRC

#### Properties

- [Documentation](https://docs.telr.com/reference/introduction-c2p)
- [API Reference](https://docs.telr.com/reference/c2p-remote)

## Common Properties

- [Website](https://telr.com/)
- [Documentation](https://docs.telr.com/)
- [LinkedIn](https://www.linkedin.com/company/telr)
- [Plans](plans/telr-plans-pricing.yml)
- [Rate Limits](rate-limits/telr-rate-limits.yml)
- [Fin Ops](finops/telr-finops.yml)
- [Blog](https://telr.com/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
