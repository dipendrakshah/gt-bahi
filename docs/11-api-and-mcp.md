# 11 — API and MCP

API and MCP are the same permissioned surface. MCP is not a backdoor.

## Public HTTP API (v1 sketch)

Base: `https://api.bahi.dev/v1` (domain TBD)

Auth: `Authorization: Bearer <token>`

Idempotency: `Idempotency-Key` on creates.

### Resources

```
GET    /org
GET    /items
POST   /items
GET    /items/{id}
GET    /stock?item_id&warehouse_id
POST   /stock/adjustments          # reason required

GET    /parties
POST   /parties                    # PAN optional but validated if present

POST   /orders
GET    /orders/{id}
POST   /orders/{id}/confirm
POST   /orders/{id}/cancel
POST   /orders/{id}/fulfil

POST   /invoices                   # usually derived from order
GET    /invoices/{id}
POST   /invoices/{id}/issue
POST   /credit-notes

GET    /payments
POST   /payments                   # manual
POST   /payments/{id}/match
POST   /qr-intents                 # Fonepay dynamic QR

GET    /registers/sales
GET    /registers/purchase
GET    /reports/vat-summary?from&to&calendar=bs

GET    /webhooks
POST   /webhooks
```

Webhooks out: `order.confirmed`, `payment.received`, `payment.matched`, `invoice.issued`, `cbms.synced`, `cbms.failed`, `stock.low`.

Errors: RFC7807-style problem+json. Never 200 with a silent fiscal failure.

## MCP server

Transport: streamable HTTP or stdio for local CA tools. Production default is remote MCP with OAuth.

### Tool list (v1)

| Tool | Side effect | Default agent allow |
|---|---|---|
| `get_org_context` | no | yes |
| `search_items` | no | yes |
| `get_stock` | no | yes |
| `get_order` | no | yes |
| `list_unmatched_payments` | no | accountant/agent |
| `create_draft_order` | yes | yes if policy |
| `confirm_order` | yes | optional |
| `create_qr_intent` | yes | optional |
| `match_payment` | yes | accountant |
| `issue_invoice` | yes | **deny by default** |
| `create_credit_note` | yes | deny by default |
| `vat_summary` | no | accountant |
| `sales_book` | no | accountant |

Every tool call writes `agent_audit(tool, args, actor, result_ids)`.

### Example agent flows we *do* support

- “Is the blue hoodie in M available in Pokhara?”
- “Create a draft order for @customer from this DM, COD, size L.”
- “Which Fonepay hits from yesterday are unmatched?”
- “VAT payable Shrawan 2083.”

### Flows we do *not* support in v1

- “Refund everyone who complained.”
- “Change all prices 10%.”
- “File VAT to IRD.”
- Unattended invoice issue from a public Instagram comment thread.

## Developer packaging

- OpenAPI spec in `/openapi/v1.yaml` (to be added with code)
- Official MCP manifest
- WooCommerce plugin
- Thin JS widget: `bahi.js` mountable on any site
- Zapier/Make only after the API is stable — do not let no-code become the contract

## Versioning

Breaking fiscal field changes require a new major. Additive tools are minor. Deprecate with dates CAs can see.
