# 01 — Original scenario

This file is the source of truth for *how the idea appeared*. Later docs interpret it. If product strategy drifts, come back here and check whether the drift is intentional.

---

## 1. Prompt 1 — Americas business software map

**Asked (paraphrase of the user’s first question):**

> What are the best business solutions in the Americas IT world? For example Shopify has a domain, QuickBooks has some value. What else exists, and what are they solving for?

**Intent inferred:** not a shopping list of logos. A map of *systems of record* — which vendor owns which workflow, and why that ownership is valuable.

**Answer shape that followed:**

The American stack is layer cake:

| Layer | Representative owners | Job |
|---|---|---|
| Store / commerce OS | Shopify, WooCommerce, BigCommerce | Own the catalog, checkout, and increasingly POS |
| Money movement | Stripe, Square, Shopify Payments, PayPal | Accept cards, ACH, wallets; take rate |
| Books | QuickBooks, Xero, NetSuite, Sage Intacct | Invoices, bank feeds, accountant acceptance |
| CRM / growth | Salesforce, HubSpot, Klaviyo | Who the customer is, how you sell again |
| People OS | Rippling, Gusto, ADP, Workday | Hire, pay, benefits, devices |
| Workspace | Microsoft 365, Google Workspace, Slack, Zoom | Talk, write, meet |
| Industry OS | Toast, ServiceTitan, Procore, Clio, Veeva | Workflow so specific that generic CRM fails |

**Structural lesson taken into later prompts:**

American winners attach *payments* to a workflow they already own. Shopify’s store is the hook; Shopify Payments is the business. Toast’s POS is the hook; restaurant card processing is the business. QuickBooks is valuable because US CPAs standardize on it, not because the UI is beloved.

---

## 2. Prompt 2 — Nepal corresponding layers

**Asked:**

> Now analyze how the Nepali market has corresponding layers addressed, and the maturity of homegrown solutions.

**Answer shape that followed:**

Nepal is an *inversion* of the American sequence.

- America: workflow software first, payments attach second.
- Nepal: **wallets and QR rails first**, IRD e-billing second, merchant OS still catching up.

Layer scores used in that analysis (homegrown product quality, not “does software exist”):

| Layer | Homegrown maturity | Notes |
|---|---|---|
| Payments rails + wallets | High | eSewa, Fonepay, ConnectIPS/NCHL, Khalti–IME |
| Tax billing / VAT books | Medium-high | Forced by IRD/CBMS; Tally still the floor install |
| Accounting as decision system | Medium | Cloud locals exist; UX and management accounting lag |
| Marketplaces | High for Daraz (foreign-owned) | Demand you do not own |
| Merchant-owned store + POS OS | Low–medium | WooCommerce count + new clones |
| HR / payroll compliance | Medium | SSF/PF/TDS/Dashain; Rippling does not compute this |
| CRM / lifecycle marketing | Very low | Facebook + spreadsheets |
| Restaurant vertical | Crowded early | Many POS vendors, no Toast |
| Other verticals | Thin | Home services, construction, legal, clinics |
| Collaboration suite | Import-dependent | Google / Microsoft — no need to rebuild |

**Constraints unique to Nepal that global SaaS fails:**

- 13% VAT registers in IRD format
- TDS heading codes
- Bikram Sambat fiscal year (Shrawan–Ashadh) on every document
- CBMS invoice sync; issued bills cannot be silently edited
- SSF vs PF, CIT, Labour Act 2074, festival allowance
- NPR wallets and Fonepay QR as default checkout, not Visa

**Practical Nepali stack described then:**

1. Demand: Facebook + Daraz (or Woo if you care about margin)
2. Collect money: Fonepay QR + eSewa + Khalti + ConnectIPS
3. Books: Tally/Swastik or Tigg/OneFlow/Lekhapal/MISAC
4. People: local HRMS above ~15 staff
5. Workspace: Google or Microsoft
6. Restaurant: local POS + Fonepay + IRD — not Toast

**Prize named then (this becomes Bahi’s seed):**

> A merchant OS that sits on Fonepay/eSewa, files CBMS invoices, and owns the customer file — Shopify + QuickBooks + a slice of Toast, for NPR. Restaurant POS vendors try from the counter. Accounting vendors try from the books. Nobody has locked the bundle.

---

## 3. Prompt 3 — New front doors (Blanxer, Zalient)

**Asked:**

> New front door like Blanxer and Zalient coming up. How are they addressing that market as by Shopify?

**Answer shape that followed:**

They are trying to become the *owned storefront*, not another Daraz.

### Blanxer (closer to a commerce OS)

