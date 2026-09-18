# 16 — Roadmap

Horizon: 36 months from a late-2026 start. Dates are quarters, not promises to customers.

Naming: **P0** foundation, **P1** money+tax, **P2** clients, **P3** harden and distribute, **P4** expand the record.

---

## North-star metric by phase

| Phase | Months | North star |
|---|---|---|
| P0 | 0–2 | First design partner issues a real invoice from an order |
| P1 | 2–6 | 80% of digital payments auto- or one-click matched for design partners |
| P2 | 5–10 | 2 external systems post production orders (Woo + 1 other) |
| P3 | 10–18 | 80 paying orgs; 10 CAs logging in monthly |
| P4 | 18–36 | 200+ paying; break-even on base case |

Vanity metrics we will display internally but not steer by: MCP tool call count, chat messages, “AI accuracy.”

---

## P0 — Foundation (weeks 1–8)

### Product

- Org, users, roles
- BS/AD date library with FY boundaries
- Items, variants, tax codes
- Customers / PAN field
- Order draft → confirm → cancel
- Invoice draft → issue (immutable) → PDF
- Credit note
- Manual payment
- Simple on-hand stock (one warehouse)
- Audit log
- Sales register CSV

### Non-product

- Working name decision stay/leave
- Counsel note on e-commerce / billing software duties
- Hire or retain a CA advisor (hours, not full-time if cash tight)
- 8 design-partner conversations; close 4 written

### Exit criteria

A partner can sell 20 SKUs for two weeks, issue invoices, and the sales book ties to invoice totals.

### Explicitly not in P0

Themes, MCP, WhatsApp, CBMS production, multi-branch, payroll.

---

## P1 — Money and tax (months 2–6)

### Product

- Fonepay dynamic QR intents + webhooks + idempotency
- Ingest eSewa and Khalti settlement reports / APIs
- ConnectIPS reference capture
- Payment matcher v1 (exact ref + amount; then fuzzy window)
- Unmatched queue UI
- Second warehouse
- Branch as a dimension
- CBMS *sandbox* or partner-bridge spike
- CA read-only login
- Day book + unmatched + VAT worksheet

### Integrations

- One 3PL *status in* if a partner demands it (Pathao or Dash). Fulfilment state only. We are not a courier OS.

### Compliance

- Invoice numbering scheme reviewed by advisor
- Reprint labeling
- Decision ADR: native CBMS listing vs bridge

### Exit criteria

For two partners, ≥80% of Fonepay payments match without spreadsheet. VAT worksheet survives a CA looking at it for 30 minutes without swearing at us.

### Kill / pivot check (end of month 6)

If partners still retype invoices into Tally because they do not trust our serials, stop new features and fix trust. If we cannot get rail webhooks, the company is a form builder — consider dying.

---

## P2 — Clients (months 5–10, overlaps P1)

### Product

- Public REST API v1 + webhooks
- OpenAPI published
- MCP server with read tools + `create_draft_order`
- WooCommerce plugin (orders + stock read)
- Checkout widget MVP (QR + COD)
- Unified inbox: paste DM → suggested draft order
- Suggest-mode chat on *our* widget only

### Policy

- `issue_invoice` denied to MCP by default
- Agent audit viewer for org owners

### Exit criteria

A Woo shop runs a week of production orders into Bahi with no daily engineer in the loop. A CA asks Claude (or ChatGPT) for unmatched payments via MCP and gets the same list as the UI.

---

## P3 — Harden and sell (months 10–18)

### Product

- CBMS production path live for listed orgs (native or bridge)
- Matcher v2 (split payments, overpay, fee lines)
- Purchases lite (bill + stock in)
- POS-lite
- WhatsApp order-taker for 5 design orgs max
- Report pack CAs actually file from
- SLA-ish: invoice PDF < 2s, webhook retry dashboard

### GTM

- Price page public in NPR
- 10 CA firms onboarded
- Case study: one brand, match-rate + hours saved
- Implementation playbook so founder is not the only implementer

### Team

- Add CS only when ticket load justifies
- Still no generic SDR

### Exit criteria

80 paying organizations (not design-partner comps). Support tickets falling. Burn covered ≥40% by revenue.

### Kill / pivot check (month 18)

If paying < 40 and ARPU < 3,000, the domain may be enterable but *this team* is not winning. Options: shrink to CA-only middleware, sell the matcher to a Tigg/Blanxer, or stop.

---

## P4 — Record expansion (months 18–36)

Only if P3 exit is hit.

- Multi-entity for groups
- Batch/expiry if a vertical pulled us
- Deeper AP / supplier TDS
- Metered API for other SaaS
- Optional Meta catalog truth-source (stock/price) if APIs allow
- Break-even operations: 170–270 paying at NPR 6k or fewer at higher ARPU

Still non-goals: theme store, wallet license, full HRMS, restaurant KDS.

---

## Month-by-month year 1 (planning grid)

| Month | Build | GTM |
|---|---|---|
| 1 | Dates, tenancy, items, order/invoice skeleton | 20 ICP interviews |
| 2 | Issue/credit note, stock, PDF | 8 design partners invited |
| 3 | Manual payments, registers | 4 partners live on skeleton |
| 4 | Fonepay QR spike | Advisor on numbering |
| 5 | Matcher v1, unmatched UI | Weekly CA office hours |
| 6 | Wallet ingest, VAT worksheet | Pivot check |
| 7 | API v1 | Woo pilot |
| 8 | Webhooks, widget | First paid Start/Operate |
| 9 | MCP read tools | Public docs site |
| 10 | MCP draft order + audit | Plugin listed |
| 11 | CBMS path | Implementation fee offered |
| 12 | Harden, POS-lite spike | 25–40 paying target (stretch) |

Year-1 revenue target is *learning plus some cash*, not break-even.

---

## Year 2 themes

Q1: CBMS trust, CA desk packaging  
Q2: Purchases lite, Firm tier  
Q3: Attach economics on matcher  
Q4: Revisit break-even; hire only against coverage

## Year 3 themes

If alive and at coverage: become infrastructure other front doors rent. If not at coverage: stay a vertical ledger for one ICP and ignore “platform.”

---

## Dependency graph (do not violate)

```
dates/tenancy → catalog → orders → invoices
                                      ↓
payments ingest → matcher → VAT worksheet
orders → API → Woo/widget
API → MCP
invoices → CBMS
matcher + invoices → CA portal
inbox/chat → draft orders only after catalog+stock exist
```

Any work that skips left-to-right is a process bug.

---

## Design-partner contract (required)

In writing:

- They file taxes; we are software
- We may use anonymized match-rate in case studies
- They give weekly 30 minutes
- Data export on request within 7 days
- Price holiday ends month 6 unless extended in writing
