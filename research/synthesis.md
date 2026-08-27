# Synthesis: Routing as the payment layer for AI

Worked from `claims.jsonl` (55 claims, all passing), not from memory of the sources.

---

## SQ1 — What actually happened

**Converged.** Stripe announced an agreement to acquire OpenRouter (c-001), and as of
the announcement the deal had not closed (c-002). Stripe disclosed no price (c-003).
OpenRouter had raised $113m at roughly $1.3bn less than three months earlier (c-008).

**Contested — and the disagreement is the finding.** Four different figures are in
print: Bloomberg's ">$7bn" (c-004), the New York Times' "~$7.5bn, $1.5bn to founders"
(c-005), Semafor's "$8bn" (c-006), and The Information's "$10bn" from the talks stage
(c-007, `mixed`).

*Why they differ:* they are not measuring the same thing at the same time. The $10bn
was a figure floated during negotiation in July; the $7–8bn figures are post-agreement
reporting from three different unnamed sources. None is a disclosure. The $7.5bn
figure is the only one that decomposes (headline vs. founder allocation), which is
weak evidence it is closest to a real term sheet — but that is inference, not evidence,
and the honest position is a range.

**Note for the user:** the $8bn figure in the original prompt is the *loosest* of the
four, not the consensus.

**Independence check:** TSG (s-007), CNBC (s-005) and PYMNTS (s-028) are three outlets
relaying three different primary reports (Bloomberg, NYT, The Information). That is
genuine independence at the reporting layer, though none of them saw the documents.

---

## SQ2 — What Stripe bought

**Converged, and this is the load-bearing section.** OpenRouter takes **no markup on
inference** and instead charges a fee **when credits are purchased** (c-012) — 5.5% on
the pay-as-you-go plan (c-013), with BYOK free to $25,000/month of list-price inference
and 5% above (c-014). Revenue was reported at roughly $140m annualised in mid-2026 by
two independent routes, PYMNTS-via-The-Information and Sacra (c-016).

**The structural point:** a percentage skimmed off money loaded onto a balance is the
shape of a payment processor's take, not a software licence. That is the strongest
mechanical support for the user's thesis, and it comes from OpenRouter's own price page
and FAQ (T1), not from commentary.

**The immediate complication:** OpenRouter's credit balance is denominated in **US
dollars** (c-015). The unit of account never became the token.

---

## SQ3 — Does routing sit on the money

**Converged.** Stripe was already metering AI tokens before this deal, via Token
Billing (c-017). Its billing stack already supports defining an abstract **"AI Credit"**,
converting each model's usage into that unit, and selling prepaid credit packs (c-018),
metered by model and token type including cached tokens (c-019). It is waitlisted, not
generally available (c-020).

**Contested (c-022, `mixed`).** OpenRouter charges 5.5%; Vercel's AI Gateway charges
**"no markup and no platform fee on tokens"** at all (c-021). Same function, opposite
price. *Why they differ:* Vercel monetises hosting and takes the gateway as a
retention feature; OpenRouter had no other product to monetise. This is not a
measurement discrepancy — it is two live business models, and it means the take rate
at this layer is a choice rather than a property of the position.

**Conclusion c-051 (`mixed`, moderate):** the routing fee is under competitive
pressure rather than established as a durable rent. Contradicting sources listed.

**Conclusion c-054 (moderate):** metering is not itself the moat — LiteLLM does
per-key/user/team spend tracking across 100+ models for free (c-023), and even it
documents that its numbers do not always reconcile with the provider's bill (c-031).

---

## SQ4 — Can a common token credit exist

**Converged, single-source-per-fact but all T1 vendor documentation.**

The pricing primitives are genuinely multi-dimensional:

- Default routing load-balances across providers **on price** (c-024), with the docs'
  own worked example spanning $1/$2/$3 per million tokens for the same model (c-025).
- Selection is probabilistic — inverse-square weighted — so an identical request has no
  fixed cost at submission time (c-026).
- Cache **writes** can cost *more* than ordinary input: 1.25x on recent OpenAI models
  (c-027). Cache **reads** are discounted 0.25x or 0.50x depending on model (c-028).
- The direction varies by provider: Anthropic carries a **negative** discount on cache
  writes and a positive one on reads (c-029).
- Routing and caching are economically coupled: sticky routing engages only when the
  provider's cache-read price beats its ordinary prompt price (c-030).

**Conclusion c-048 (moderate):** no fixed token price can be quoted before a request is
routed. This is an inference from a mechanism described in one source (OpenRouter's own
docs) — flagged as the most load-bearing single-source step in the project.

**Conclusion c-049 (high):** therefore a common credit unit can only ever be a
*per-model conversion*, never a direct count of tokens. Stripe's own product language
concedes this — it says "configure how usage of each model **converts** to credits."

