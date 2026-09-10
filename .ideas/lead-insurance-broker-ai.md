# Lead: private AI for an insurance broker (Park Insurance)

**Date:** 2026-09-10
**Status:** strongest lead so far — the first one where we have a named, real firm with the exact
problem. Blocked on one question (see IP warning).

---

## Why this is different

Every previous lead died on the same thing: no access to a real customer with a real, stated pain.

This one starts with the customer. James named Park Insurance as an internal insurance broker with
lots of sensitive data that would like to use AI and can't. That is *precisely* the objection the
self-hosted direction exists to answer (`direction-self-hosted-ai.md`).

---

## ⚠️ IP WARNING — resolve this before writing a line of code

**If Park Insurance is James's employer, they may legally own anything he builds.**

Under UK law, inventions and software created by an employee in the course of their employment
generally belong to the employer — and using company time, company hardware or company data makes
that claim far stronger.

This can quietly destroy the business before it exists: build the thing, prove it works, then find
the employer owns it and can't be sold to.

**Before building anything:**
- Read the employment contract's IP and moonlighting clauses.
- If it's ambiguous, get written confirmation the side project is James's own.
- Build on Ollie's kit, on personal time, with synthetic or anonymised data until that's settled.
- Consider Park Insurance as the *first customer*, not the venue — a contract with them is much
  cleaner than an unclear internal project.

This is not legal advice. It's a flag, and it is worth an hour with an actual solicitor before
months of work.

---

## Why a broker is a genuinely good fit

Brokers are drowning in documents that AI is good at and cloud AI is barred from touching:

- Policy wordings and schedules (long, dense, comparison-heavy)
- Insurer quotes arriving as PDFs that need re-keying
- Claims correspondence and histories
- Renewal packs
- Client files containing personal, financial and sometimes medical data

The work is high-volume reading, comparing and extracting — the thing language models are actually
good at. And the data is exactly what can't be pasted into ChatGPT.

---

## Regulatory picture (better than expected)

- **The FCA has no AI-specific rules**, and is actively studying barriers to adoption rather than
  restricting it. AI sits under existing conduct, governance and resilience obligations.
- Compliance runs on two tracks: **FCA** (conduct, senior-manager accountability) and **data
  protection** (lawful, fair, transparent processing).
- The practical baseline for a regulated deployer in 2026: a documented AI inventory, a risk
  assessment per deployment, a named accountable senior manager, monitoring, and an incident
  response process.
- **Most current adoption is happening with no governance, audit trail or compliance review.**

Sources (search snippets, pages not fetched):
https://www.kennedyslaw.com/en/thought-leadership/article/2026/deploying-ai-in-financial-services-in-the-uk-fca-and-data-protection-considerations/ ,
https://www.pinsentmasons.com/out-law/guides/the-regulation-of-ai-in-uk-insurance-an-introductory-guide ,
https://aiforbrokers.co.uk/

**The commercial read:** that last point is the product. Brokers are already using AI unsafely.
"Self-hosted, your data never leaves, and it produces the audit trail your compliance officer
needs" is a far stronger pitch than "AI for brokers" alone. The governance wrapper isn't overhead —
it's the differentiator.

---

## Price anchor

AI document-processing tools in this space run roughly **£200–£500/month**, about £2–£5 per client
at ~50 new clients a month.
Source: https://www.insurancebook.co.uk/article/ai-tools-insurance-brokers-financial-services-2026
(snippet, not fetched)

Modest, but it's per-firm recurring revenue and there are thousands of UK brokers.

---

## Where Kubernetes earns its place

Same as `direction-self-hosted-ai.md`: multi-tenant isolation per broker, GPU scheduling across
tenants, scale-to-zero when idle, rolling updates without downtime. If this becomes multi-firm,
k8s is load-bearing rather than decoration.

For a single first deployment at one broker, it is over-engineering — but a deliberate one, since
learning it is an explicit goal and there's no deadline.

---

## Biggest reasons it fails

1. **The IP problem above.** Genuinely the largest risk, and the cheapest to check.
2. **One customer is not a market.** Park Insurance wanting it proves one firm wants it. Brokers
   buy through networks and BIBA; without a second and third firm this is a bespoke internal tool,
   not a business.
3. **Accuracy bar.** Getting a policy answer wrong in a regulated firm isn't an embarrassing bug,
   it's a compliance incident. The product must cite its sources and be auditable, not just fluent.

---

## Next steps, in order

1. **Settle the IP question.** Nothing else matters until this is clear.
2. **Find out what they'd actually do with it.** Ask which specific job is slow and manual today —
   comparing wordings, re-keying quotes, prepping renewals? Build for one job, not "AI".
3. **Ask whether a second broker has the same problem.** One firm is a favour; two is a market.
