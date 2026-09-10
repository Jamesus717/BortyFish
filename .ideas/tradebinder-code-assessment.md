# TradeBinder — code assessment

**Date:** 2026-09-10
**Repo:** https://github.com/Jamesus717/TradeVaultFirstEd
**Local:** `Documents/1TradeVault/TradeVaultFirstEd`

---

## Verdict: it's alive, and in better shape than expected

**`next build` passes clean** after four months untouched — TypeScript compiles, 14 routes
generate, zero errors. Nothing has rotted.

~9,500 lines across `app/`, `lib/` and `supabase/`. Stack is current, not stale:
Next.js **16.2.5**, React **19**, Tailwind **4**, TypeScript **5.9**, Supabase JS **2.103**,
deployed to Cloudflare Workers via OpenNext. Dependencies were fresh when it stopped.

**No TODOs, no FIXMEs, no stubbed-out functions.** It stopped mid-project, not mid-thought.

---

## What's actually wired up

| Area | State |
|---|---|
| Auth (email + Google OAuth) | Working |
| Collection / binder, owned variants, bulk actions | Working |
| Wishlist | Working |
| Public profiles (`/u/[slug]`) | Working |
| Trade board with listings, card search, image upload | Working |
| Inbox, conversations, offers (accept/decline/counter) | Working |
| Realtime notifications | Working |
| Pokémon TCG API proxy (5 routes, cached) | Working |
| eBay pricing | Wired into `/api/pokemon/price` |

11 tables, 5 migrations, RLS policies on everything.

---

## Real problems found

**1. `app/trade/page.tsx` is 1,419 lines.** One file holding the board, filters, the listing
modal, and card search. This is the file TradeHubs has to change, and it will fight back. Worth
splitting *before* adding to it, not after.

**2. `app/navbar.tsx` is 831 lines** — because the entire auth flow (login, signup, password
reset, username picker) lives inside the navbar component. Should be its own route or modal
module.

**3. `app/inbox/[conversationId]/page.tsx` is 951 lines.** Same pattern.

None of these are bugs. They're the reason the next feature takes three days instead of one.

**4. `/bortytest` ships to production.** A price-testing page, included in the build output.
Delete it or move it behind a dev flag.

**5. `NEXT_PUBLIC_DEV_PRICES`** switches `/api/pokemon/price` into a dev mode. Being
`NEXT_PUBLIC_`, it's exposed client-side. Worth checking it can't be flipped in production.

---

## What TradeHubs actually needs

Good news: **location awareness already exists.** `trade_listings.postcode_prefix` is on the
schema and flows all the way through to the conversation view ("SW1 area").

Missing:

- A `trade_hubs` table — shop name, address, coordinates, opening hours, verified flag
- A link from a conversation/trade to a chosen hub ("meet at X")
- **Real geo search.** Postcode *prefix* is a string match — "within 10 miles" needs lat/lng and
  a distance query. Postgres has `earthdistance`/PostGIS for this.
- Shop-side view: which trades are scheduled at my shop this week

That's a well-scoped piece of work, not a rewrite.

---

## Ollie's work queue

Ranked by value, with the traps marked.

### 1. Self-hosted card scanning service — **start here**
The actual differentiator. Every competitor pays a cloud API per scan; on Ollie's GPUs the
marginal cost is electricity.

Cleanly separable: an HTTP service that takes an image and returns a card ID. The Next app calls
it. It can be built and tested with **zero changes to the existing codebase**, which makes it the
ideal first job — two people working in parallel without treading on each other.

This is also where Kubernetes genuinely belongs: GPU scheduling, scale-to-zero, rolling model
updates.

### 2. Containerise the Next app + a deploy pipeline
Currently Cloudflare Workers via OpenNext. Getting it running in a container on his cluster gives
cost control and puts the app next to the GPU work. Good, real k8s learning.

### 3. Object storage for card images
Currently Supabase Storage. MinIO or similar on his kit is a straightforward swap and cuts a
dependency.

### ⚠️ Do NOT self-host Supabase yet
Tempting, and a trap. Supabase is providing auth, Postgres, row-level security, Realtime *and*
storage. Replacing all of that is weeks of work for near-zero user-visible gain, and every hour
spent on it is an hour not spent finding out whether shops want this.

Revisit only when there's revenue, or a concrete reason (cost, data residency) that isn't
"it would be neat".

---

## Suggested first move

1. **James** — split `trade/page.tsx` and add the `trade_hubs` table + real geo search.
2. **Ollie** — stand up the scanning service as a standalone container, no repo changes needed.
3. Meet in the middle when both halves work.

Neither blocks the other. And neither needs a business-model decision first — but the shop
conversations (`lead-tradebinder.md`) should still happen in parallel, because they decide
whether any of this is worth finishing.
