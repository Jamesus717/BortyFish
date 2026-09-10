# Opportunities — 2026-09-11

**UPDATE 2026-09-10:** the VERIFIED section below has since been filled in from pages actually
fetched in the interactive session. Leads 1 and 3 are now resolved. The original low-confidence
warning still applies to everything in the SEARCH-SNIPPET and INFERRED sections.

**Confidence: LOW.** Egress probe (see `routine-log.md`, 2026-09-10 20:30 BST) found 9 of 10
target domains blocked by the sandbox's network proxy — same failure as the previous routine.
Only `github.com` was directly fetchable; it carries no pricing data. **Every money figure below
comes from a WebSearch result snippet, not a page I fetched myself.** That means nothing here
clears this task's own bar for "verified" (a source URL I actually fetched). Treat all of it as
**directionally useful, not confirmed** — before spending real time on any of these, fetch the
vendor pricing pages directly once egress works, or check them by hand in a browser.

Per the brief: community esports league/tournament SaaS was investigated and killed
(`decisions.md`, 2026-09-10). Not revisited. Sports-data/odds APIs are excluded below for the
same reason (see INFERRED section) even though they showed strong pricing evidence.

---

## VERIFIED (fetched from a primary source)

Filled in 2026-09-10 by the interactive session, which is not behind the sandbox egress proxy.
These pages were actually fetched.

### 1. Google Sheets data connector — STRONG, best fit

**Coefficient** — https://coefficient.io/pricing (fetched 2026-09-10)

| Tier | Price |
|---|---|
| Free | $0 — 3 sources, 5k rows, 50 refreshes/mo |
| Starter | **$49/mo** — "solo builders operationalising manual workflows" |
| Pro | **$99/user/mo** — small teams, hourly refresh, 5 users |
| Enterprise | Custom |

**Why it matters:** people pay $49–$99 *per user per month* to get messy third-party data into a
spreadsheet on a schedule. That is exactly what SecretLeague already does (Imprint API → Google
Sheets → live site), including the hard part: reconciling an upstream API that lies.

Sheetgo exists in the same space but hides pricing behind per-product pages (fetched, no figures).

**Biggest reason it fails:** the generic version is taken. This only works aimed at one specific
vertical whose data source nobody else has bothered to connect.

### 2. Embedded analytics — real money, WRONG SHAPE

**Luzmo** — https://www.luzmo.com/pricing (fetched 2026-09-10)

- **From €1,995/month**, billed annually, platform fee + usage
- Customers named: Grubhub, Lansweeper, Greenly, Marigold

**Verdict: skip.** The money is real but it's enterprise — annual contracts, procurement, security
reviews, competing against funded companies. Unwinnable on evenings and weekends, and nothing
about the price point suits a first product.

### 3. Premium Discord bot — KILLED

Discord's entire Premium Apps programme is **an estimated $5–19M per year in total**, roughly
0.5–2% of Discord's revenue, split across every developer on the platform. Discord takes 15% of
the first $1M, then 30%.
Source: https://techpoint.africa/guide/how-does-discord-make-money/ (search snippet — the page
itself was not fetched, so treat the figure as approximate).

**Verdict: dead.** Even a dominant share of that category wouldn't support two people. The pond is
too small regardless of execution.

---

## SEARCH-SNIPPET SOURCED (WebSearch only — treat as leads, not proof)

### 1. Niche Google Sheets data-connector (Sheetgo/Coefficient model, one underserved vertical)

- **What it is:** A tool that syncs a specific messy third-party data source (an API, a scrape,
  another app) into Google Sheets on a schedule, so non-technical users get a live spreadsheet
  instead of manual copy-paste.
- **Who pays / what they pay:** Sheetgo — Free tier, Professional from $22/mo, Business from
  $79/mo (source: automationatlas.io / Capterra snippets, via WebSearch, not fetched). Coefficient
  — Free tier, Starter $49/mo, Pro $99/user/mo (source: coefficient.io snippet via WebSearch).
  Both are general-purpose players with years of runway.
- **Why this team could win:** This is almost exactly the SecretLeague stack already
  proven in production — Google Sheets as live backend, third-party API integration, reconciling
  unreliable upstream data (Imprint API). The pitch isn't "compete with Sheetgo" — it's "own one
  specific ugly data source Sheetgo/Coefficient don't bother integrating" (a niche community
  platform, a hobby-specific API, a scraped source with no official API).
- **Biggest reason it fails:** Generic connectors are a scale game — value comes from breadth of
  integrations and reliability across thousands of edge cases. A 2-3 person team can own one
  vertical well, but the addressable market for any single niche source may be too small to
  matter, and "sync your weird API into Sheets" is a feature, not obviously a stand-alone product
  someone searches for and pays $20+/mo for.

### 2. Niche premium Discord utility bot (one workflow, not general moderation)

