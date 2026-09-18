# 08 — Product scope

## Core objects

```
Organization
  ├── Users, Roles, API keys, MCP clients
  ├── Fiscal calendars (BS/AD), branches, warehouses
  ├── Parties (customers, suppliers) + PAN validation
  ├── Items / SKUs / variants / bundles
  ├── Stock lots (optional batch/expiry)
  ├── Channels (web, pos, instagram, whatsapp, phone, import)
  ├── Orders (draft → confirmed → fulfilled / cancelled)
  ├── Invoices (tax invoices, bills, credit notes)
  ├── Payments & payouts
  ├── Journal entries (derived + manual)
  ├── Tax registers (sales book, purchase book, VAT, TDS)
  └── CBMS sync log
```

## Workflow A — Order to cash (heartbeat)

1. Order created from widget, POS, chat agent, or API.
2. Stock reserved on confirm (configurable: reserve on draft vs confirm).
3. Payment intent created (dynamic QR, wallet redirect, COD, bank).
4. Webhook / poll from rail → payment object.
5. Matcher links payment to order (reference, amount, time window, customer).
6. On policy: auto-issue tax invoice or wait for pack.
7. Fulfilment marks qty shipped; stock commits.
8. COD collected later → second payment object → match.
9. Returns create credit note + stock in.

## Workflow B — Month close (CA heartbeat)

1. Unmatched payments list.
2. Draft invoices older than N days.
3. Sales book / purchase book IRD layout.
4. VAT computation 13% with exempt/zero buckets.
5. TDS where the org is withholder.
6. CBMS exceptions (failed sync, gap in serial).
7. Export: Excel, XML/JSON as required, PDF annex-style reports.
8. Optional Tally / CSV dump.

## Workflow C — Agent exception

Human-in-the-loop queue:

- Agent wanted to sell OOS item
- Price override
- Customer PAN missing on invoice above threshold
- Payment amount ≠ order amount
- Abuse / chargeback-like wallet reversal

## Modules by phase

### Phase 0 — skeleton (weeks 1–8)

- Tenancy, auth, BS dates
- Items, parties, warehouses
- Orders + invoice issue + credit note
- Manual payment entry
- Sales register export
- Audit log

### Phase 1 — money and tax (months 2–6)

- Fonepay dynamic QR + webhook
- eSewa + Khalti + ConnectIPS ingest
- Matcher
- CBMS sync (or approved vendor path)
- Multi-branch stock
- CA read portal

### Phase 2 — clients (months 5–10)

- Public REST + webhooks
- MCP server
- Woo plugin
- Headless checkout widget (not a theme shop)
- Instagram/WhatsApp order-taker v1 (structured, not free chat)

### Phase 3 — deepen (months 10–18)

- Purchases / GRN / landed cost light
- Batch/expiry if pharmacy-like beachhead appears
- Loyalty only if it writes to the same customer
- Basic payroll journal import (not full HRMS)
- Agency / multi-entity for CAs

## Reports that must exist before any “AI insights”

- Day book
- Stock on hand by warehouse
- Unmatched payments
- Sales book, purchase book
- VAT payable worksheet
- Invoice serial integrity
- Channel contribution (web vs chat vs POS)
- COD outstanding aging

## Permissions model

- `owner`
- `operator` (orders, POS)
- `fulfilment`
- `accountant` (issue/void via notes, reports, no catalog merchandising)
- `ca_external` (read + comment + export, no issue)
- `developer` (keys)
- `agent` (scoped tools only)

Every MCP session maps to `agent` or a user-as-agent role.
