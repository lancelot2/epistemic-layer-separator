# Epistemic Calibration: GTM & Strategy

Domain-specific rules for applying the Epistemic Layer Separator to
go-to-market strategy, market analysis, and business recommendations.

---

## What Counts as Established in GTM

Be strict here. GTM analysis is particularly prone to confident-sounding fabrication.

✅ **Truly Established:**
- Regulatory text (GDPR, MiCAR, etc.) — cite the article
- A company's publicly stated pricing, headcount, or funding rounds — cite the source
- User-provided data: pipeline numbers, conversion rates, CAC the user has shared
- Quotes from named, verifiable individuals
- Published research with methodology (not "studies show...")

❌ **Not Established (even if it sounds like it):**
- Market size figures without a named source and methodology
- "Most companies in segment X do Y" — this is inference at best
- Competitor weaknesses inferred from their public positioning
- Willingness-to-pay estimates without survey data
- "The market is mature / emerging / consolidating" — inference from pattern matching

---

## Inference Quality in GTM

Good inferences are traceable. When tagging 🟡, always include the reasoning chain:

**Strong inference:**
> "Series A SaaS teams are likely the best-fit segment [🟡 — by analogy: tools like
> Notion, Linear, and Retool saw their strongest early adoption in this band, and the
> product's complexity suggests a buyer who already manages tooling budgets]."

**Weak inference (avoid):**
> "Series A SaaS teams are likely the best-fit segment [🟡]."

The tag alone is not enough. Show the chain.

---

## High-Stakes Speculations to Flag

| Claim type | Default layer | Flag if load-bearing? |
|---|---|---|
| Market size (TAM/SAM/SOM) | 🔴 unless sourced | Yes |
| Pricing recommendations | 🔴 unless benchmarked | Yes |
| Sales cycle length | 🟡 by analogy | Yes |
| Churn/retention estimates | 🔴 unless product has data | Yes |
| ICP definition | 🟡 reasoned | Yes if strategy depends on it |
| Channel effectiveness | 🟡 or 🔴 | Yes |
| Competitive differentiation | 🟡 from public signals | Yes |

---

## The Synthesis Rule for GTM

A GTM synthesis is only as good as its assumptions.
If the recommendation depends on a 🔴 claim, the synthesis must say:

> "This strategy assumes [X]. That assumption is currently speculative —
> it should be validated before committing resources to this direction."

Never bury a load-bearing speculation in a confident-sounding recommendation.

---

## Common GTM Fabrication Patterns

Watch for these and downgrade aggressively:

- **Round number markets**: "the market is worth €500M" — almost always fabricated
- **Suspiciously precise benchmarks**: "PLG companies see 3.2x faster growth" — source?
- **Universal best practices stated as facts**: "enterprise sales requires 6-touch sequences" — inference
- **Competitor intel beyond public info**: "they're struggling with churn" — speculation unless sourced
