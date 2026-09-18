# 06 — ICP and positioning

## Positioning statement

For **Nepali VAT-registered merchants who sell through more than one channel**, Bahi is the **order-to-invoice ledger** that turns website, counter, and chat sales into stock, matched payments, and CBMS-ready bills — so the owner and the CA stop reconstructing the month in Excel.

Unlike Blanxer, we do not exist to make a prettier store.  
Unlike Tigg/Tally, we do not exist to type invoices after the fact.  
Unlike Meta, we do not exist to talk to customers.

## Primary ICP (year 1) — “D2C operator”

Must have **all** of:

- NPR 2–20 million monthly GMV across web + social (not Daraz-only)
- Already paying for ads or a storefront (Blanxer / Woo / custom)
- VAT-registered or crossing computerized billing thresholds within 12 months
- 1–3 people touching orders daily (founder + packer + maybe CA)
- Pain they will pay to remove: unmatched QR, COD leakage, oversell, invoice backlog

Examples: cosmetics, personalized gifts, electronics accessories, apparel brands with their own site, official-brand shops doing drops.

**Why this ICP:** they already feel operational pain, they already pay Blanxer-level prices, they create high document volume, they understand software subscriptions.

## Secondary ICP (year 1.5) — “trading house / multi-branch retailer”

- 2–8 locations
- Wholesale + retail
- Swastik/Tally users whose inventory is a lie by Thursday
- Will pay implementation (NPR 15–40k) and monthly

Do not take this ICP before the D2C invoice engine is boringly reliable.

## Channel ICP — Chartered accountants / accounting firms

Not a user of selling. A user of **closing**.

Job: pull VAT pack, TDS list, unmatched payments, sales/purchase books in IRD shape, without visiting the client’s laptop.

Pricing: per-client seat. Distribution: one CA can bring 8–40 merchants.

Year-1 goal: 10 firms, even if they only watch.

## Explicit non-ICP (see also non-goals)

- Restaurants and cloud kitchens as flagship (POS bloodbath)
- Kirana doing 20 SKUs and NPR 200k/month (Zalient/Tally Express territory)
- INGOs and project accounting
- Banks, cooperatives, hydropower, construction job costing
- Cross-border exporters whose books are USD + LC (later)
- Pure marketplaces who never own inventory

## Buyer vs user

| Role | What they fear | What they touch |
|---|---|---|
| Founder | Oversell, stolen COD, IRD notice | Phone dashboard, chat exceptions |
| Store operator | Slow billing, wrong stock | POS / order inbox |
| Packer | Wrong warehouse | Pick list |
| Accountant / CA | Unauditable invoices, missing PAN | CA portal, MCP, exports |
| Developer / agency | Fragile webhooks | API keys, MCP |

Sell to the founder. Design daily use for the operator. Lock-in through the CA.

## Category name we should use in sales

Do not say ERP. Do not say Shopify-killer. Do not say AI platform.

Say: **“Order to VAT.”**  
Backup: **“Commerce ledger.”**  
Nepali spoken: **“Order aayepachi bill ra stock aafai milne system.”**
