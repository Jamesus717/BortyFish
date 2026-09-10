# History

What's been built, tried and learned. Newest first. Append a dated section; don't rewrite old ones.

---

## 2026-09-10 — ECC evaluated, not adopted

James asked whether [affaan-m/ECC](https://github.com/affaan-m/ECC) would help. Verdict: **take
ideas, don't install.**

- Real project — MIT, actively maintained, shipping daily. Quality isn't the issue.
- **91MB, 3,699 files, 291 skills, 68 agents.** Built for large teams across seven agent harnesses.
- Its own tagline is *"optimise the context window"*, but installing hundreds of always-loaded
  skills and rules into a two-person project does the opposite.
- Its hooks execute code. Adopting 3,699 files of someone else's automation is a real
  supply-chain and maintenance surface for a team of two.

Worth stealing conceptually: `plan → test → implement → review → verify → remember → improve`.
We already do most of that; persistent memory and `CLAUDE.md` cover the "remember" part.

Revisit if the team grows past ~5 people or work spans many repos.

---

## 2026-09-10 — League-management SaaS: killed

Ruled out as a business. See `decisions.md`.

---

## 2026-08 → 2026-09 — SecretLeague (`Jamesus717/SecretShop2`)

A live UK community Dota 2 league site — 22 teams, ~110 players. James's main build, and the
source of most of the experience so far. Static site on Cloudflare Pages + Pages Functions,
Supabase, Google Sheets, and the Imprint esports API.

**What got built:**
- Team registration with roster/rank/Steam-ID validation, logo upload, Discord auth
- Team Info, group-stage schedule, standings with divisions, playoff brackets
- A circular "wheel" bracket rendered as SVG, driven live from a Google Sheet
- Server-side sync computing true win/tie/loss records from match data

**Hard-won lessons (all now in that repo's `CLAUDE.md`):**
- Cloudflare returns **200 + HTML** for missing files, cached ~4h — a 200 never proves a deploy
- Windows hides case-sensitivity bugs that break on the live host
- Never recreate an Apps Script deployment; old `/exec` URLs stay live with frozen code
- Unapplied Supabase migrations usually fail **silently**
- Third-party APIs lie: Imprint's own win/loss aggregates were per-game not per-series, with real
  gaps — had to be rebuilt from match-level data
- A sync that marks work "done" on failure will quietly destroy its own backlog during an outage

---

## Standing context

- **James** builds around a day job, often late at night in short bursts.
- He hands over control readily and acts on what he's told — so being wrong is expensive, and
  flattery is worse than useless.
- **Ollie (breadfish)** — infra lead. **Multiple servers + some GPU resource** available for use,
  **IT infrastructure**, **k8s cluster admin**, **Linux sysadmin**. Business is a three-way effort.
