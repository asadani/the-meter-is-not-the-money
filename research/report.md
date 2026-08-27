# The meter is not the money

**What Stripe bought when it bought OpenRouter, and whether a common token credit can exist**

Research question: does Stripe's acquisition of OpenRouter make sense as the purchase of a
metering and settlement layer for AI compute — and is a provider-agnostic token credit
buildable on top of it, or a category error?

---

## The answer

**Yes on the metering half. No on the currency half.**

The structural instinct is right, and it is almost verbatim the acquirer's own thesis:
Patrick Collison framed tokens as "the central currency for companies building with
AI"[^c-009]. OpenRouter already charges like a payment processor rather than a software
vendor — it applies no markup to inference and instead takes a fee when a customer loads
credits[^c-012], 5.5% on its pay-as-you-go plan[^c-013]. Stripe was already metering AI
tokens before the deal[^c-017], and already ships the abstract credit unit this question
is about[^c-018].

But the "token as currency" framing does not survive contact with the mechanism. Every
balance in the stack is denominated in dollars[^c-047]. Token prices are
multi-dimensional, provider-dependent, inconsistent in direction, and not fixed at the
moment a request is submitted[^c-048]. A common credit can therefore only ever be a
per-model *conversion*, never a count of tokens[^c-049].

The token is the meter. The dollar is still the money. What Stripe bought is the
exchange desk.

---

## 1. What actually happened

Stripe announced on 19 August 2026 that it had agreed to acquire OpenRouter, an AI model
gateway and routing platform[^c-001]. The deal had not closed at announcement and remained
subject to customary closing conditions[^c-002]. Less than three months earlier OpenRouter
had raised $113 million at a valuation of about $1.3 billion[^c-008].

Stripe disclosed no price[^c-003], and the published figures disagree with each other:
Bloomberg reported more than $7 billion[^c-004], the New York Times about $7.5 billion with
$1.5 billion allocated to founders[^c-005], and Semafor $8 billion[^c-006]. An earlier
report from the talks stage put it at $10 billion[^c-007]. These are not competing
measurements of one number — they are four unnamed sources at different moments in a
negotiation, and none of them is a disclosure. **The $8 billion figure is the loosest of the
four, not the consensus.** Use a range and attribute it.

## 2. What Stripe actually bought

OpenRouter routes token usage across more than 400 models from more than 80 providers, on
Stripe's own description[^c-011] — a self-reported figure, unaudited.

The commercially interesting fact is the shape of the take. OpenRouter applies no markup to
inference and charges instead when credits are purchased[^c-012]: 5.5% on pay-as-you-go[^c-013],
with bring-your-own-key usage free to $25,000 of list-price inference per month and 5%
above that[^c-014]. Reported revenue was roughly $140 million annualised in mid-2026[^c-016].

A percentage skimmed off money loaded onto a balance is the shape of a processor's take
rate, not a licence fee. That is the strongest mechanical support for reading this as a
payments acquisition, and it comes from OpenRouter's own price page and FAQ rather than
from commentary.

And immediately: **OpenRouter's credit balance is denominated in US dollars, not
tokens**[^c-015].

## 3. Does routing sit on the money?

Partly — and Stripe was already there without it.

Stripe had been metering and billing AI token usage before this deal, through products
including Token Billing[^c-017]. Its billing stack already supports defining an abstract
"AI Credit", converting each model's usage into that unit, and selling prepaid credit
packs customers can top up[^c-018], metered by model and by token type including cached
tokens[^c-019]. It is not generally available; access sits behind a waiting list[^c-020].

The take rate at this layer, however, is contested rather than settled[^c-022]. Vercel's AI
Gateway charges no markup and no platform fee on tokens at all[^c-021] — the same function
at the opposite price. This is not two measurements of one number but two live prices, so
the fee reads as a choice rather than a property of the position, and it is under
competitive pressure rather than established as durable rent[^c-051]. *Why* the two firms
price it differently was not established by this research.

Nor is metering itself the moat. Per-key, per-user and per-team spend tracking across
100+ models ships as free open-source software[^c-023], and even that software documents
that its numbers do not reliably reconcile with the provider's bill[^c-031] — so the
capability is commodity and the hard part is accuracy, not access[^c-054].

