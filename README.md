# Telr (telr)

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
