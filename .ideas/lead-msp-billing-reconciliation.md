# Lead: MSP billing reconciliation

**Status:** best candidate found so far. Verified pricing. Not yet validated with a real customer.
**Date:** 2026-09-10

---

## Why this one

Every other lead failed on the same thing: no domain access. This one has it — **Ollie works in
IT** and can reach MSPs directly.

It's also the *same problem shape James has already solved*. SecretLeague's hardest part wasn't
the website; it was that the Imprint API lied — counts were per-game not per-series, with gaps —
so records had to be rebuilt server-side from raw match data and reconciled. That is exactly this
problem, in a market that pays.

---

## The problem

An MSP bills clients for licences and services. Two systems disagree:

- What Microsoft 365 (or the RMM) says is **actually provisioned**
- What the PSA/billing system says is **being invoiced**

Drift happens constantly — a client adds seats, someone offboards, a licence lapses. Every gap is
either money the MSP never billed, or a client being overcharged. Someone reconciles it by hand,
in a spreadsheet, every month.

---

## Verified pricing (pages fetched 2026-09-10)

**BillingReconcile** — https://billingreconcile.com/pricing

| Tier | Price | Scale |
|---|---|---|
| Core | **$129/mo** | ~50 clients |
| Team | **$249/mo** | ~75–175 clients |
| Business | **$399/mo** | ~200–400 clients |
| Enterprise | **$649/mo** | ~500–900+ clients |

Add-on: historical reporting from **$19/mo** (30 days → 24 months).

Related, same space:
- **Syncro** — $129–$179 per technician per month; Team tier bundles automated M365 licence billing
- **Sync 365** — compares M365 licence counts against PSA billing records (pricing not published)

Source for Syncro/Sync 365: https://www.syncrosecure.com/pricing/ and
https://www.sync365license.com/pricing/ (search snippets; Syncro figures not fetched directly).

---

## Why this team could win

- **Flat pricing, not per-tech.** Syncro charges per technician. A flat fee is a real wedge.
- **Self-hosted.** Ollie's servers mean near-zero hosting cost, so undercutting doesn't destroy
  margin the way it would for a cloud-hosted competitor.
- **Data-sovereignty angle.** MSPs handle client billing data. "Runs on your own infrastructure,
  your data never leaves" is a genuine differentiator against SaaS-only rivals — especially for
  UK/EU MSPs with GDPR-sensitive clients.
- **The hard part is already known.** Reconciling two disagreeing sources is the exact thing
  SecretLeague does.

---

## Biggest reason it fails

**Incumbents already exist and MSP software is a crowded, relationship-driven market.**
BillingReconcile, Syncro and Sync 365 are already here. MSPs buy through channel relationships and
peer recommendation, not search. Without Ollie actively selling into people he knows, this is
unwinnable — the product is not the hard part.

Secondary risk: integrations mean Microsoft Partner Center and PSA APIs (ConnectWise, Halo,
Autotask). Partner-API access can require approval and paperwork.

---

## The next test — do this before writing code

Ollie asks **three MSPs he already knows**:

1. How do you check your M365 licence counts match what you invoice?
2. Who does it, how long does it take, how often does it go wrong?
3. What do you use, and what do you pay?

If all three say "spreadsheet, half a day a month, painful" — that's the product.
If they say "our PSA handles it" — kill it and move on, cheaply.

---

## PARKED 2026-09-10 — and why

Real problem, real money, but **wrong project for what James wants to learn.** It needs no
Kubernetes (one container would do) and AI adds nothing — it's reconciliation and arithmetic.
Picking it would mean working against his own goals with no deadline to force him through.

Kept here in case Ollie ever wants it. See `direction-self-hosted-ai.md` for the direction taken
instead.

---

## Short version for Ollie

An MSP bills each client monthly for things that keep changing — Microsoft 365 seats, monitored
devices, backup storage. Those numbers live in different systems that don't talk to each other, so
the invoice drifts away from reality. Someone reconciles it by hand in a spreadsheet every month.
Every gap is either money the MSP never billed, or a client being overcharged who eventually
notices.

Tools already exist for this: BillingReconcile charges **$129–$649/month flat**, Syncro charges
**$129–$179 per technician per month**.

Our angle would have been flat pricing plus self-hosting — "runs on your own kit, your client
billing data never leaves". The reason we parked it is fit, not viability. If you think it's worth
a look, say so.
