# 02 — Problem and thesis

## The job that is failing

A Nepali merchant who sells on Instagram, a website, and sometimes a counter lives in five books:

1. Messenger / WhatsApp / TikTok inbox — the real order book
2. A Blanxer / Woo / custom site — some of the orders
3. eSewa + Fonepay + Khalti + cash — the money
4. A Pathao / Dash spreadsheet — the parcels
5. Tally or a CA’s Excel — the legal truth, reconstructed weeks later

None of these systems agrees. Oversell happens. COD is marked paid by hope. VAT bills are typed from screenshots. Shrawan close is archaeology.

That is the problem. Not “Nepal needs Shopify.” Not “Nepal needs ChatGPT.”

## Why global tools do not close it

- **Shopify** has no native Fonepay/eSewa, bills in USD, no IRD invoice, no BS dates.
- **QuickBooks** has no Nepal VAT register, no CBMS, no BS fiscal year, no Nepal payroll.
- **Stripe** is for export SaaS and cards. Domestic GMV is wallets and QR.
- **HubSpot** does not know that the customer paid NPR 2,450 via Fonepay reference `FP-…` against invoice `081/82-00412`.
- **Meta Business Agent** can reply in Nepali. It cannot legally issue your VAT bill or decrement batch stock.

## Why local tools do not close it either

- **Blanxer** owns ads → checkout → courier for D2C. Books are a Tigg link. Reconciliation is still a person.
- **Tigg / OneFlow / Lekhapal / BUSY** own VAT paper. Orders arrive as typed invoices, not as living sales documents from chat.
- **Tally** owns the accountant’s muscle memory. It is not an operational system for 200 daily TikTok orders.
- **Daraz** owns demand and the customer file. The merchant is a vendor.
- **Restaurant POS pack** owns KOT. Wrong ICP for a general ledger company.

## Thesis

**Bahi is the system of record for operational commerce in Nepal.**

A sale is one object. It has:

- channel (web, POS, Instagram, WhatsApp, phone)
- line items with SKU and warehouse
- tax treatment (VAT / exempt / TDS where relevant)
- payment intents and settlements (QR, wallet, bank, COD)
- fulfilment state
- an immutable fiscal invoice once issued
- a CBMS sync state

Everything else — storefront widget, chat agent, CA portal, Claude via MCP — is a *client* of that object.

## Why now (2026)

1. **QR and wallets are default.** The payment data exists. It is just not posted.
2. **IRD computerized billing is widening.** Thresholds already pull hotels/restaurants and larger VAT payers onto CBMS. The state has even floated a free government e-billing client — which makes *pretty billing UI* a worse business and *operational capture of source documents* a better one.
3. **Front doors multiplied.** Blanxer et al. create more order streams that still dump into Tally.
4. **Agents arrived.** MCP is a standard. Meta ships a business agent. Shopify is turning stores into agent-readable catalogs abroad. Nepal merchants will expect “ask the books” within two years. Someone has to be the books.
5. **IT export talent exists in Kathmandu** while domestic product companies remain thin. The constraint is ICP and compliance, not raw engineering.

## Anti-thesis (so we do not lie to ourselves)

If Bahi is “a modern ERP with AI,” it will lose to Tally + a junior accountant.

If Bahi is “a storefront with AI chat,” it will lose to Blanxer + Meta.

If Bahi is “MCP for Nepal accounting,” it will lose to whoever already has the data (Tigg adding an MCP header, or a CA Excel export).

The only defensible sentence:

> We are the record other systems are allowed to trust.

## Success definition (year 3)

Not GMV processed. Not “AI messages sent.”

- 200+ organizations where **the invoice that went to IRD was born in Bahi from an order**, not retyped
- At least 30 CA firms logging in weekly
- Two non-Bahi front doors (e.g. Blanxer or Woo plugin, plus chat) posting production orders
- Gross margin high enough that NPR 6k blended ARPU supports a 6–8 person team
- A merchant can ask an MCP client: “What is unsold of SKU X in Pokhara, and which Fonepay payments from yesterday are unmatched?” and get an answer from live books
