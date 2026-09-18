# 12 — Storefront and chat (as clients)

These are **clients of the ledger**, not the product identity.

## Storefront strategy

### What we ship

1. **Headless checkout widget**  
   Mount on Woo, custom PHP, even a Blanxer custom HTML block if they allow it. Shows cart, guest checkout, Fonepay QR, COD, creates Bahi orders.

2. **WooCommerce plugin**  
   Product sync optional (Bahi catalog as master *or* Woo as master — pick one per org). Orders and payments always master in Bahi once confirmed.

3. **POS-lite**  
   Browser + thermal print + barcode. Enough for a brand counter. Not a restaurant floor system.

### What we do not ship in year 1

- Theme editor
- Blog
- App store
- Visual landing page builder
- Multi-vendor marketplace

If a merchant has no website, send them to Woo + our plugin or to Blanxer + our API. We can keep a referral list. We do not become their agency except as paid implementation.

## Chat strategy

### Reality

Nepali D2C demand arrives as:

- Instagram DMs
- Facebook Messenger
- TikTok comments + inbox
- WhatsApp (growing; Viber still used in pockets)
- Phone notes typed into Viber

Meta is putting an agent on three of those surfaces. Fighting that text layer is vanity.

### What Bahi agents are for

A **constrained order taker**:

1. Identify item (catalog search, image later)
2. Check `get_stock`
3. Quote price including VAT policy
4. Collect size / address / PAN if needed
5. `create_draft_order`
6. Send pay link / QR or mark COD
7. Hand to human on anything fuzzy

Tone can be Nepali + English mix. The model is a commodity. The tools and the policy are the product.

### Channel adapters

| Channel | Year 1 | Notes |
|---|---|---|
| Web widget chat | yes | We control the page |
| WhatsApp Cloud API | yes if a beachhead needs it | Template + session rules; cost line item |
| Instagram Messaging | limited | Webhook + human assist; official APIs change |
| Messenger | same as IG | |
| TikTok | no official good API | Operator pastes into Bahi inbox |
| SMS | notifications only | |

### Human inbox

A unified “unparsed demand” queue: paste a screenshot or forward a DM, AI suggests a draft order, human confirms. This will close more sales in 2026 Nepal than a fully autonomous agent.

## Agent quality bar

Ship only when we can measure:

- % of suggested orders accepted without edit
- % of agent quotes that matched live stock
- Zero unauthorized `issue_invoice` calls
- Time-to-first-response on the web widget

If those are worse than a junior operator, keep the agent in suggest mode.