**Conclusion c-050 (high):** the product the user proposes is already specified and
waitlisted at Stripe.

---

## SQ5 — The patronage variant  ⚠ weakest section

**Thin, and it should be reported as thin.**

Buy Me a Coffee charges 5% and pays creators directly to their bank (c-032), and
already processes payments **through Stripe** (c-033). So both legs of a "buy me
tokens" product already terminate at Stripe (c-055, moderate).

Existing giftable AI access is **plan-shaped, not balance-shaped**: Anthropic sells a
tier and a duration (c-034), expiring at 365 days (c-035). OpenRouter's own credits
also carry a one-year expiry (c-036, low — the numeral was absent from the
server-rendered snapshot and only the phrase survived).

**Conclusion c-053 (low).** The blocker is the shape of the loop, not the payment rail.
This rests partly on a **2003** FinCEN administrative ruling (c-037) which explicitly
says FinCEN "intends to engage in further rulemaking." Twenty-three years is not a
recency window anyone should accept for a regulatory claim.

**Checked and absent:** no source found showing a transferable, cross-vendor,
balance-denominated AI credit shipping anywhere.
**Not checked:** current CFPB Regulation E / prepaid-account treatment, state
money-transmitter licensing, EU e-money rules. Out of road, not out of scope.

---

## SQ6 — The case against

**Converged among skeptics.** At the floated price the multiple was roughly **70x
annualised revenue** (c-038), reported as high against comparable AI acquisitions on
forward revenue (c-039) — though OpenRouter's unit economics were genuinely strong at
28.5% cost of serving and ~70% gross margin (c-040).

Two competing readings of the strategic logic:

1. **Commoditisation-by-design** (c-041, c-042): routing is *meant* to become
   low-margin, because Stripe monetises billing, tax, fraud, stablecoin settlement and
   treasury around it.
2. **Expense management, not payments** (c-043): the move is to the other side of the
   ledger, and Databricks, Rippling and Ramp were already there (c-044).

**Conclusion c-052 (`mixed`, moderate):** the value plausibly sits *around* routing
rather than in it — which is explicitly not how Stripe framed the deal (c-010).
Contradicting source recorded.

Open-source self-hosting is named as direct pressure on willingness to pay (c-045).
OpenRouter asserts neutrality post-acquisition (c-046) — an assertion, not evidence.

---

## Overall answer to the brief

**Yes on the metering half; no on the currency half.**

The acquisition makes sense as buying a metering-and-settlement position: OpenRouter
already charges like a processor (c-012, c-013), Stripe already meters tokens (c-017),
and Stripe already ships the abstract credit unit (c-018). The user's structural
instinct is correct and is, almost verbatim, the acquirer's stated thesis — Collison
said "tokens are the central currency for companies building with AI" (c-009).

But the "token as currency" framing does not survive contact with the mechanism. Every
balance in the stack is denominated in dollars (c-047). Token prices are
multi-dimensional, provider-dependent, directionally inconsistent, and not fixed at
request time (c-026 through c-030). A credit unit is therefore a *conversion layer*
over dollars (c-049) — which is exactly what Stripe built (c-050).

**The token is the meter. The dollar is still the money. What Stripe bought is the
exchange desk.**

Confidence: **moderate.** The mechanism claims are high-confidence T1; the strategic
conclusions are contested by design (c-051, c-052); the patronage strand is low.

### What would change this

- If OpenRouter's fee were shown to be a flat platform fee unrelated to volume, the
  processor framing weakens. *Checked — it is 5.5% of credits purchased (c-013).*
- If a transferable cross-vendor credit shipped anywhere, the "new product" framing is
  wrong and this becomes a market-structure question. *Checked and absent.*
- **Single source that would most change the answer if withdrawn:** s-012, OpenRouter's
  provider-selection documentation. c-024, c-025, c-026 and conclusion c-048 all rest
  on it.
- **Strongest honest case against:** Semafor's (c-041, c-042). It accepts every fact
  above and concludes routing is the *loss leader*, not the rail. It is not refuted
  here, only recorded.

## Gaps

**Checked and absent** — no transferable cross-vendor AI credit in production; no
independent audit of OpenRouter's token-volume or model-count figures (all self-reported).

**Not checked** — modern prepaid/e-money regulation (SQ5); antitrust; valuation
modelling; router quality benchmarks. All excluded by the brief except the regulation,
which ran out of road.

**Unknowable from public sources** — the actual price and deal structure. Stripe
disclosed nothing (c-003); every figure is an unnamed source (c-007).

**Capture failures** — Bloomberg, NYT, The Information, WSJ, Axios and Forbes could not
be captured (paywall, 403, JS wall), so all four price figures reach this workspace
secondhand. Cloudflare and Portkey returned unusable pages, so competitor evidence for
SQ3 rests on Vercel and LiteLLM alone.