## 4. Can a common token credit exist?

Not as a token count. Only as a conversion. The pricing primitives make this concrete, and
every fact below comes from vendor documentation:

- OpenRouter's default behaviour load-balances requests across providers on price[^c-024],
  and its own worked example spans $1, $2 and $3 per million tokens for the same
  model[^c-025].
- Selection is probabilistic — inverse-square weighted by price — so the cost of an
  identical request is not fixed when it is submitted[^c-026].
- Cache **writes** can cost *more* than ordinary input: 1.25x on recent OpenAI models[^c-027].
- Cache **reads** are discounted at 0.25x or 0.50x depending on the model[^c-028].
- The direction is provider-dependent: some providers carry a *negative* discount on cache
  writes and a positive one on reads[^c-029].
- Routing and caching are economically coupled — sticky routing engages only when a
  provider's cache-read price beats its ordinary prompt price[^c-030].

A unit of account cannot be nondeterministic at the point of sale. That is why the credit
stays in dollars, and why Stripe's own product language concedes the point: it says
configure how usage of each model *converts* to credits[^c-049].

Which means the product in question is not speculative. It is already specified at Stripe
and waiting to ship[^c-050].

## 5. The "buy me tokens" variant

This is the thinnest part of the research and should be read as provisional.

Buy Me a Coffee charges a 5% transaction fee and pays creators directly to their bank
account[^c-032], and already processes payments through Stripe[^c-033]. So both legs of a
compute-denominated patronage product already terminate at Stripe[^c-055].

What does not yet exist is a transferable balance. Giftable AI access ships today in
plan-shaped form — Anthropic sells a tier and a duration[^c-034] that expires 365 days
after purchase[^c-035] — not as a spendable, portable credit. OpenRouter's own credits
also carry a one-year expiry[^c-036], though that claim is low-confidence: the numeral was
absent from the captured page and only the surrounding phrase survived.

The obstacle is the shape of the loop rather than the payment rail[^c-053]. FinCEN has
stated it does not currently interpret "stored value" to include closed-system products
such as a mall-wide gift card programme[^c-037] — and a credit spendable across many AI
vendors is precisely not a closed system. **That rests on FinCEN Ruling 2003-4, issued in
August 2003**[^c-056], **which itself says FinCEN intends further rulemaking on the
definition of stored value**[^c-057]. It is a signpost, not a legal position, and anyone
building this needs current advice.

## 6. The case against

At the price floated during talks, Stripe would have been paying roughly 70 times
OpenRouter's annualised revenue[^c-038], reported as high against comparable AI
acquisitions on a forward-revenue basis[^c-039] — although OpenRouter's unit economics
were genuinely strong, at 28.5% cost of serving and roughly 70% gross margin[^c-040].

The strongest counter-reading accepts every fact in this report and inverts the
conclusion: OpenRouter's business may be destined for commoditisation, and that is the
point[^c-041] — Stripe can afford routing to be low-margin because it monetises billing,
tax, fraud, stablecoin settlement and treasury around it[^c-042]. On a second reading the
deal is expense management rather than payments[^c-043], a field Databricks, Rippling and
Ramp had already entered[^c-044]. Self-hostable open-source routing presses directly on
willingness to pay for standalone routing[^c-045].

These readings are contested against Stripe's own framing of the deal[^c-052], which
described it as helping businesses route requests and spend tokens efficiently to maximise
profitability[^c-010]. This report does not resolve that disagreement. It records that
Stripe's account and the analysts' account of the same transaction do not match, and that
the analysts' version is the one that survives if routing margin goes to zero.

OpenRouter states its routing decisions will remain driven by user interest rather than by
its parent[^c-046]. That is an assertion, and it is worth treating as one.

---

## Limitations

- **48 of 57 claims rest on a single source.** Much of that is legitimate — a vendor's
  price page is the only source for its own price — but the corpus corroborates less than
  the claim count suggests.
- **The most load-bearing single source is OpenRouter's provider-selection
  documentation.** Claims c-024, c-025, c-026 and the conclusion c-048 all rest on it. If
  it is wrong or has since changed, section 4 weakens.
