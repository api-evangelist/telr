---
name: Telr hosted payment page checkout
description: Create a Telr hosted payment page order, redirect the customer to pay, then poll the order status.
api: openapi/telr-openapi.yml
operations: [createHostedOrder]
---

# Telr hosted payment page checkout

Use this to take a payment without handling raw card data (no PCI scope).

## Auth
The legacy gateway endpoints authenticate with a numeric `store` id plus an
`authkey`, passed **inside the JSON body** (not an HTTP header). Generate the
auth key per store in Merchant Administration. See
`authentication/telr-authentication.yml`.

## Steps
1. **Create the order** — POST `/gateway/order.json` (`createHostedOrder`) with
   `method: create`, `store`, `authkey`, an `order` object (`cartid`, `amount`
   as a major-unit string e.g. `"9.50"`, `currency` ISO 4217 e.g. `AED`,
   `description`, `trantype: sale`), and `return` URLs (`authorised`, `declined`,
   `cancelled`). Set `order.test: 1` while testing.
2. **Redirect** the customer to the returned `order.url`
   (`https://secure.telr.com/gateway/process.html?o=<ref>`). Keep the returned
   `order.ref`.
3. **Confirm** — POST `/gateway/order.json` again with `method: check` and the
   saved `ref` to read the authoritative `order.status`. Never trust only the
   browser return URL.

## Rules
- Idempotency: there is no idempotency-key header — use a **unique `cartid`** per
  order to avoid duplicates (`conventions/telr-conventions.yml`).
- Errors surface as an in-body `error{message,note}` plus an authorisation
  status letter + code (`errors/telr-decline-codes.yml`).
- In test mode, simulate outcomes with the CVV rules in
  `sandbox/telr-sandbox.yml` (e.g. CVV `041` => Insufficient funds).