- **What it is:** A Discord bot solving one specific recurring admin task for one type of
  community (not another MEE6/Carl-bot moderation clone).
- **Who pays / what they pay:** Incumbent premium bots: MEE6 ~$11.95/mo, Carl-bot ~$7.99/mo, Dyno
  ~$4.99/mo, Arcane ~$7/mo (source: peakbot.pro blog snippets via WebSearch). Search-snippet
  claims (unverified, secondary blog — shipworkflow.com) about paid Discord *communities* (not
  bots) reaching real MRR in specific niches: trading-signal communities $49-299/mo,
  fitness-coaching $29-79/mo.
- **Why this team could win:** Direct skill match — Discord OAuth is already built and proven.
  Building one narrow, well-executed bot for a specific hobby/community type plays to "ship
  something small and real" rather than competing head-on with MEE6's breadth.
- **Biggest reason it fails:** Discord bot monetization needs either high volume of small
  servers paying a little (needs distribution/marketing they don't have) or one high-trust niche
  paying a lot (trading/fitness — no credibility or audience there). Server churn on Discord is
  high; retention is the real product problem, not the build.

### 3. Scoped-down embedded chart widget for small SaaS products

- **What it is:** A cheap, simple way for a small SaaS to embed a good-looking customer-facing
  chart/dashboard, without buying a full embedded-analytics platform.
- **Who pays / what they pay:** Enterprise embedded-analytics vendors charge real money — Sisense
  Launch $399/mo (50 viewer seats), Grow $1,299/mo; Embeddable Starter €495/mo, Premium €1,995/mo
  (source: WebSearch snippets, vendor sites not fetched). Market sized at $27-57B in 2026 per the
  same snippets — treat the market-size figure as marketing copy, not a reliable number.
- **Why this team could win:** SVG data visualisation is a demonstrated skill (the SecretLeague
  wheel bracket). A stripped-down "just the chart, none of the BI platform" product undercuts
  Sisense/Embeddable's price point by an order of magnitude.
- **Biggest reason it fails:** This is a cold B2B sale into other software companies — a sales
  motion this team has no track record in. It also competes with free open-source chart libraries
  (Chart.js, ApexCharts, D3) that cover most of what a small SaaS actually needs, which caps how
  much anyone will pay for "just a chart."

---

## INFERRED (no direct payment evidence, or evidence excluded on purpose)

- **Sports odds/data reconciliation API** — WebSearch snippets showed real, substantial pricing
  (The Odds API from $30/mo, SportsGameOdds $99-499/mo, Unabated from $3,000/mo) and a strong
  skill match (reconciling unreliable upstream sports data is exactly what SecretLeague already
  does). Deliberately **not** proposed as a candidate: it's the same sports-data vertical as the
  killed league-management idea, and it adds gambling-industry compliance/licensing overhead that
  doesn't fit an evenings/weekends team. Flagging it here so it isn't silently missed, not
  recommending it.
- **Uptime monitoring / status pages** — repeatedly mentioned in "indie SaaS ideas" listicles as
  profitable, with a "Better Uptime started small and grew to millions in ARR" claim. Excluded as
  a candidate: the source is a secondary listicle (planmysaas.com), not the vendor, and the space
  is crowded with strong free/cheap incumbents (UptimeRobot, Pingdom, Atlassian Statuspage). Also
  doesn't play to this team's specific strengths (Sheets, SVG viz, Discord, data reconciliation)
  — it's generic devtools.
- **Freelance data-pipeline/API-integration contract work** — Upwork listing snippets confirm
  demand exists but gave no reliable rate figures. This is consulting income, not a product; worth
  noting as a bridge/cashflow option, not a business.

---

## WHAT I COULD NOT VERIFY

- No pricing page was fetched directly for any candidate — Sheetgo, Coefficient, MEE6, Carl-bot,
  Sisense, and Embeddable pricing above are all secondary WebSearch snippets, some from
  comparison/listicle sites rather than the vendors themselves. Numbers may be stale, wrong, or
  editorialised by the source site.
- Could not confirm actual customer counts, retention, or real revenue (MRR/ARR) for any specific
  competitor — only list-price pricing tiers, which don't prove anyone is actually paying at
  volume.
- Could not check whether any of these niches already has a well-funded competitor doing exactly
  this (the killed league-SaaS research found strong competitors by direct site visits — that
  method wasn't available this run).
- Could not verify the "$15.7B → $59.6B micro-SaaS market" and "$27-57B embedded analytics
  market" figures — these read as SEO-blog marketing stats, not sourced data, and should not be
  treated as real.
- Egress was blocked identically to the previous routine's run — this is not a one-off blip.
  Worth checking with James/Ollie whether the sandbox network policy can be changed, since it is
  now blocking two runs in a row and capping what this kind of research can actually confirm.
