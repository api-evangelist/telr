---
name: Telr repeat-billing agreement management
description: Create, amend, forecast, or cancel a recurring repeat-billing agreement against a stored card.
api: openapi/telr-openapi.yml
operations: [manageAgreement]
---

# Telr repeat-billing agreements

Manage recurring / instalment agreements charged against a stored card.

## Auth
In-body `store` + `authkey` (see `authentication/telr-authentication.yml`).

## Steps
1. **Manage** — POST `/gateway/manageagreement.json` (`manageAgreement`) with
   `method: manage`, `store`, `authkey`, and an `agreement` object (`ref`,
   `type: recurring|instalment|unscheduled`, `amount`, `currency`).
2. **Forecast** upcoming charges with `method: forecast` (bounded date range,
   max 31 days).
3. **Cancel** with `method: cancel` (supports future cancel dates).

## Rules
- Agreement changes emit webhooks (`CHANGE_DATE`, `CHANGE_DETAILS`, `FREEZE`,
  `STORE_TRANSFER`, `CANCEL`) — verify the `tran_check`/`account_check` SHA1
  signature per `asyncapi/telr-webhooks.yml`.
- Reporting endpoints use date-range windows, not cursor pagination
  (`conventions/telr-conventions.yml`); a duplicate-request lock blocks
  concurrent calls for the same store + auth key.
- Errors return the in-body `error{message,note}` envelope
  (`errors/telr-problem-types.yml`).
