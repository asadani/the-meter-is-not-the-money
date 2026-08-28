# The Meter Is Not the Money — the argument in brief

**A token is a meter reading, not a unit of account.** Every AI credit that ships
is a per-model conversion layer over dollars — which is why the position worth
owning is the exchange desk rather than the mint.

---

## 01 · The sentence, and the price page

In August 2026 Stripe agreed to buy OpenRouter for a price it never disclosed.
Its chief executive explained the purchase in one line:

> "Tokens are the central currency for companies building with AI."

It is a good sentence. It is also contradicted by the documentation of the
company Stripe was buying, which answers the only question that matters — in what
unit is the balance held? — without ceremony:

> "OpenRouter uses a credit system where the base currency is US dollars."

Not tokens. Dollars. And the reason is measurement rather than caution. A unit of
account has to mean the same thing to both parties at the moment they agree to a
trade, and a token does not. Providers serving the identical open-weight model
differ threefold in price. The router picks between them with a draw weighted by
the inverse square of cost, so roughly one request in ten still goes to a costlier
supplier. A cache write can cost *more* than an ordinary input token, and whether
that adjustment is a discount or a surcharge depends on which vendor you asked.

Which means the price of a request is not a number when you press send. It is a
distribution, and it does not resolve until the work is done. You cannot quote a
fixed price for a request before it is routed — not because the tooling is young,
but because there is no fixed price there to quote. The clearest admission of what
that costs in practice sits in the documentation of LiteLLM, the open-source
gateway thousands of teams use to track spend, under a heading it does not
euphemise:

> "Cost does not match your provider bill?"

## 02 · The unit already exists, and it is worth a cent

So the interesting question is not why nobody minted a token currency. It is what
the people closest to the problem built once they worked out they could not. The
answer is already shipping, and almost nobody has noticed it.

When Claude is sold through the AWS and Azure marketplaces, Anthropic does not
bill in tokens. A cloud marketplace needs one countable line item and cannot
express "1.25x base input price for a five-minute cache write," so the vendor
rates the usage in dollars and then invents a unit to report:

> "rates your token usage in USD at standard per-model, per-feature rates, applies
> any negotiated discount, converts the result to CCUs at $0.01 per CCU."

A Claude Consumption Unit is worth a penny. Note the direction of travel: usage is
priced **in USD first**, then converted. The dollars are not derived from the
units. The units are derived from the dollars — which is the whole argument of
this book, running in production as a billing integration, for reasons that have
nothing to do with any acquisition.

Stripe's own product does the same thing one layer up, letting a business define
an "AI Credit" and configure how each model's usage *converts* to it. That verb is
carrying the argument. A credit is a synthetic unit whose exchange rate against
real tokens is set per model and changed at will by whoever sells it. The
complexity does not vanish; it moves behind an interface, where one business
absorbs it so its customers never look at it.

---

## What the book does that this page cannot

It presents the strongest case *against* its own thesis — that routing is meant to
become worthless, and that a buyer can afford zero routing margin because it
monetises billing, tax, fraud and settlement around it — with no rebuttal
appended, because the research could not build one.

It also marks its own limits: the mechanism is documented, the magnitude is not
measured, and the regulatory section stops at a federal rulemaking.

---

*The full inquiry is 30 pages: 38 sources captured and hashed, 77 claims bound to
exact quotations, every superscript resolving to a row in the claim ledger.*
