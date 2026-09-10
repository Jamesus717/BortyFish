# Ollie's Quest Log ⚡

Welcome to TradeBinder. You're the infrastructure half.

The good news: **the app already works.** It builds clean, 14 routes, no errors, four months
after James last touched it. You're not rescuing a wreck — you're bolting an engine onto
something that already drives.

Your jobs are the ones that make us **cheaper and harder to copy** than every rival app.

---

## 🥇 Badge 1 — The Scanner
### *Build the thing that makes us different*

**The job:** an HTTP service. Send it a photo of a Pokémon card, it sends back which card it is.

**Why it matters:** every competitor — Collectr, TCGDex, DittoDex — pays a cloud API *every single
time someone scans a card*. On your GPUs, a scan costs electricity.

That's not a feature. That's a margin advantage they can't match without buying hardware.

**Why you'll enjoy it:** it's completely standalone. One container, one endpoint. **You don't need
to touch James's codebase at all** — he keeps building the app, you build this, they meet in the
middle later. No merge conflicts, no waiting on each other.

**Done when:** `POST /scan` with an image returns a card ID, and it runs on your kit.

> *Start here. Everything else can wait.*

---

## 🥈 Badge 2 — The Cluster
### *Kubernetes, for an actual reason*

**The job:** get the scanner running properly on your cluster.

This is where k8s stops being a CV line and starts being load-bearing:

- **GPU scheduling** — several people scanning, finite GPUs, something has to queue them
- **Scale to zero** — nobody scanning at 4am? Don't hold a GPU
- **Rolling updates** — swap the model without dropping anyone mid-scan
- **Multi-tenant isolation** — when shops come on board, their data stays theirs

James wants to learn k8s. This is the honest excuse — not a lab exercise, a real workload with
real users.

---

## 🥉 Badge 3 — The Move
### *Bring the app home*

**The job:** containerise the Next.js app and run it on your infrastructure instead of Cloudflare.

Gets us cost control, and puts the app next to the GPU work so they're not talking across the
internet.

**Bonus round:** card images currently live in Supabase Storage. MinIO on your kit is a clean
swap and drops a dependency.

---

## ☠️ The Trap — read this one

### **Do NOT self-host Supabase.** Not yet.

It's tempting. It's the obvious next domino. It's also weeks of your life.

Supabase is currently giving us: authentication, Postgres, row-level security, realtime
subscriptions, *and* file storage. All of it working. Replacing that stack buys us **nothing a
user would ever notice.**

Every hour spent there is an hour not spent finding out whether card shops actually want this.

Revisit when there's revenue, or a real reason that isn't "it'd be neat".

*(There's always one trap. This is it.)*

---

## 📋 The board

| | Quest | Why | Blocked by |
|---|---|---|---|
| 🥇 | Scanner service | The margin advantage | nothing |
| 🥈 | k8s + GPU scheduling | Makes it real | Badge 1 |
| 🥉 | Containerise the app | Cost control | nothing |
| 🎁 | MinIO for images | Drop a dependency | nothing |
| ☠️ | ~~Self-host Supabase~~ | **Don't** | — |

---

## What James is doing meanwhile

Backend and frontend: making the API faster, unpicking some oversized files, and smoothing out
the app (his words: *"it feels clunky"*). Then the **TradeHub** work — card shops as verified
places to meet and trade.

Your half and his half don't overlap. That's deliberate.

---

## Anything you need to know

- **Repo:** https://github.com/Jamesus717/TradeVaultFirstEd
- **Stack:** Next.js 16, React 19, TypeScript, Supabase, currently on Cloudflare Workers
- **Full technical assessment:** `.ideas/tradebinder-code-assessment.md`
- **Why we're building this at all:** `.ideas/pitch-ollie-tradebinder.md`

**No deadlines on any of this.** If the business works, brilliant. If it doesn't, you've run a
real multi-tenant GPU workload on your own cluster with real users on it — which beats any
tutorial you'd have done instead.

Now go catch 'em all. 🔴⚪
