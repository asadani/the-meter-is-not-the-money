# The Meter Is Not the Money

*How AI compute gets priced, metered, and paid for* — Anuj Sadani, 2026.

A short book arguing that tokens are a meter reading rather than a unit of
account, that every AI credit is a conversion layer over dollars, and that this
explains what a payments company bought when it bought a router.

Built with [book-forge](../book-forge), theme `sheet-oxblood` — the same
pipeline and look as the other books.

## Layout

```
meta.yaml          book-forge configuration
book.html.in       the manuscript, hand-authored HTML
assets/            cover art
research/          the verified source ledger this book is built on
index.html                       built — screen edition
the-meter-is-not-the-money.pdf   built — 30pp, A4, folio-stamped
```

## Build

```bash
PYTHONPATH=../book-forge python -m bookforge build
```

`doctor` checks the environment; `verify` audits an already-built PDF; `inject`
re-renders the front-matter and about partials into `book.html.in` after a
`meta.yaml` change. (`bf` is not on PATH here, hence `python -m`.)

**Run `inject` before `build` whenever the matter config in `meta.yaml` changes.**
The QR slots live inside the injected partials, so a build without injection
fails verification on stale QR codes and missing matter probes.

## Sourcing

Every `c-0NN` superscript in the text resolves to a row in
`research/claims.jsonl`. That workspace was produced by the `research-anything`
pipeline: each claim bound to a quoted passage inside a stored snapshot of its
source, with the snapshot's SHA-256 recorded, machine-checked before the sentence
citing it was written.

- **38 sources**, 17 of them T1 — price pages, terms of service, vendor
  documentation, and a federal rulemaking.
- **77 claims**, all `verified: pass`. 83 citations across 74 distinct claims;
  every one resolves and none is marked failed.
- **4 contested claims** (`c-007`, `c-051`, `c-052`, `c-069`) are each presented
  as contested in the text rather than resolved silently.

Two rules follow and should not be relaxed:

1. **Do not cite a claim that is not in the ledger.** If a sentence needs a
   source that is not there, run the research first. Two quotations reached a
   late draft unbound and were bound before publication rather than cut.
2. **Do not soften Section 5.** It carries the strongest case against the book's
   own thesis, and the front matter promises the reader it stands unanswered.

## Known limits

Each is disclosed in the section that depends on it, not only here.

| Section | Limit |
|---|---|
| 2 | All four reported prices reach the book secondhand — the primary reporting is paywalled |
| 3 | Mechanism is documented; the *magnitude* of price variance in production is unmeasured |
| 4 | Five pricing models is not a market survey |
| 6 | State money-transmitter licensing, CFPB Reg E, CARD Act and non-US regimes unresearched |
| 6 | Float, breakage and revenue recognition for prepaid balances unresearched |

## Notes

`deep-research-report.md` in this directory is a generic research-methodology
document, not routing material, and nothing in the book draws on it.
`AI Routing Ecosystem Analysis.docx` is registered in the ledger as `s-027` at
tier T4 with its provenance flagged — no named author, and its footnote
markers resolve to nothing — so no claim rests on it either.
