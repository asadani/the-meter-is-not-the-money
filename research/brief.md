# Research brief: Routing as the payment layer for AI

## Question

Does Stripe's acquisition of OpenRouter make sense as the purchase of a *metering
and settlement layer for AI compute* — and if so, is a common, provider-agnostic
token credit (the "buy me tokens" unit) a buildable product on top of it, or a
category error?

## Decision this feeds

Whether Anuj publishes the thesis "tokens are the new AI currency and the routing
layer is where that currency settles" as a written argument, and at what strength.
The research must be able to tell him which parts of the thesis are load-bearing
and evidenced, which are speculation he should label as such, and which are wrong.

## Sub-questions

1. **What actually happened.** Price, structure, date, acquirer's and target's own
   stated rationale, and where reported figures disagree.
2. **What Stripe bought.** What OpenRouter does mechanically — where it sits in the
   request path, what it meters, what it takes as a fee, what volume it carries,
   and which of those numbers are self-reported.
3. **Does routing actually sit on the money.** Is the router the place where usage
   becomes a billable quantity, or is it merely adjacent to it? Who else occupies
   that position (LiteLLM, Portkey, Cloudflare AI Gateway, Vercel AI Gateway,
   Bedrock, Requesty, Martian), and does anyone already charge like a payment rail?
4. **Is a common token credit unit feasible.** Do the underlying pricing primitives
   — input/output asymmetry, cache read vs cache write, reasoning tokens, batch
   discounts, per-provider variance on identical open weights — permit a stable
   single unit a payment layer could deduct from? What specifically breaks, and
   has anyone shipped this?
5. **Does the consumer patronage variant have legs.** "Buy me a coffee" → "buy me
   tokens/compute": is there precedent, and what is the economics and regulatory
   treatment of a prepaid, transferable, multi-vendor compute credit (stored
   value, breakage, float, money-transmission exposure)?
6. **The strongest case against.** Why $7-8B could be an overpay: router margin
   compression, disintermediation by model vendors, open-source substitution,
   and whether the strategic story is post-hoc.

## Out of scope

- **Which router or model is technically best.** No benchmark bake-off. The
  question is about position in the value chain, not quality.
- **How to build a router.** No architecture or implementation guidance.
- **Stripe's non-AI business.** Payments volume, Bridge/stablecoins, and Tempo
  only enter where they bear directly on the AI-metering thesis.
- **Antitrust and merger review.** Real, but a separate question.
- **Valuation modelling.** No DCF, no comparables table. "Was $8B the right price"
  is not answerable; "what would have to be true for it to be" is, and that is
  sub-question 6.
- **Agentic-commerce protocols** (ACP, AP2, x402) except where they are the
  settlement mechanism for the credit unit in sub-question 4-5.

## What a good answer looks like

A short argument with a clear verdict on the thesis, in which every factual
sentence is bound to a snapshot. Specifically it should be able to say:

- the deal facts, with the price disagreement attributed rather than averaged;
- whether OpenRouter's position is *on* the flow of funds or beside it, with
  evidence from its own pricing/terms rather than from commentary;
- a concrete list of the pricing primitives that make a universal credit hard,
  each one cited to a live vendor price page captured with an access date;
- at least one strong, captured source arguing the deal is an overpay or that
  routing is a commodity.

**What would change my mind:** if OpenRouter's published fee structure turns out
to be a flat platform fee unrelated to token volume, the "payment rail" framing
weakens sharply. If a provider-agnostic credit unit already ships in production
somewhere, the "new product" framing is wrong and it becomes a market-structure
question instead.

## Lens

`market`, with a recency override — deal facts must come from sources dated
2026-08-14 or later; pricing evidence must carry an access date. T1 here means
company disclosure, published price lists, and terms of service captured
directly. T4 includes the acquisition press release *as a statement of strategy*,
even though it is T1 as evidence that the deal happened.

## Known traps

From the lens: a market-size number every source repeats and none computed;
funding rounds read as traction; self-reported volume figures.

Specific to this question:

- **The announcement is not the reason.** Both parties have an interest in the
  strategic story being legible. Separate the fact of the deal from the rationale.
- **Reported price varies ($7B / $7.5B / $8B+).** Attribute, never average.
- **OpenRouter's own token-volume and model-count figures are self-reported** and
  should be tiered accordingly even when quoted by reputable press.
- **The user arrives with a thesis.** The corpus must include sources gathered by
  searching *against* it, not only for it — see sub-question 6.
- **Recency collision.** Anything about OpenRouter written before 2026-08-16
  describes an independent company; it can be evidence about the router market
  but not about the combined entity.
