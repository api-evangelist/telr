---
name: Telr direct (remote) card or wallet transaction
description: Process a server-to-server sale/auth with card or Apple/Google/Samsung Pay wallet token, then capture, refund, or void.
api: openapi/telr-openapi.yml
operations: [createRemoteTransaction]
---

# Telr direct (remote) transaction

Full control of the checkout UI by submitting card or wallet data directly.
Requires appropriate PCI scope for raw card data.

## Auth
In-body `store` + `authkey` (see `authentication/telr-authentication.yml`).

## Steps
1. **Sale/auth** — POST `/gateway/remote.json` (`createRemoteTransaction`) with
   `method: transaction`, a `tran` object (`type: sale|auth`, `class:
   ecom|moto|cont`, `amount` string, `currency`), and either a `card`
   (`number`, `expiry.month`, `expiry.year`, `cvv`) or an `applepay` /
   `googlepay` / `samsungpay` wallet token.
2. **Read the result** from `transaction.status` / `transaction.code`. Letter
   `A` = authorised, `H` = held for review, `D` = declined, `E` = error.
3. **Follow-up transactions** — capture, refund, or void by POSTing again with
   `tran.type: capture|refund|void` and `tran.ref` set to the **original
   transaction ref**.

## Rules
- Map declines with `errors/telr-decline-codes.yml` (e.g. code `41` Insufficient
  funds, `47` 3-D Secure rejected). Do not expose raw issuer decline detail to
  the buyer.
- Test with the cards + CVV simulation in `sandbox/telr-sandbox.yml`
  (`tran.test: 1`).
- No idempotency-key header — use a unique `tran.id` (cart id) per attempt.
