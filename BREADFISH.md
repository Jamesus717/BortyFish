# Hello Ollie 👋

This is the shared notes repo for you, James (Borty) and Claude. **BortyFish** = Borty + breadfish.

It is **not code**. It's where we keep ideas, decisions and what we've learned, so nobody has to
remember it all and Claude can read the same context every time.

---

## The goal

Build software that makes **real money** — enough for James and his partner to live on.

Not a hobby. Not an app we never charge for.

---

## Who does what

| Who | Does |
|---|---|
| **James** | Builds the software. Runs a Dota 2 league (110 players) as the practice ground. |
| **Ollie (you)** | TBD — James will fill this in. |
| **Claude** | Builds, tests, researches, checks facts. Tells us when we're wrong. |

---

## What already exists

**SecretLeague** — a working website for James's Dota 2 league. 22 teams, ~110 players.

It does real things:
- Teams sign up, with their ranks checked automatically
- Live league table that works out wins and losses from real match data
- Playoff brackets drawn as a circle
- Logins through Discord

**Why it matters:** it proves we can build and ship a real thing that real people use. That's the
skill we're trying to turn into money.

---

## Rules we work by

1. **No cheerleading.** If an idea is bad, we say so early. Better than wasting three months.
2. **Evidence over opinion.** "People would probably pay for this" means nothing. Has anyone
   *actually* paid for something like it?
3. **Write decisions down.** So we don't argue about the same thing twice.

---

## Ideas list

### ❌ Ruled out

**Selling our league software to other tournament organisers.**

We looked into it on 10 Sep 2026. Killed the same day.

- Big free tools already exist (Challonge, Battlefy, start.gg)
- The one similar league we found **built their own site instead of buying one**
- That's the problem: people who run leagues are the type who enjoy building the site themselves

*Full reasoning in `.ideas/decisions.md`.*

### 👉 Current focus — read this one

**TradeBinder** — reviving James's Pokémon card trading app and adding "TradeHubs" (real card
shops as safe in-person trading venues).

**Pitch written for you: `.ideas/pitch-ollie-tradebinder.md`** — start there. It covers what's
already built, where your infra and GPU work fits, and the honest risks.

Repo: https://github.com/Jamesus717/TradeVaultFirstEd

### 🔎 Also looked into

A proper research run happens **tonight (10 Sep, 20:30)**. It's looking for things people are
**already paying for** that we could build in evenings and weekends.

Results will appear in `.ideas/opportunities-2026-09-11.md`.

Strict rule for that list: if we can't find proof someone already pays, it doesn't go on it.

### ➕ Add your own

Make a file in `.ideas/`, name it after the idea. Anything is fine — rough is fine.

Useful to include:
- What is it?
- Who would pay?
- Why us?

---

## Honest expectations

Worth knowing before we start, so nobody's disappointed:

- Most people doing this make **under £1k/month**
- The ones who do well take **12–18 months** to reach ~£10k/month, counting from their *first
  paying customer*
- Roughly the top 10% get there at all

*Sources: [Indie Hackers](https://www.indiehackers.com/post/tech/hitting-125k-mrr-as-a-solo-founder-by-doubling-down-on-the-right-segment-c4o2Tfs6mjdpip5yZhaO),
[Better Launch](https://www.betterlaunch.co/blog/indie-hacker). Treat as rough — this came from
blog posts, not proper data.*

**Meaning:** this is a long game. The thing that decides it isn't the code — it's finding people
who'll pay, early.

---

## Where things live

| File | What |
|---|---|
| `CLAUDE.md` | Instructions for Claude. Read if curious. |
| `.ideas/history.md` | What we've built and learned |
| `.ideas/decisions.md` | Decisions + why |
| `.ideas/routine-log.md` | Log of Claude's automatic overnight runs |

---

*Last updated: 2026-09-10*
