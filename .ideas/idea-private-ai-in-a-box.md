# Idea: private AI in a box — we install it and run it, they just use it

**Date:** 2026-09-15
**Status:** idea, straight off a Discord conversation. Not validated.
**Related:** this is a *delivery shape* for `direction-self-hosted-ai.md`, not a new direction.

---

## Where it came from

James saw a paid Meta ad for **Otto** (`myotto.ai`) — a presale box that runs OpenClaw agents,
set up from your phone, no terminal. His read:

> This is the kinda thing every company wants right now — a local AI, easy to use and set up. If we
> did the hosting and setting up for them, all they'd have to do is pay for the server space and AI
> tokens and ask the questions. We do the frontend, then a server usage bill.

Ollie's version of the same thing, minutes later:

> A guided model install onto a server, and a paid version of OpenWebUI. Use an open framework to
> load models onto a node, detect the OS from a couple of key indicators, host OpenWebUI with some
> customisations so it doesn't scream "we're running OpenWebUI and you could replicate this with a
> bit of time".

Both agreed OpenWebUI is the obvious frontend. Backend model/API source was left open — James
noted there's a GitHub repo listing all the free LLM APIs.

---

## What's actually true

Checked, not assumed. Confidence marked per row.

| Claim | Verdict | Confidence |
|---|---|---|
| **OpenClaw** is a real, free, self-hosted agent framework — runs 24/7 on your own hardware, model-agnostic (Claude/GPT/Gemini/local via Ollama), bridges Slack/WhatsApp/Telegram/Discord, proactive not just reactive | True | High — docs + multiple write-ups |
| **Otto** = presale hardware from *The Tokenry*: **from $599**, **$20 deposit**, ships with OpenClaw pre-installed, NFC phone pairing, **no monthly seat fee**, price rises at shipping | Probably true | **Low** — `myotto.ai` and `thetokenry.com` are both blocked by this session's egress proxy. Figures are search snippets, **no primary source** |
| Otto is crypto-adjacent | Likely | Medium — the related GitHub org ships OpenClaw "skills" billed via **x402 micropayments** for DeFi/market intel. Presale + deposit + token-ish branding = nothing shipped yet |
| **OpenWebUI can be rebranded** | **Only under 50 users** | High — licence read directly |
| Someone already sells Ollie's exact proposal | **Yes** | High |

### The OpenWebUI licence problem (this one matters)

Since **v0.6.6 (April 2025)** OpenWebUI is BSD-3-Clause **plus a branding clause**. Verbatim from
the licence: licensees are *"strictly prohibited from altering, removing, obscuring, or replacing
any 'Open WebUI' branding, including but not limited to the name, logo, or any visual, textual, or
symbolic identifiers"*.

Exemptions: total end users (*"individual natural persons with direct access to the application"*)
**does not exceed fifty (50) in any rolling thirty (30) day period**, or written permission, or an
enterprise licence (reported **~$5,000/yr for the first 50 users, then ~$3/user/month**).

**So Ollie's point 6 is fine at small scale and illegal at scale.** One deployment per client, each
a small UK firm under 50 staff → we can rebrand freely. The first tenant that passes 50 seats means
the branding goes back or we pay. Worth knowing *before* building a product whose selling point is
that it doesn't look like OpenWebUI.

### We'd have a competitor on day one

**Opsily** already sells managed OpenWebUI hosting: **from €14/month** (SSL, daily backups, managed
updates, hosted in Germany) and **white-label at $150/month flat**, with EU data residency and your
own SSO. That is Ollie's proposal, live, priced, and cheaper than we could be bothered to be.

### On the free-API repo

Those lists are real (several of them). But **free tiers are rate-limited and route client data
through someone else's logs on someone else's terms**. Unusable for anything sold on privacy. Fine
for our own prototyping, never for a client.

---

## The part that doesn't survive contact

- **"Local AI" and "we do the hosting" are opposites.** If it runs on Ollie's servers, the client's
  data has left their building. We're then just a cloud AI vendor — up against OpenAI on
  convenience and Opsily on price — as two people with no certifications, no insurance and no
  reference customers. That's the same race to zero that killed transcription in
  `direction-self-hosted-ai.md`.
- **Hosting their confidential data makes us a GDPR data processor.** A DPA per client, breach
  notification duty, ICO registration, PI/cyber cover. Real liability, all of it before revenue.
- **The frontend is not the moat.** OpenWebUI is free, good, and already white-labelled by people
  charging $150/month. Nobody pays for a skin.

## The part worth keeping

Same mechanism, flip whose hardware it runs on:

- **Sell install + operation on the client's own kit** (or a box we ship them, Otto-style). Data
  never leaves, the legal wedge from the direction file holds, and we're not a data processor.
- **Setup fee + monthly retainer** for patching, backups and keeping it alive. That's a services
  business, not SaaS — lower ceiling, but it's the one where **Ollie's ops skill is the product**
  and where two unknowns can actually be credible.
- The repeatable asset is **the installer** — Ollie's "detect the OS, load the model, stand up the
  frontend" script. Build it by doing the first install by hand, then automate only what repeats.

---

## Verdict

**The instinct is right, the delivery model as described is wrong.** Demand for private, easy AI is
real — Otto raising presales and Opsily charging monthly are both evidence. But we'd be hosting,
and hosting is the one version of this we can't win or safely insure.

**No new research needed.** This is `direction-self-hosted-ai.md` found again through a different
door, and that file's next test is still the same one written on **2026-09-10** and untouched for
five days:

> Find one firm that has said out loud: "we'd use AI but we can't send client data to it."

Ollie's IT contacts, one conversation. Choosing a frontend or writing an installer before that
happens is procrastination with a keyboard. **Don't write a line of it until someone has said the
sentence.**

## Park until there's a client

- OpenWebUI vs alternatives — irrelevant until someone is paying. Don't burn an evening comparing.
- Ship hardware vs install on their server. **Otto's presale is that market's test — watch whether
  it actually ships**, and at what price, before betting on a box.

---

## Sources

- OpenClaw: [docs.openclaw.ai](https://docs.openclaw.ai/) ,
  [Milvus write-up](https://milvus.io/blog/openclaw-formerly-clawdbot-moltbot-explained-a-complete-guide-to-the-autonomous-ai-agent.md)
- Otto (snippets only, both domains egress-blocked): [myotto.ai/presale](https://myotto.ai/presale) ,
  [thetokenry.com](https://thetokenry.com/) ,
  [useOttoAI/openclaw-skills](https://github.com/useOttoAI/openclaw-skills)
- OpenWebUI licence (read directly):
  [github.com/open-webui/open-webui/blob/main/LICENSE](https://github.com/open-webui/open-webui/blob/main/LICENSE) ,
  [docs.openwebui.com/license](https://docs.openwebui.com/license/)
- Opsily pricing: [white-label](https://opsily.com/hosting/open-webui/white-label-ai) ,
  [hosting](https://opsily.com/hosting/open-webui/open-webui-hosting) ,
  [enterprise licence](https://opsily.com/hosting/open-webui/open-webui-enterprise-license)
- Free LLM API lists: [awesome-free-llm-apis](https://github.com/amardeeplakshkar/awesome-free-llm-apis) ,
  [awesome-freellm-apis](https://github.com/open-free-llm-api/awesome-freellm-apis)
