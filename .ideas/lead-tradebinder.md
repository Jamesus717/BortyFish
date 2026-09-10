# Lead: TradeBinder / BortyTrades — revive it

**Date:** 2026-09-10
**Status:** strongest lead yet. Already substantially built. Real distribution.

---

## What already exists

`Documents/1TradeVault/TradeVaultFirstEd` — last commit **2026-05-13**, ~4 months dormant.
Live at `tradevault.jamesfburt69.workers.dev`.

Next.js + TypeScript + Tailwind, Supabase (auth, Postgres, RLS, Realtime, Storage), deployed to
Cloudflare Workers via OpenNext.

Already working:
- **Binder / collection** — browse sets, search, sort, owned-variant tracking, bulk actions
- **Public profiles** (slug routes)
- **Trade board** — listings with card search and image upload
- **Inbox + messaging + offers** — accept / decline / counter, in-chat
- **Realtime notifications** with unread badge
- Server-side Pokémon TCG API layer, eBay auth integration

This is far more finished than anything else we've considered. Reviving beats starting over.

---

## What's crowded — do NOT compete here

**Collection tracking and AI card scanning is a solved, busy market.**

- **Collectr** — $4.99/mo annual, $7.99 monthly. Scans a card, identifies exact set/number/variant,
  20+ TCGs, graded and sealed, 5+ years price history.
- **TCGDex**, **DittoDex**, **CollectDeck**, **TCG Scanner** — all AI scanning, all shipping.

Source: https://getcollectr.com/ , https://www.getcollectdeck.com/ (search snippets)

Scanning is now table stakes, not a differentiator. Building "another scanner" loses.

---

## The wedge: TradeHubs — and someone is already on it

James's idea is physical card shops as verified **TradeHubs** for in-person trading, using his
existing relationships with real Pokémon shops and sellers.

**This is genuinely the right wedge** — it fixes the two hardest problems in peer-to-peer card
trading (trust, and shipping risk) that the big online marketplaces don't.

**But it is not unclaimed.** **CardChase** (https://cardchase.org/) does exactly this: an app for
trading in person at "verified locations" and "Trainer Centers" — real card shops — with public
trader reputation and family/parent account management.

**How far along is CardChase?** Fetched 2026-09-10:
- Version 4.0.0, on **TestFlight** plus Google Play — still beta / early
- **No disclosed user numbers, no pricing, no stated countries**

**Read:** the concept is validated — somebody thought it worth building — but nobody has won it,
and it looks early. That's a much better position than an entrenched incumbent.

---

## Why James specifically could win it

**Distribution.** He already knows real Pokémon shops and sellers who'd act as TradeHubs, and some
who'd potentially invest.

That matters more than the software. Marketplaces die of the cold-start problem: no traders
without shops, no shops without traders. **Shop relationships solve exactly that** — each shop
brings its own existing customers. CardChase has to sign shops from cold; he doesn't.

This is the first idea where the asset isn't the code — it's the network.

---

## Where AI and Kubernetes actually fit

Honestly, neither is the headline. But both have a real place:

- **Card scanning needs AI** — and it's now table stakes, so it's needed for *parity*, not
  advantage. The advantage is cost: running recognition on Ollie's GPU resource means **no per-scan API
  fee**, which is a genuine margin edge over rivals paying per call at scale.
- **Kubernetes** — a Next.js app doesn't need it. Self-hosting the scanning model does: GPU
  scheduling, scale-to-zero when idle, rolling model updates. Legitimate, but it belongs at the
  inference layer, not bolted round the web app.

---

## Biggest reasons it fails

1. **Two-sided cold start.** The classic marketplace killer. Shop relationships are the mitigation,
   which is why they must be confirmed *before* building more.
2. **CardChase gets there first**, or a funded competitor enters. The concept is public now.
3. **Trust and safety is real work.** In-person trades involving minors and valuable goods means
   verification, reputation, dispute handling and safeguarding. Not optional, not glamorous.
4. **Money is unclear.** Collectr charges $5–8/mo for tracking. Whether traders pay, shops pay, or
   it's transaction fees is unanswered — and it decides the whole product shape.

---

## Next steps, in order

1. **Talk to three shops.** Would they act as a TradeHub? What's in it for them — footfall, a cut,
   a fee? Would they pay, or want paying? Their answer defines the business model.
2. **Look at CardChase properly.** Install it. Is it UK? How good is it? What's missing?
3. **Only then decide what to build.** Most of the app already exists — the gap is TradeHubs and
   scanning, not the collection features.
