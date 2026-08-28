# Verification report

**Verdict: PASS**

| | |
|---|---|
| Report | `research/report.md` |
| Sources in ledger | 38 |
| Claims in ledger | 77 |
| Claims cited by the report | 57 |
| Hard failures | 0 |
| Warnings | 37 |

## Hard failures

None. Every cited claim resolves to a ledger row, binds an existing source,
and locates its evidence in a snapshot whose hash still matches.

## Warnings

Advisory. These do not block the report.

### W1 -- Claim in the ledger is never cited

- **claims.jsonl:58** -- claim c-058 is in the ledger but the report never cites it
  Anthropic prices cache operations on three separate multipliers: a 5-minute write at 1.25x base input, a 1-hour write at 2x, and a cache rea
- **claims.jsonl:59** -- claim c-059 is in the ledger but the report never cites it
  Anthropic documents the break-even point for caching explicitly: one cache read for the five-minute duration, two for the one-hour duration.
- **claims.jsonl:60** -- claim c-060 is in the ledger but the report never cites it
  Choosing where inference physically runs is itself a priced dimension: Anthropic applies a 1.1x multiplier across every token category for U
- **claims.jsonl:61** -- claim c-061 is in the ledger but the report never cites it
  Anthropic converts dollar-rated usage into a synthetic billing unit for cloud marketplaces, rating usage in USD and then converting to Claud
- **claims.jsonl:62** -- claim c-062 is in the ledger but the report never cites it
  Cache read discounts differ by vendor rather than converging: Amazon Bedrock prices cache reads at 75% below its on-demand input price.
- **claims.jsonl:63** -- claim c-063 is in the ledger but the report never cites it
  Amazon Bedrock offers batch inference at half the on-demand price for selected models, making latency tolerance a priced dimension.
- **claims.jsonl:64** -- claim c-064 is in the ledger but the report never cites it
  OpenRouter can filter providers on sustained measured throughput before applying a price sort, routing to the cheapest provider inside a qua
- **claims.jsonl:65** -- claim c-065 is in the ledger but the report never cites it
  Changing a model slug mid-conversation invalidates the sticky routing key, coupling a naming choice to cache economics.
- **claims.jsonl:66** -- claim c-066 is in the ledger but the report never cites it
  Cloudflare offers its AI Gateway's core features, including analytics, caching and rate limiting, at no charge on all plans.
- **claims.jsonl:67** -- claim c-067 is in the ledger but the report never cites it
  Portkey monetises the same gateway function as a flat monthly subscription with log quotas rather than as a share of spend.
- **claims.jsonl:68** -- claim c-068 is in the ledger but the report never cites it
  Portkey also offers a permanently free tier for non-production use.
- **claims.jsonl:69** -- claim c-069 is in the ledger but the report never cites it
  The same gateway function is monetised four incompatible ways across the market: a share of money loaded, no fee at all, a flat subscription
- **claims.jsonl:70** -- claim c-070 is in the ledger but the report never cites it
  FinCEN's 2011 final rule renamed 'stored value' as 'prepaid access' and deleted the terms 'issuer' and 'redeemer' of stored value.
- **claims.jsonl:71** -- claim c-071 is in the ledger but the report never cites it
  That rule imposed recordkeeping and suspicious activity reporting on providers and sellers of prepaid access, and a registration requirement
- **claims.jsonl:72** -- claim c-072 is in the ledger but the report never cites it
  The rule exempts lower-risk categories of prepaid access from certain requirements rather than regulating all prepaid value identically.
- **claims.jsonl:73** -- claim c-073 is in the ledger but the report never cites it
  FinCEN framed the 2011 rule as closing gaps opened by prepaid innovation over the preceding twelve years.
- **claims.jsonl:74** -- claim c-074 is in the ledger but the report never cites it
  The regulatory treatment of a prepaid balance turns on the closed-loop distinction, which the 2011 rule carries forward as a defined categor
- **claims.jsonl:75** -- claim c-075 is in the ledger but the report never cites it
  Stripe framed the difficulty as combinatorial rather than merely expensive, naming the matrix of model, task, speed and price as what makes
- **claims.jsonl:76** -- claim c-076 is in the ledger but the report never cites it
  A leaked letter from Stripe's founders to investors said the company had decided the singularity began on 1 January and was operating on tha
- **claims.jsonl:77** -- claim c-077 is in the ledger but the report never cites it
  The reporting treats that phrase as deliberately tongue-in-cheek rather than as a literal forecast.

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
