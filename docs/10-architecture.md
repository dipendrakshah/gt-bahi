# 10 — Architecture (target shape)

This is a *target*, not an implementation mandate. Change via ADR.

## Design goals

- One tenant’s books cannot leak into another’s, including via MCP
- Issued invoices append-only
- Rails are adapters; core does not speak only Fonepay
- Agents are OAuth clients
- Can reconstruct any invoice from events

## Logical services (may be one process)

| Component | Responsibility |
|---|---|
| Identity | Users, API keys, OAuth apps, MCP tokens |
| Catalog | Items, taxes, warehouses |
| Commerce | Orders, reservations, fulfilment |
| Fiscal | Invoice numbering, notes, registers |
| Treasury | Payments, matcher, settlement batches |
| Tax gateway | CBMS, IRD-shaped exports |
| Journal | Double-entry projections |
| Channel adapters | Woo, widget, Meta webhooks, POS |
| Agent gateway | MCP + tool policy + audit |
| Notify | SMS / email / WhatsApp templates |

## Data

- Primary store: relational (Postgres or equivalent)
- Document immutability: invoice tables are insert + status machine, no UPDATE of fiscal fields
- Event log: `audit_events` at minimum; full event sourcing optional later
- Files: invoice PDFs, KYC, CBMS payloads — object storage
- Search: start with SQL; add search engine only if CA query latency hurts

## Integration style

```
[Instagram] [WhatsApp] [Woo] [Widget] [POS]
                 \       |       /
                  Channel adapters
                         |
                    Commerce core
                    /    |     \
              Treasury  Fiscal  Stock
                    \    |     /
                     Journal
                         |
                 Tax gateway (CBMS)
                         |
              API / MCP / CA portal
```

## Reliability

- Payment webhooks: idempotent by rail event id
- CBMS: retry queue with dead-letter and operator UI
- Matcher: never auto-match below confidence threshold; human queue
- Multi-warehouse: reservations expire

## Security

- Tenant id on every row
- Scoped tokens (`orders:write`, `invoices:issue`, `stock:read`, `payments:match`)
- Agent tools default deny on `invoices:issue` until org policy enables it
- Full prompt/tool audit for MCP (what was asked, which tool, which ids)
- Secrets for rails in a vault, not in env on laptops

## Hosting

Nepal data residency is a sales feature. Prefer a region story CAs will accept. Decision deferred (`19-open-questions.md`) but do not casually put fiscal data only on a random US hobby plan.

## What we will not do in v1

- Separate microservice per table
- Kafka
- Multi-region active-active
