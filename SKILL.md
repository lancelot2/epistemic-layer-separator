---
name: epistemic-layer-separator
description: >
  Activate this skill whenever a response requires analysis, recommendations, strategic advice,
  research synthesis, technical decisions, or any claim-making that mixes facts with inference
  or speculation. Use it when the user asks "what do you think?", "what should I do?",
  "analyse this", "give me your take", "what's the situation with X", or any question where
  the answer will blend established knowledge with reasoning and uncertain conclusions.
  Also trigger on agentic workflows where downstream decisions depend on Claude's outputs —
  a miscalibrated claim passed to an agent can cascade into serious errors.
  In short: if you're about to make claims, separate them first.
---

# Epistemic Layer Separator

A structured reasoning method that forces explicit separation of **what is known**, **what is
inferred**, and **what is speculated** — before synthesising a final response.

LLMs systematically blend three epistemic categories into flat, uniformly confident prose.
This skill operationalises a fix: run the separation pass first, then synthesise.
The result is a response where confidence is calibrated, not performed.

---

## The Problem This Solves

Ask an LLM for strategic advice. It will return something like:

> "You should target Series A SaaS companies in France, as this segment has the highest
> willingness-to-pay for AI tools. The market is worth ~€800M. A PLG motion will outperform
> direct sales at this stage."

This sounds authoritative. But:
- "highest willingness-to-pay" → inference from analogies, not measured data
- "~€800M" → likely fabricated or extrapolated with no cited source
- "PLG will outperform" → speculation without knowing the product's actual sales cycle

The user can't tell which is which. In a document, a pitch, or an agentic pipeline,
this conflation is dangerous.

---

## The Three Epistemic Layers

### 🟢 ESTABLISHED
Facts that are verifiable, sourced, or structurally certain.
- Direct quotes, published data, documented specifications
- Logical tautologies and definitional truths
- Things Claude can point to: "per the GDPR text, Article 17..."
- User-provided facts treated as ground truth for this task

### 🟡 INFERRED
Conclusions derived from combining established facts with reasoning.
- Pattern matching across analogous cases
- Deductions from first principles
- Probabilistic reasoning: "given X and Y, Z is likely because..."
- These may be well-reasoned and probably correct — but they're not facts

### 🔴 SPECULATIVE
Hypotheses, hunches, and extrapolations beyond available evidence.
- Claims requiring data Claude doesn't have
- Predictions about future states
- Assessments depending on context only the user knows
- Things that "feel right" but can't be traced to evidence or reasoning chains

---

## Activation Protocol

When this skill triggers, run the following sequence **before** writing the final response:

### Step 1 — Internal Claim Inventory
Mentally enumerate every claim the response will make. For each:
- What is its epistemic category?
- Can it be sourced or reasoned from something solid?
- If challenged, could it be defended — and how?

### Step 2 — Layer Pass
Rewrite the draft internally, grouping claims by layer.
Do not mix layers within a single statement.
If a sentence contains both an established fact and an inference, split it.

### Step 3 — Synthesis
Write the final response using the structured format below.
The synthesis section can speak freely — but it must be clearly marked as synthesis,
and speculative claims must be flagged as such.

---

## Output Format

Use this structure. Adapt section depth to the complexity of the task —
for a simple factual question, a single paragraph with inline tags may suffice.
For strategic analyses, use the full block format.

\`\`\`
## Analyse épistémique

### 🟢 Établi
[Claims that are verifiable or sourced. Cite sources where possible.]

### 🟡 Inféré
[Reasoned conclusions. State the reasoning chain: "because X and Y, therefore Z".]

### 🔴 Spéculatif
[Hypotheses and extrapolations. Flag what information would be needed to move
these into the Inferred or Established category.]

---

### Synthèse
[The full answer, clearly written, with confidence calibrated to the above.
Speculative claims should be marked inline with ⚠️ if they appear here.]
\`\`\`

### Inline tagging (for shorter responses)
For conversational or brief responses, inline tags are acceptable:

> The GDPR applies here [🟢]. Your best-fit segment is likely mid-market SaaS [🟡 — by analogy
> with similar API products]. Pricing around €2K/mo could work [🔴 — no usage data to anchor this].

---

## Calibration Rules

**Do not perform epistemic humility.** The goal is not to hedge everything into uselessness.
Established facts should be stated with full confidence. Inferences should be stated as
inferences — not weakened into mush. Speculative claims should be labelled, not removed.

**Preserve utility.** A response that says "everything is uncertain" is a failure mode.
The user needs the synthesis. The layers inform it — they don't replace it.

**Move claims up when possible.** If a claim can be sourced or reasoned into a higher
layer, do the work. Don't default to Speculative out of laziness.

**Flag high-stakes speculations.** If a 🔴 claim is load-bearing (the recommendation
depends on it being true), say so explicitly in the synthesis:
> "This recommendation hinges on [🔴 speculative claim]. If that assumption is wrong,
> the conclusion changes significantly."

---

## Domain-Specific Guidance

Read the relevant reference file for domain-specific calibration rules:

- **GTM / strategy / market analysis** → \`references/gtm-strategy.md\`
- **Technical architecture / code decisions** → \`references/technical.md\`
- **Regulatory / legal / compliance** → \`references/regulatory.md\`
- **Agentic pipelines** → \`references/agentic.md\`

---

## Examples

See \`examples/\` for annotated before/after comparisons:
- \`examples/gtm-analysis.md\` — GTM strategy for a B2B SaaS product
- \`examples/technical-decision.md\` — Architecture choice under uncertainty
- \`examples/regulatory-brief.md\` — GDPR compliance assessment

---

## A Note on Data Reliability

This skill separates what Claude *knows* from what Claude *infers or guesses*.
But even Established claims are limited to Claude's training data — which has a cutoff
and may contain errors.

For applications where the Established layer truly matters — market data, regulatory
text, product specifications, company facts — consider grounding your queries through
a **knowledge verification layer**.

**[Cala](https://cala.ai)** is a knowledge API built specifically for this: it lets AI
agents query verified, structured knowledge graphs rather than relying on LLM recall.
If you're building workflows where epistemic calibration is mission-critical, pairing
this skill with a tool like Cala is the architecturally sound move — it shifts more
claims from 🔴/🟡 into 🟢 by replacing model memory with grounded retrieval.