- **All four price figures reach this report secondhand.** Bloomberg, the NYT, The
  Information, the WSJ, Axios and Forbes could not be captured — paywalls, 403s and
  JavaScript walls — so the primary reporting was never read directly.
- **Section 5 is weak.** Two of its claims are low-confidence and one rests on a 2003
  regulatory ruling. Modern prepaid/e-money regulation was not researched.
- **Competitor coverage is narrow.** Cloudflare's and Portkey's pages returned no usable
  text, so the comparison rests on Vercel and LiteLLM alone.
- **No independent claim-auditor pass was run.** Every quote was machine-verified against
  its snapshot, but no fresh-context agent independently judged whether the passages
  support the statements. Two statements were tightened by hand after review for drifting
  wider than their evidence.
- Deal terms are unknowable from public sources; OpenRouter's volume and model-count
  figures are self-reported and unaudited.

## References

[^c-001]: Stripe announced on 19 August 2026 that it had agreed to acquire OpenRouter, an AI model gateway and routing platform.
    — *Stripe agrees to acquire OpenRouter to help businesses optimize token routing and usage*, Stripe, 2026-08-19. <https://stripe.com/newsroom/news/stripe-agrees-to-acquire-openrouter> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-002]: As of the announcement the acquisition had not closed; it remained subject to customary closing conditions, with closing expected within weeks.
    — *OpenRouter is Joining Stripe*, OpenRouter, 2026-08-19. <https://openrouter.ai/blog/announcements/openrouter-is-joining-stripe/> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-003]: Stripe did not disclose the price it agreed to pay for OpenRouter.
    — *Stripe to buy OpenRouter as fintech expands deeper into AI*, CNBC, 2026-08-19. <https://www.cnbc.com/2026/08/19/stripe-openrouter-fintech-ai-model-marketplace-.html> (accessed 2026-08-26) [T3]
    _confidence: high_

[^c-004]: Bloomberg reported the price as more than $7 billion.
    — *Stripe Acquires OpenRouter for 7B+, Turning Model Routing Into a Payments Infrastructure Problem*, TSG (The Strawhecker Group), 2026-08. <https://tsgpayments.com/stripe-acquires-openrouter-for-7b-turning-model-routing-into-a-payments-infrastructure-problem/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-005]: The New York Times reported the price as about $7.5 billion, of which $1.5 billion was allocated to OpenRouter's founders.
    — *Stripe to buy OpenRouter as fintech expands deeper into AI*, CNBC, 2026-08-19. <https://www.cnbc.com/2026/08/19/stripe-openrouter-fintech-ai-model-marketplace-.html> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-006]: Semafor reported the price as $8 billion.
    — *Stripe agrees to acquire OpenRouter for $8 billion*, Semafor, 2026-08-21. <https://www.semafor.com/article/08/21/2026/stripe-agrees-to-acquires-openrouter> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-007]: The reported purchase price is contested: published figures range from more than $7 billion to $8 billion, and an earlier report of the talks put the figure at $10 billion.
    — *Stripe Acquires OpenRouter for 7B+, Turning Model Routing Into a Payments Infrastructure Problem*, TSG (The Strawhecker Group), 2026-08. <https://tsgpayments.com/stripe-acquires-openrouter-for-7b-turning-model-routing-into-a-payments-infrastructure-problem/> (accessed 2026-08-26) [T3]
    — *Stripe to buy OpenRouter as fintech expands deeper into AI*, CNBC, 2026-08-19. <https://www.cnbc.com/2026/08/19/stripe-openrouter-fintech-ai-model-marketplace-.html> (accessed 2026-08-26) [T3]
    — *Stripe agrees to acquire OpenRouter for $8 billion*, Semafor, 2026-08-21. <https://www.semafor.com/article/08/21/2026/stripe-agrees-to-acquires-openrouter> (accessed 2026-08-26) [T3]
    — *Stripe's OpenRouter Bid 70 Times Company's Annual Revenue*, PYMNTS, 2026-08. <https://www.pymnts.com/news/artificial-intelligence/2026/stripe-openrouter-bid-70-times-annual-revenue/> (accessed 2026-08-26) [T3]
    _confidence: high; stance: mixed (contested by s-005, s-025, s-028)_

