# Decisions

Settled calls. **Don't relitigate without new evidence** — but do reopen if evidence appears.

---

## 2026-09-10 — League/tournament management SaaS: NO

**Decision:** not pursuing it as a business. James's call, same day as the research.

**Why:**
- Toornament, Challonge, Battlefy and start.gg all cover registration, brackets and scheduling on
  **free tiers**, with years of head start.
- The nearest peer — **Kobold League** (UK, same Imprint stats API) — **built their own site
  rather than buying one.** The people who run community leagues are the sort who enjoy building
  the site. That's the buyer not existing.
- The genuine differentiator (standings computed from live match data instead of manual score
  entry) is real engineering, but nobody was shown to pay for it.
- The closest open-source analog, D2-LRG, went unmaintained with no paid successor.

**Caveat on the evidence:** the overnight research run had most vendor sites blocked by its network
proxy, so **no pricing figure was verified from a primary source** and the Kobold League claim was
inferred from search results, not the site itself. The conclusion is directionally sound but the
evidence base is thin. If someone actually asks to buy it, that's new evidence.

**Reopen if:** two or more organisers independently ask to pay for it.

---

## 2026-09-10 — ECC harness: NO (take ideas only)

Overkill at this team size — 3,699 files and 291 always-loaded skills work against the context
window we're trying to protect. Full reasoning in `history.md`.

**Reopen if:** the team passes ~5 people or work spans many repos.

---

## 2026-09-10 — Notes format: markdown, not JSON

James asked whether another format would be easier for Claude to read and write.

**Answer: no.** Markdown is the best option. JSON adds syntax noise and can't hold nuance or
reasoning. There is no special "AI-native" format that reads better — structured markdown with
clear headers is already the optimum. Keep prose for the *why*, tables for comparisons.

---

## 2026-09-10 — Small recurring jobs go in software, not in Claude

The league data sync runs as a **GitHub Actions cron**, not a scheduled Claude session.

If a task is fully defined and verifiable, ten lines of YAML does it better, free, forever, with
no model in the loop. Claude is for the parts that need judgement.
