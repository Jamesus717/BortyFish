# Ollie — pitch: TradeBinder

**Repo:** https://github.com/Jamesus717/TradeVaultFirstEd
**Live (old build):** https://tradevault.jamesfburt69.workers.dev/

---

## In one line

A Pokémon card collection and trading app, where trades happen **in person at real card shops**
instead of by posting cards to strangers.

---

## Why this one, and not the other ideas

We looked at four things tonight and killed three (MSP billing, transcription, insurance AI). This
is the one that survived, for two reasons:

1. **It's already ~70% built.** Not a napkin sketch — a working app.
2. **James knows actual Pokémon shops.** That's distribution, and it's the thing that normally
   kills marketplaces.

---

## What already exists

Next.js + TypeScript + Tailwind, Supabase (Postgres, auth, RLS, Realtime, Storage), deployed to
Cloudflare Workers.

**11 database tables, 5 migrations, 9 pages, 5 API routes.** Working:

- **Collection / binder** — browse sets, search, sort, track which variants you own, bulk actions
- **Wishlist**
- **Public profiles** with shareable slug URLs
- **Trade board** — create listings, card search, image upload
- **Inbox + messaging** — with offers inside chat: accept / decline / counter
- **Realtime notifications** with unread badge
- **Pokémon TCG API** wrapped server-side, plus eBay auth for pricing

It's been dormant since **13 May 2026**. Nothing's broken — it just stopped.

---

## The actual opportunity: TradeHubs

Trading cards with strangers online has two problems nobody's solved well: **you might get
scammed**, and **posting valuable cards is a pain**.

The idea: **real card shops become verified "TradeHubs"** — you arrange the trade in the app, then
meet at a shop to do it. Shop gets footfall. Traders get safety.

James already knows shops and sellers who'd host this, and some who'd potentially invest.

**Being straight with you:** a company called **CardChase** is already building exactly this.
So the idea is validated — but they're still on TestFlight at v4.0.0, with no published user
numbers, pricing or countries. Early, not entrenched.

**What decides it isn't the app — it's who signs up shops first.** They're doing it cold. James
isn't.

---

## Where you come in

This is where your side matters more than the web app, and it's the genuinely interesting
engineering:

**1. Card scanning on our own hardware.**
Every rival app scans cards with AI (Collectr, TCGDex, DittoDex — all shipping). It's table stakes
now, so we need it. But they all pay a cloud API per scan.

**We wouldn't.** Running recognition on your GPU resource means the marginal cost of a scan is
electricity. At volume that's a real margin advantage, and it's the kind of thing that's very hard
to undo once it's working.

**2. That's where Kubernetes actually earns its place.**
Not around the web app — a Next.js app doesn't need it. Around the **inference layer**: GPU
scheduling, scale-to-zero when nobody's scanning, rolling model updates without downtime. James
wants to learn k8s and this is a legitimate reason to use it rather than a bolted-on excuse.

**3. Hosting.**
Currently Cloudflare Workers. Moving it onto your kit gives us cost control and somewhere to put
the GPU work next to the app.

**4. Trust and safety infrastructure.**
In-person trades, sometimes involving kids, sometimes valuable cards. Verification, reputation,
dispute handling. Unglamorous but it's the product, not a feature.

---

## Honest risks

- **Two-sided cold start.** No traders without shops, no shops without traders. Shop relationships
  are the whole mitigation — if they don't materialise, this doesn't work.
- **CardChase or someone funded gets there first.**
- **We don't know who pays yet.** Traders? Shops? A cut of trades? Collectr charges $5–8/month for
  tracking alone, so people do pay in this space — but our model is undecided, and it changes what
  we build.
- **Trust and safety is real, ongoing work**, not a launch task.

---

## What we'd decide first

Before writing code:

1. **Talk to three shops.** Would they host a TradeHub? What's in it for them — footfall, a cut, a
   fee? Would they pay us, or expect paying? Their answer defines the business.
2. **Install CardChase.** Is it UK? How good is it? What's missing?
3. **Then scope.** Most of the app exists. The gap is TradeHubs and scanning.

---

## Why it's worth your time even if it fails

You'd be running a real multi-tenant GPU workload on your own cluster, with real users on it.
That's a better k8s and self-hosted-AI portfolio piece than anything you'd build as a lab exercise,
and it stays useful regardless of whether the business works.

No deadline on any of this.
