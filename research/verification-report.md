# Verification report

**Verdict: PASS**

| | |
|---|---|
| Report | `.research/report.md` |
| Sources in ledger | 30 |
| Claims in ledger | 57 |
| Claims cited by the report | 57 |
| Hard failures | 0 |
| Warnings | 17 |

## Hard failures

None. Every cited claim resolves to a ledger row, binds an existing source,
and locates its evidence in a snapshot whose hash still matches.

## Warnings

Advisory. These do not block the report.

### W2 -- Assertion with no marker

- **report.md:3** -- unbound assertion (asserts something about a named entity)
  **What Stripe bought when it bought OpenRouter, and whether a common token credit can exist**
- **report.md:5** -- unbound assertion (asserts something about a named entity)
  Research question: does Stripe's acquisition of OpenRouter make sense as the purchase of a metering and settlement layer for AI compute —...
- **report.md:13** -- unbound assertion (asserts something about a named entity)
  **Yes on the metering half.
- **report.md:29** -- unbound assertion (asserts something about a named entity)
  What Stripe bought is the exchange desk.
- **report.md:41** -- unbound assertion (contains a figure)
  These are not competing measurements of one number — they are four unnamed sources at different moments in a negotiation, and none of the...
- **report.md:59** -- unbound assertion (asserts 'strongest')
  That is the strongest mechanical support for reading this as a payments acquisition, and it comes from OpenRouter's own price page and FA...
- **report.md:69** -- unbound assertion (asserts something about a named entity)
  Partly — and Stripe was already there without it.
- **report.md:84** -- unbound assertion (asserts something about a named entity)
  Nor is metering itself the moat.
- **report.md:91** -- unbound assertion (asserts something about a named entity)
  Only as a conversion.
- **report.md:110** -- unbound assertion (asserts something about a named entity)
  Which means the product in question is not speculative.
- **report.md:121** -- unbound assertion (asserts something about a named entity)
  What does not yet exist is a transferable balance.
- **report.md:150** -- unbound assertion (asserts something about a named entity)
  It records that Stripe's account and the analysts' account of the same transaction do not match, and that the analysts' version is the on...
- **report.md:166** -- unbound assertion (contains a figure)
  **The most load-bearing single source is OpenRouter's provider-selection documentation.** Claims c-024, c-025, c-026 and the conclusion c...
- **report.md:172** -- unbound assertion (contains a figure)
  **Section 5 is weak.** Two of its claims are low-confidence and one rests on a 2003 regulatory ruling.
- **report.md:174** -- unbound assertion (asserts something about a named entity)
  **Competitor coverage is narrow.** Cloudflare's and Portkey's pages returned no usable text, so the comparison rests on Vercel and LiteLL...
- **report.md:176** -- unbound assertion (asserts something about a named entity)
  **No independent claim-auditor pass was run.** Every quote was machine-verified against its snapshot, but no fresh-context agent independ...
- **report.md:180** -- unbound assertion (asserts something about a named entity)
  Deal terms are unknowable from public sources; OpenRouter's volume and model-count figures are self-reported and unaudited.

---

Rules are defined in `docs/LEDGER-SPEC.md` section 5.