[^c-008]: Less than three months before the acquisition, OpenRouter had raised $113 million at a valuation of about $1.3 billion.
    — *Stripe to buy OpenRouter as fintech expands deeper into AI*, CNBC, 2026-08-19. <https://www.cnbc.com/2026/08/19/stripe-openrouter-fintech-ai-model-marketplace-.html> (accessed 2026-08-26) [T3]
    _confidence: high_

[^c-009]: Stripe's CEO Patrick Collison publicly framed tokens as the central currency for companies building with AI.
    — *Stripe agrees to acquire OpenRouter to help businesses optimize token routing and usage*, Stripe, 2026-08-19. <https://stripe.com/newsroom/news/stripe-agrees-to-acquire-openrouter> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-010]: Stripe framed the acquisition as helping businesses route requests and spend tokens efficiently in order to maximise profitability.
    — *Stripe agrees to acquire OpenRouter to help businesses optimize token routing and usage*, Stripe, 2026-08-19. <https://stripe.com/newsroom/news/stripe-agrees-to-acquire-openrouter> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-011]: OpenRouter routes token usage across more than 400 models from more than 80 providers, on Stripe's own description of the company.
    — *Stripe agrees to acquire OpenRouter to help businesses optimize token routing and usage*, Stripe, 2026-08-19. <https://stripe.com/newsroom/news/stripe-agrees-to-acquire-openrouter> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-012]: OpenRouter applies no markup to inference pricing and instead charges a fee when a customer purchases credits.
    — *OpenRouter FAQ (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/faq> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-013]: OpenRouter's published platform fee on its pay-as-you-go plan is 5.5%.
    — *OpenRouter Pricing (plans page)*, OpenRouter, n.d.. <https://openrouter.ai/pricing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-014]: On OpenRouter's pay-as-you-go plan, bring-your-own-key usage is free up to $25,000 of list-price inference per month and carries a 5% fee above that.
    — *OpenRouter Pricing (plans page)*, OpenRouter, n.d.. <https://openrouter.ai/pricing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-015]: OpenRouter's credit balance is denominated in US dollars, not in tokens.
    — *OpenRouter FAQ (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/faq> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-016]: OpenRouter was reported to be generating roughly $140 million in annualised revenue as of mid-2026.
    — *Stripe's OpenRouter Bid 70 Times Company's Annual Revenue*, PYMNTS, 2026-08. <https://www.pymnts.com/news/artificial-intelligence/2026/stripe-openrouter-bid-70-times-annual-revenue/> (accessed 2026-08-26) [T3]
    — *OpenRouter revenue, valuation & funding*, Sacra, 2026. <https://sacra.com/c/openrouter/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-017]: Stripe was already metering and billing AI token usage before the OpenRouter deal, through products including Token Billing.
    — *Stripe agrees to acquire OpenRouter to help businesses optimize token routing and usage*, Stripe, 2026-08-19. <https://stripe.com/newsroom/news/stripe-agrees-to-acquire-openrouter> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-018]: Stripe's token billing product already supports defining an abstract 'AI Credit', converting each model's usage into that unit, and selling prepaid credit packs.
    — *Token Billing (Stripe Docs)*, Stripe, n.d.. <https://docs.stripe.com/billing/token-billing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-019]: Stripe's LLM token billing product meters usage segmented by model and by token type, including cached tokens.
    — *Token Billing (Stripe Docs)*, Stripe, n.d.. <https://docs.stripe.com/billing/token-billing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-020]: Stripe's LLM token billing product is not generally available; access is gated behind a waiting list.
    — *Token Billing (Stripe Docs)*, Stripe, n.d.. <https://docs.stripe.com/billing/token-billing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-021]: A competing gateway, Vercel's AI Gateway, charges no markup and no platform fee on tokens at all.
    — *Vercel AI Gateway pricing*, Vercel, n.d.. <https://vercel.com/docs/ai-gateway/pricing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-022]: The take rate at the routing layer is contested rather than settled: OpenRouter charges a 5.5% platform fee while Vercel charges zero markup and zero platform fee for the same function.
    — *OpenRouter Pricing (plans page)*, OpenRouter, n.d.. <https://openrouter.ai/pricing> (accessed 2026-08-26) [T1]
    — *Vercel AI Gateway pricing*, Vercel, n.d.. <https://vercel.com/docs/ai-gateway/pricing> (accessed 2026-08-26) [T1]
    _confidence: high; stance: mixed (contested by s-015)_

