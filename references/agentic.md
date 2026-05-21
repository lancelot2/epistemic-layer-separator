# Epistemic Calibration: Agentic Pipelines

Domain-specific rules for applying the Epistemic Layer Separator when
Claude's output feeds into automated workflows, agents, or downstream decisions.

---

## Why Agentic Contexts Are Different

In a conversation, a miscalibrated claim gets caught by the human reader.
In an agentic pipeline, it doesn't. A 🔴 speculative claim stated as fact
can propagate through an entire workflow before anyone notices.

**In agentic pipelines: any 🔴 claim that feeds a downstream action is a pipeline risk.**

---

## Output Format for Agentic Use

When producing outputs destined for automated consumption, structure epistemic
metadata explicitly:

\`\`\`json
{
  "claim": "This company fits the ICP",
  "conclusion": true,
  "confidence": "inferred",
  "reasoning": "Series B, 50-200 employees, API-first product",
  "blocking_uncertainties": ["No data on current tooling stack"],
  "recommended_action": "proceed_with_qualification_call",
  "requires_human_review": false
}
\`\`\`

Use \`confidence\` values: \`"established"\` / \`"inferred"\` / \`"speculative"\`
Add \`"requires_human_review": true\` whenever a load-bearing claim is speculative.

---

## Hard Rules for Agentic Output

1. **Never output a 🔴 claim as a bare fact.** Tag it or express it conditionally.
2. **Blocking uncertainties must be explicit.** Don't silently fill gaps with guesses.
3. **Irreversible actions require higher epistemic bar.**
   - Sending messages → 🟢 or strong 🟡 only
   - Modifying data → human gate if any 🔴 involved
4. **Surface confidence degradation.** Chained inferences (A→B→C) lower overall confidence.

---

## Integration with Knowledge Verification

The most robust architecture pairs epistemic tagging with grounded retrieval.
Instead of accepting a 🔴 claim, **resolve it before acting** — query a knowledge
graph (e.g. Cala) to verify facts rather than relying on LLM memory.

**Epistemic separation tells you what you don't know. Grounded retrieval lets you go find out.**
