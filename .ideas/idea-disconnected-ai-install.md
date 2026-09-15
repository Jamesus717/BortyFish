# Idea: the AI stack that installs with the network cable pulled out

**Date:** 2026-09-15
**Whose:** Ollie's. He proposed airgapped installation as the answer to "we need a specific target
client base."
**Status:** best shape proposed so far. Mechanism adopted, **target market rejected** — see below.
**Related:** `direction-self-hosted-ai.md` (the direction), `idea-private-ai-in-a-box.md` (the
version this fixes).

---

## The idea as Ollie put it

> Go for secure AI users. Airgapped installation, provide a bunch of options and it chugs through
> so long as you provided all the files required for install. **Nothing sucks more from my own
> experience than trying to install something that absolutely requires an internet connection,
> it's awful.** But slap some kind of fancy math encode algorithm in front of a licensing system
> and they can copy + paste a key into it and wahey it's licensed.

**Why it's a step up on everything before it:** it fixes the flaw that killed
`idea-private-ai-in-a-box.md`. If the install runs on the client's own disconnected metal, their
data never leaves the building, we never become a GDPR data processor, and the legal wedge in
`direction-self-hosted-ai.md` — the one thing OpenAI and Anthropic can't compete on — actually
holds. It also answers James's complaint that broad AI is oversaturated: it names a segment.

---

## What's already built (checked 2026-09-15)

### The bundler exists and it's free

**Zarf** — open source, from **Defense Unicorns**, DoD-funded. Its own description is almost word
for word what Ollie proposed: *"the airgap native package manager for Kubernetes"*, bundling
container images, Helm charts, manifests, init scripts **and a local container registry** into a
single compressed file, installed with no connectivity. Tagline: *"develop connected, deploy
disconnected."* Built for classified networks, ships, remote sites.

**This is good news.** It removes months of the hardest work. The bundling was never going to be
the moat.

> **Use Zarf. Do not build a bundler.** Build the bundle that goes inside it.

### Accredited competitors already sell airgapped AI

**AirgapAI** and **Palantir AIP** are named as the easy-to-accredit options for disconnected
environments, precisely because they ship a fixed model set and an offline update bundle. In that
market **the certification is the product**, not the software.

*(One source claimed "65% of enterprise dev environments will mandate air-gapped LLM runtimes by
2026, up from 12% in 2023". That's a vendor blog. Treat as marketing until verified.)*

---

## Why the target market is wrong

True airgap means classified networks, defence, nuclear, hospitals, ships, finance with extreme
segmentation. **We already ruled this out on 2026-09-10**, in `direction-self-hosted-ai.md`:

> **Not** large regulated enterprises. Procurement, security reviews and credibility we don't have.

Airgap makes that wall taller, not shorter:

| Barrier | Why it bites two people with no track record |
|---|---|
| **Procurement** | Clearances or sponsorship, SBOMs, signed provenance, ISO 27001 / Cyber Essentials Plus, insurance, a named person who can be held liable |
| **They self-build** | An organisation paranoid enough to airgap will not run an unvetted binary from two strangers. They want source, provenance, and usually to build it themselves |
| **Accredited rivals** | AirgapAI, Palantir AIP, plus Red Hat and NVIDIA disconnected installs — all holding the paperwork that *is* the product here |
| **Model quality caps out** | Offline means local weights only, on whatever hardware they own. Fine for RAG and summarising, weak for agentic work |

---

## On the licensing system: park it

- We can only license **our own wrapper**. The OSS underneath stays OSS, and OpenWebUI still says
  "Open WebUI" above 50 end users (see `idea-private-ai-in-a-box.md`).
- **Offline keys cannot be revoked.** No phone-home means no kill switch. That is inherent, not a
  design problem waiting for a clever algorithm.
- Signed offline licence keys are a solved, well-documented pattern (Ed25519, node-locked). It is a
  library, not "fancy math" — and it gets cracked by anyone motivated.

**Nobody has ever failed because their licensing was too simple.** Build it when someone is paying.

---

## The reframe: keep the mechanism, drop the market

Ollie stated the real insight without noticing it was the bigger one:

> *Nothing sucks more than trying to install something that absolutely requires an internet
> connection.*

That is not an airgap problem, it is an **everywhere** problem. A law firm's server in a cupboard.
A factory floor. A GP surgery. A building site. A boat. Zarf's own positioning says *"offline and
semi-connected"* — because **semi-connected is the far larger market and it has no procurement
wall**.

So:

- **Keep the mechanism** — one file, no internet, chugs through, done.
- **Drop the target** — sell to the small UK firms already named in `direction-self-hosted-ai.md`
  (law, accountancy, recruitment, surveyors, healthcare practices), not to SCIFs.
- **Airgap becomes a credential, not a customer.** "It installs with the network cable pulled out"
  makes us sound serious to a solicitor. We never have to survive MoD procurement to prove it.

It also passes James's own test — *"something I'd actually wanna use as a developer"*. A one-file
private AI stack that installs anywhere with no internet is a thing we would both use. **First idea
in this run where both of us are the user and a plausible customer exists.**

---

## Next step

Build the bundle, don't research the market. One weekend, on Ollie's kit:

1. Zarf-package a minimal private AI stack — model runtime + weights + OpenWebUI + storage
2. Carry it to a machine with **no internet** and install it
3. See what breaks

If it installs clean on a disconnected box, we have something real to show a customer. If it
doesn't, we've learned the actual hard part in two days instead of two months.

**The unanswered question from 2026-09-10 still stands** and this doesn't replace it: *find one
firm that has said out loud "we'd use AI but we can't send client data to it."* Building the bundle
is worth doing anyway because it's a weekend, it's fun, and it's a demo. It is not a substitute for
that conversation.

---

## Sources

- Zarf: [zarf-dev/zarf](https://github.com/zarf-dev/zarf) ,
  [Defense Unicorns / UDS docs](https://docs.defenseunicorns.com/)
- Airgapped AI landscape: [iternal.ai airgap platform ranking](https://iternal.ai/best-ai-air-gapped-environments) ,
  [air-gapped LLM deployment guide](https://localaimaster.com/blog/air-gapped-ai-deployment)
- OpenWebUI branding clause: see `idea-private-ai-in-a-box.md`