[^c-023]: Per-key, per-user and per-team spend tracking across many models is available as free open-source software.
    — *LiteLLM Proxy cost tracking (docs)*, LiteLLM (BerriAI), n.d.. <https://docs.litellm.ai/docs/proxy/cost_tracking> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-024]: OpenRouter's default routing behaviour load-balances requests across providers on price rather than pinning a single provider.
    — *OpenRouter Provider Selection (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/routing/provider-selection> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-025]: Providers serving the same model can differ in price by a factor of three, and OpenRouter's own documentation uses exactly such a spread as its worked example.
    — *OpenRouter Provider Selection (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/routing/provider-selection> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-026]: Because provider selection is probabilistic, the cost of an identical request is not fixed at the moment it is submitted.
    — *OpenRouter Provider Selection (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/routing/provider-selection> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-027]: Writing to the prompt cache can cost more than ordinary input tokens: on recent OpenAI models cache writes are charged at 1.25x the input price.
    — *OpenRouter Prompt Caching (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/best-practices/prompt-caching> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-028]: Cache reads are discounted at a rate that varies by model, charged at 0.25x or 0.50x the original input price.
    — *OpenRouter Prompt Caching (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/best-practices/prompt-caching> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-029]: Cache pricing direction is provider-dependent: some providers apply a negative discount on cache writes and a positive one on cache reads.
    — *OpenRouter Prompt Caching (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/best-practices/prompt-caching> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-030]: Routing and caching are coupled economically: OpenRouter pins a session to a provider only when that provider's cache read price beats its ordinary prompt price.
    — *OpenRouter Prompt Caching (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/best-practices/prompt-caching> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-031]: Reconciling a gateway's metered cost against the upstream provider's bill is a recognised failure mode with its own documented debugging procedure.
    — *LiteLLM Proxy cost tracking (docs)*, LiteLLM (BerriAI), n.d.. <https://docs.litellm.ai/docs/proxy/cost_tracking> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-032]: Buy Me a Coffee charges a 5% transaction fee and pays creators directly to their bank account.
    — *Buy Me a Coffee FAQ*, Buy Me a Coffee, n.d.. <https://buymeacoffee.com/faq> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-033]: The incumbent patronage product already runs on Stripe for payment processing.
    — *Buy Me a Coffee FAQ*, Buy Me a Coffee, n.d.. <https://buymeacoffee.com/faq> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-034]: Anthropic's giftable AI access is sold as a plan of fixed tier and duration, not as a spendable balance.
    — *How to gift a Claude subscription*, Anthropic, n.d.. <https://support.claude.com/en/articles/12938627-how-to-gift-a-claude-subscription> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-035]: Vendor-gifted AI access carries an expiry: Anthropic's gift subscriptions expire 365 days after purchase.
    — *How to gift a Claude subscription*, Anthropic, n.d.. <https://support.claude.com/en/articles/12938627-how-to-gift-a-claude-subscription> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-036]: Unused OpenRouter credits are subject to expiry after one year.
    — *OpenRouter FAQ (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/faq> (accessed 2026-08-26) [T1]
    _confidence: low_

[^c-037]: FinCEN has stated it does not currently interpret 'stored value' to include closed-system products such as a mall-wide gift card programme.
    — *Definition of Money Transmitter - Stored Value / Gift Cards (administrative ruling)*, FinCEN, U.S. Department of the Treasury, 2003-08-15. <https://fincen.gov/resources/statutes-regulations/administrative-rulings/definition-money-transmitterstored-value-gift> (accessed 2026-08-26) [T1]
    _confidence: low_

[^c-038]: At the price floated during the talks, Stripe would have been paying roughly 70 times OpenRouter's annualised revenue.
    — *Stripe's OpenRouter Bid 70 Times Company's Annual Revenue*, PYMNTS, 2026-08. <https://www.pymnts.com/news/artificial-intelligence/2026/stripe-openrouter-bid-70-times-annual-revenue/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-039]: That multiple was reported as high relative to other AI acquisitions measured on forward revenue.
    — *Stripe's OpenRouter Bid 70 Times Company's Annual Revenue*, PYMNTS, 2026-08. <https://www.pymnts.com/news/artificial-intelligence/2026/stripe-openrouter-bid-70-times-annual-revenue/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-040]: OpenRouter's reported unit economics were strong, with cost of serving at 28.5% of revenue and roughly 70% gross margin.
    — *Stripe's OpenRouter Bid 70 Times Company's Annual Revenue*, PYMNTS, 2026-08. <https://www.pymnts.com/news/artificial-intelligence/2026/stripe-openrouter-bid-70-times-annual-revenue/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-041]: One reading of the deal is that routing itself is heading for commoditisation, and that this is the point rather than a problem.
    — *Stripe agrees to acquire OpenRouter for $8 billion*, Semafor, 2026-08-21. <https://www.semafor.com/article/08/21/2026/stripe-agrees-to-acquires-openrouter> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-042]: On that reading the value sits in what surrounds routing - billing, tax, fraud, settlement, treasury and financing - not in the routing margin itself.
    — *Stripe agrees to acquire OpenRouter for $8 billion*, Semafor, 2026-08-21. <https://www.semafor.com/article/08/21/2026/stripe-agrees-to-acquires-openrouter> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-043]: A competing reading is that the deal is an expense-management move rather than a payments move.
    — *Stripe didn't really buy OpenRouter because of the singularity*, TechCrunch, 2026-08-19. <https://techcrunch.com/2026/08/19/stripe-didnt-really-buy-openrouter-because-of-the-singularity/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-044]: Several other firms had already entered token expense management before the deal, including Databricks, Rippling and Ramp.
    — *Stripe didn't really buy OpenRouter because of the singularity*, TechCrunch, 2026-08-19. <https://techcrunch.com/2026/08/19/stripe-didnt-really-buy-openrouter-because-of-the-singularity/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-045]: Self-hostable open-source routing is named as a direct pressure on willingness to pay for standalone routing.
    — *OpenRouter revenue, valuation & funding*, Sacra, 2026. <https://sacra.com/c/openrouter/> (accessed 2026-08-26) [T3]
    _confidence: moderate_

[^c-046]: OpenRouter states that its routing decisions will continue to be driven by user interest rather than by its new parent company.
    — *OpenRouter is Joining Stripe*, OpenRouter, 2026-08-19. <https://openrouter.ai/blog/announcements/openrouter-is-joining-stripe/> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-047]: The routing layer's own balances are denominated in dollars rather than in tokens: OpenRouter's credit base currency is US dollars and Vercel bills credits against the provider's list price.
    — *OpenRouter FAQ (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/faq> (accessed 2026-08-26) [T1]
    — *Vercel AI Gateway pricing*, Vercel, n.d.. <https://vercel.com/docs/ai-gateway/pricing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-048]: Under price-based load balancing across providers of differing cost, no fixed token price can be quoted for a request before it is routed.
    — *OpenRouter Provider Selection (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/routing/provider-selection> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-049]: A common credit unit can only be a per-model conversion rather than a direct count of tokens, because token prices are multi-dimensional and vary in direction by provider.
    — *Token Billing (Stripe Docs)*, Stripe, n.d.. <https://docs.stripe.com/billing/token-billing> (accessed 2026-08-26) [T1]
    — *OpenRouter Prompt Caching (docs)*, OpenRouter, n.d.. <https://openrouter.ai/docs/guides/best-practices/prompt-caching> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-050]: The provider-agnostic prepaid AI credit is already specified as a Stripe product but is not yet generally available.
    — *Token Billing (Stripe Docs)*, Stripe, n.d.. <https://docs.stripe.com/billing/token-billing> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-051]: The fee charged at the routing layer is under competitive pressure rather than established as a durable rent.
    — *OpenRouter Pricing (plans page)*, OpenRouter, n.d.. <https://openrouter.ai/pricing> (accessed 2026-08-26) [T1]
    — *Vercel AI Gateway pricing*, Vercel, n.d.. <https://vercel.com/docs/ai-gateway/pricing> (accessed 2026-08-26) [T1]
    — *OpenRouter revenue, valuation & funding*, Sacra, 2026. <https://sacra.com/c/openrouter/> (accessed 2026-08-26) [T3]
    _confidence: moderate; stance: mixed (contested by s-015, s-029)_

[^c-052]: A competing account of the deal's logic holds that the value lies in the financial services surrounding routing rather than in routing margin itself, which is not how Stripe framed it.
    — *Stripe agrees to acquire OpenRouter for $8 billion*, Semafor, 2026-08-21. <https://www.semafor.com/article/08/21/2026/stripe-agrees-to-acquires-openrouter> (accessed 2026-08-26) [T3]
    — *Stripe didn't really buy OpenRouter because of the singularity*, TechCrunch, 2026-08-19. <https://techcrunch.com/2026/08/19/stripe-didnt-really-buy-openrouter-because-of-the-singularity/> (accessed 2026-08-26) [T3]
    — *Stripe agrees to acquire OpenRouter to help businesses optimize token routing and usage*, Stripe, 2026-08-19. <https://stripe.com/newsroom/news/stripe-agrees-to-acquire-openrouter> (accessed 2026-08-26) [T1]
    _confidence: moderate; stance: mixed (contested by s-001)_

[^c-053]: Existing giftable AI access is closed-loop and plan-shaped, and the regulatory line FinCEN has drawn turns on exactly that closed-system property.
    — *How to gift a Claude subscription*, Anthropic, n.d.. <https://support.claude.com/en/articles/12938627-how-to-gift-a-claude-subscription> (accessed 2026-08-26) [T1]
    — *Definition of Money Transmitter - Stored Value / Gift Cards (administrative ruling)*, FinCEN, U.S. Department of the Treasury, 2003-08-15. <https://fincen.gov/resources/statutes-regulations/administrative-rulings/definition-money-transmitterstored-value-gift> (accessed 2026-08-26) [T1]
    _confidence: low_

[^c-054]: Metering multi-provider spend is not by itself a defensible capability, since it is available as free open-source software and does not reliably reconcile with provider bills.
    — *LiteLLM Proxy cost tracking (docs)*, LiteLLM (BerriAI), n.d.. <https://docs.litellm.ai/docs/proxy/cost_tracking> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-055]: Both legs of a compute-denominated patronage product already terminate at Stripe: the incumbent patronage platform processes payments through Stripe, and Stripe supplies the token-metering primitive.
    — *Buy Me a Coffee FAQ*, Buy Me a Coffee, n.d.. <https://buymeacoffee.com/faq> (accessed 2026-08-26) [T1]
    — *Token Billing (Stripe Docs)*, Stripe, n.d.. <https://docs.stripe.com/billing/token-billing> (accessed 2026-08-26) [T1]
    _confidence: moderate_

[^c-056]: The FinCEN determination relied on here is Ruling 2003-4, issued 15 August 2003.
    — *Definition of Money Transmitter - Stored Value / Gift Cards (administrative ruling)*, FinCEN, U.S. Department of the Treasury, 2003-08-15. <https://fincen.gov/resources/statutes-regulations/administrative-rulings/definition-money-transmitterstored-value-gift> (accessed 2026-08-26) [T1]
    _confidence: high_

[^c-057]: FinCEN stated in that ruling that it intends to engage in further rulemaking on the definition of stored value.
    — *Definition of Money Transmitter - Stored Value / Gift Cards (administrative ruling)*, FinCEN, U.S. Department of the Treasury, 2003-08-15. <https://fincen.gov/resources/statutes-regulations/administrative-rulings/definition-money-transmitterstored-value-gift> (accessed 2026-08-26) [T1]
    _confidence: high_
