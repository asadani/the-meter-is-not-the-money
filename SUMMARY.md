# The Meter Is Not the Money — the condensed argument

**Question.** Can a token serve as a unit of account for AI compute — and what
did a payments company buy when it bought a router?

**Answer.** It cannot, and the reason is measurement rather than finance. A unit
of account has to mean the same thing to both parties at the moment they agree
to a trade, and a token does not: its price is not fixed when you buy it, it
varies by a factor of three between suppliers of an identical product, and the
sign of its cache adjustment depends on which vendor served the request. So
every credit balance in this market is denominated in dollars, and every
"AI credit" that ships is a per-model conversion layer over dollars. The
position worth owning is the exchange desk, not the mint.

---

## What set this off

On 19 August 2026 Stripe agreed to acquire OpenRouter for a price it never
disclosed. Its chief executive explained the purchase in one sentence: "Tokens
are the central currency for companies building with AI."

The company that was bought does not agree, in the only place that counts. Its
own documentation says the credit system's **base currency is US dollars**.
Vercel's gateway bills against a dollar balance at the provider's list price.
Stripe's own billing product lets a business define an "AI Credit" and configure
how each model's usage *converts* to it. That verb carries the whole argument.

## Why a token cannot hold still

Four documented mechanisms, all from vendor pages their own customers read.

**Price depends on who serves it.** For open-weight models the weights and the
hardware come apart. OpenRouter's own worked example spans $1, $2 and $3 per
million tokens for the same model.

**You do not choose which one.** The documented default load-balances on price
with candidates weighted by the inverse square of cost — nine times likelier for
the cheapest than the dearest. Roughly one request in ten still goes to a
costlier supplier. At the instant you press send, the price is a distribution,
not a number, and it does not resolve until the work is done.

**Not all tokens are the same kind of token.** A cache write costs 1.25x an
ordinary input token on recent OpenAI models; a cache read costs a quarter or a
half. Same word, same model, same request, three prices.

**The multipliers do not point the same way.** Anthropic carries a *negative*
discount on cache writes and a positive one on reads. A negative discount is a
surcharge. There is no shared sign convention to appeal to, and cache reads are
0.1x at Anthropic, 0.25x at Bedrock, 0.25x or 0.5x at OpenAI.

The consequence: **you cannot quote a fixed price for a request before it is
routed.** Not because the tooling is young — because there is no fixed price
there to quote. LiteLLM's documentation carries a section headed "Cost does not
match your provider bill?" and names three ways your meter can disagree with
your supplier's.

## What a payments company saw

Reported prices range from more than $7bn (Bloomberg) through $7.5bn (NYT) to
$8bn (Semafor), with $10bn floated during talks. None is a disclosure; averaging
them produces a number nobody reported.

The structural fact is the fee. OpenRouter takes **no markup on inference** and
charges **5.5% when you purchase credits**. That is a take rate — a percentage
of money moved, the economic signature of a processor rather than a software
vendor. It scales with how much money you put in, not with how much compute you
use. Stripe had already shipped the meter (Token Billing); what it lacked was
the thing that knows, request by request, which of eighty providers served the
work and what it charged.

## But the fee is not a rent

Five firms sell the same function four incompatible ways. OpenRouter charges
5.5% of funds loaded. Vercel charges no markup and no platform fee on tokens.
Portkey charges $49 a month. Cloudflare charges nothing. LiteLLM is free
open-source software you run yourself.

That dispersion means the take rate is a **business-model choice rather than a
property of the position**. A processor's fee is defended by licensing and
settlement obligations; a routing fee has neither, and two well-capitalized
firms have already set it to zero because they monetize elsewhere.

## The strongest case against this argument

Presented in the book without rebuttal, because the research could not build
one.

Semafor's reading: routing is *destined* for commoditization, and that is the
point — Stripe can afford zero routing margin because it monetizes billing, tax,
fraud, stablecoin settlement and treasury around it. Under that account the
routing layer is not the valuable position but the entry point to valuable
positions, none of which is routing.

A second reading has it as expense management rather than payments — a move to
the other side of the ledger, into a category Databricks, Rippling and Ramp had
already entered. And the arithmetic is unkind either way: at the figure floated
during talks, roughly **70x annualized revenue**.

These counter-readings dispute *where the value accrues*, not the mechanism.
Nobody argues the mess is imaginary.

## What can be built

The conversion layer is not speculative — it already ships. When Claude is sold
through cloud marketplaces, Anthropic rates usage **in USD first**, then converts
to Claude Consumption Units at one cent each. The dollars are not derived from
the units; the units are derived from the dollars. That is the thesis running in
production, for reasons unrelated to any acquisition.

What does not ship is a transferable balance. Gifted AI access is plan-shaped
and closed-loop. The obstacle is not payments plumbing — both legs already
terminate at Stripe, since Buy Me a Coffee runs on it — but that a balance
spendable across unaffiliated vendors is a regulated instrument. FinCEN's 2011
rule renamed "stored value" to "prepaid access" and keeps closed loop as a
lighter-touch category; open loop is not.

## What would change my mind

- A vendor quoting a **fixed price per token guaranteed at submission**, absorbing
  the routing variance the way an insurer absorbs risk.
- A **transferable, cross-vendor balance** shipping and surviving.
- The **cache multipliers converging** across vendors into one number.
- Whether OpenRouter's commitment that routing stays driven by what is best for
  the user holds under its new ownership. If in three years the router quietly
  prefers providers that settle through its parent's rails, the exchange desk
  was the point.

---

*The full inquiry is 30 pages: 38 sources captured and hashed, 77 claims bound
to exact quotations, every superscript resolving to a row in the claim ledger.*