- Founded ~2022/23, Bhaktapur (Lokanthali), bootstrapped, small team
- Origin: founder ran Wrapsy, tried Shopify, hit USD price + no native Nepal rails
- Positioning: “Commerce OS for Nepal”
- Company-claimed scale (treat as upper bound): 550–1,000+ businesses, 1M+ orders, logos including Oliz, Pari, Bloom, and Bhatbhateni jersey drops
- Nepal-ized Shopify motion:
  - Guest checkout tuned for Facebook/TikTok ads (claimed 3–5% conversion)
  - **Blanxer QR** on Fonepay (dynamic QR, bank settlement, skip ~NPR 28.5k Fonepay setup)
  - One-click 3PL: Pathao, Dash, Upaya, Nepal Can Move, Aramex
  - POS on higher plans
  - SMS tracking
  - Tigg hook for books — adjacent, not the core
- Price: NPR 24k / 28k / 38k / 48k **per year** plus **2.75–3.9% on QR**
- Not Shopify: no real app/theme economy, thinner POS than specialists, support complaints at the top tier, no Capital, no Klaviyo-class retention

### Zalient Shop

- Company started on NFC visiting cards, launched free shop builder late 2025
- GTM is price: **Rs 0** after Blanxer removed a free plan
- Tiny distribution (Play Store still early)
- Ambition language (“plugin marketplace, code editor”) ahead of live ecosystem
- Adding chat-to-order / AI commerce as a narrative

### Clone pack around them

SaralNova (done-for-you + WhatsApp alerts, cheaper), Brodox (broader shop OS), ShriGo (cheap builder + take-rate), Saauzi (store + restaurant/retail POS), Jetmux and others named in local forums.

**Strategic read taken forward:**

Nepal’s missing layer is merchant-owned store + POS OS. Blanxer is the first homegrown company *credibly occupying the D2C front door*. The remaining prize is becoming the **system of record** (stock, customer, QR money, IRD invoice, courier payout). Blanxer started that with QR fee + Tigg hook. They have not closed it.

---

## 4. Prompt 4 — Should we build the full bundle?

**Asked:**

> Can you genuinely tell me: is this domain still enterable? Shall I build a product around accounting system with API, MCP, storefront and social media chat agents? What can be a good business model and year for break even in the current market?

This is the founding product question. The answer is the constitution of this repo.

### Verdict preserved

1. **Domain: yes, enterable** — the loop from order to VAT is still unowned as one product.
2. **Full bundle as year-one company: no.** Accounting + storefront + social agents + API + MCP is four products. Each already has an owner.
3. **MCP is not a moat.** By 2026 it is how agents talk to systems. Shopify, Stripe, Xero, HubSpot ship servers. Shipping MCP without owning the record is a wrapper.
4. **Generic chat agents are being productized by Meta** (Business Agent on WhatsApp / Instagram / Messenger, 2026). You will not win “answers DMs.” You can win “the agent is allowed to promise stock and issue a legal invoice.”
5. **Generic cloud accounting is price-compressed** in Nepal at NPR 6k–32k/year. Another P&L screen does not pay a team.
6. **Another theme shop** fights Blanxer, WooCommerce, Zalient, and Daraz at once.

### Wedge preserved

An IRD-correct ledger whose source documents are *orders* (web, POS, chat), with payments auto-matched and stock decremented, plus API/MCP so ChatGPT/Claude and CA tools can query and post.

Ship order:

1. Sales document → stock → VAT invoice → CBMS
2. Payment matching (Fonepay, eSewa, Khalti, ConnectIPS, COD)
3. API first, UI second
4. MCP on that API
5. Chat agent last, only as an order taker that writes the ledger
6. Storefront as embed/headless widget — do not rebuild themes

### Business model preserved

- Subscription NPR 2,000–6,000/month for serious SMBs (also yearly for Tally-minded buyers)
- Small attach on reconciled digital GMV (0.3–0.8%) or per matched payment — capped
- CA seat NPR 500–1,500/client/month
- Implementation NPR 15–40k for multi-branch
- API/MCP free under cap, then metered for agencies and other SaaS

Planning ARPU: **NPR 6,000/month**. If you cannot get that, you have a feature.

### Break-even preserved

Lean Kathmandu team 4–6 people, burn NPR 10–16 lakh/month.

- ~170–270 paying accounts to cover burn at NPR 6k ARPU
- Optimistic cash-flow break-even: month 18–24
- Base: month 24–36 (FY 2084/85, mid-2028 to mid-2029 if build starts late 2026)
- 12-month break-even called founder fan fiction without existing CA/seller distribution

---

## 5. Prompt 5 — This repository

**Asked:**

> Create a git repo for this and include a docs folder with roadmap and original scenario for this product. Be really exhaustive.

That is this tree. The product working name assigned here is **Bahi**.

---

## 6. Constraints the founder accepted by asking for docs

Writing this down commits to:

- A Nepal-first compliance product, not a global “AI commerce OS” slogan
- A refusal list (see `09-non-goals.md`)
- Economics that assume NPR willingness-to-pay, CA-led sales, and Tally inertia
- MCP and chat as *interfaces to a ledger*, not the ledger itself

If a future pitch deck says “the AI Shopify of Nepal,” it contradicts this file on purpose. Flag it.
