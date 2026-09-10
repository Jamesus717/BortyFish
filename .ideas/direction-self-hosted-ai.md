# Direction: self-hosted AI for people whose data can't leave

**Date:** 2026-09-10
**Status:** the most promising fit for what we actually have. Not yet validated.

---

## Why this shape, not the others

We have three assets most people building this don't:

1. **Ollie's servers + some GPU resource** — multiple machines available for use, already paid for
2. **Ollie's ops skill** — **IT infrastructure**, **k8s cluster admin**, **Linux sysadmin** — the ops most solo builders can't do
3. **No time pressure** — we can take the slow, hard route

The single biggest barrier to self-hosting AI is hardware: **$10,000–$15,000** before you start.
We've already skipped it.
Source: https://petronellatech.com/blog/private-ai-deployment-guide-enterprise/ (search snippet)

---

## The opening

For some organisations, self-hosting isn't a preference — it's **a legal requirement**. GDPR, HIPAA,
ITAR and financial-services rules all rule out sending data to a cloud API.

That matters commercially: it's the one AI niche where **OpenAI and Anthropic cannot compete**,
because they're excluded by law rather than by price. Everywhere else, we'd be racing giants to
zero (see the transcription kill below).

Sources: https://developer.meta.com/ai/docs/deployment/regulated-industry-self-hosting/ ,
https://predictionguard.com/blog/best-self-hosted-ai-models-regulated-industries (snippets)

---

## Where Kubernetes is genuinely needed (not decoration)

This is the honest test — most small products don't need k8s. This one does:

- **Multi-tenant isolation.** Each client's data and model must be walled off. Namespaces, network
  policies and per-tenant storage are exactly the problem k8s solves.
- **GPU scheduling.** Several tenants, finite GPUs — something must queue and allocate them.
- **Scale to zero.** A tenant's model shouldn't hold a GPU while idle.
- **Rolling updates.** Model or service updates without dropping a client's service.

If we build this, k8s isn't a learning detour bolted on — it's load-bearing.

---

## Who to aim at

**Not** large regulated enterprises. Procurement, security reviews and credibility we don't have.

**Instead:** small UK firms handling confidential client data who want AI over their own documents
and cannot paste it into ChatGPT. Law firms, accountants, recruiters handling CVs, healthcare
practices, surveyors. Small enough to sell to without procurement; regulated enough that "your data
never leaves your control" is the entire pitch.

---

## Biggest reason it fails

**Trust.** We'd be asking a firm to hand confidential data to two people with no track record, no
certifications, no insurance and no reference customers. The technology is the easy part; being
credible enough to be allowed near the data is not.

Mitigation is slow and unglamorous: one friendly first customer, then a reference, then Cyber
Essentials / ISO-style paperwork. Ollie's IT background helps. Nothing else shortcuts it.

**Second risk:** open-source models keep getting good enough to run on a laptop. Some of this
market may self-serve before we reach it.

---

## Killed on the way here

### Transcription / speech-to-text — DEAD
Already commoditised and racing to zero:
- OpenAI Whisper API: **$0.006/min ($0.36/hr)**; GPT-4o Mini Transcribe **$0.18/hr**
- AssemblyAI batch: **~$0.21/hr**
- Deepgram Nova-3: **$0.0043/min**

Sources: https://www.assemblyai.com/blog/speech-to-text-api-pricing ,
https://brasstranscripts.com/blog/deepgram-pricing-per-minute-2025-real-time-vs-batch (snippets)

Free compute can't be a wedge when the incumbent charges 18p an hour. There is no margin left to
undercut. **Do not build transcription.**

---

## Next test

Nothing to build yet. The question to answer first:

**Find one firm that has said out loud "we'd use AI but we can't send client data to it."**

Ollie's IT contacts are the fastest route — he'll already know firms with that exact objection.
One real conversation beats another week of research.
