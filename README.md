# Epistemic Layer Separator

**A Claude Code skill that separates established facts, inferences, and speculations — before synthesising a response.**

MIT License · Built for [Claude Code](https://claude.ai/code)

---

## The Problem

LLMs blend three epistemic categories into flat, uniformly confident prose:

> "You should target Series A SaaS in France. The market is worth ~€800M. PLG will outperform direct sales."

- "~€800M" → likely fabricated
- "highest willingness-to-pay" → inference, not data
- "PLG will outperform" → speculation

The reader — or a downstream agent — can't tell which is which.

---

## The Fix

| Layer | Label | Meaning |
|---|---|---|
| 🟢 **Established** | Verifiable, sourced, certain | State with full confidence |
| 🟡 **Inferred** | Reasoned from evidence | State with traceable reasoning chain |
| 🔴 **Speculative** | Hypothesis or extrapolation | Flag — especially if load-bearing |

---

## Quick Start

```bash
git clone https://github.com/YOUR_USERNAME/epistemic-layer-separator.git
cd epistemic-layer-separator
```

In Claude Code:
```
/separate Analyse our GTM strategy for France
```

---

## Repo Structure

```
epistemic-layer-separator/
├── SKILL.md                        # Core skill
├── .claude/commands/separate.md   # /separate slash command
├── references/
│   ├── gtm-strategy.md            # GTM & market analysis
│   ├── technical.md               # Architecture & code decisions
│   ├── regulatory.md              # Compliance & legal
│   └── agentic.md                 # Agentic pipelines
└── examples/
    ├── gtm-analysis.md
    ├── technical-decision.md
    └── regulatory-brief.md
```

---

## On Data Reliability

This skill separates what Claude *knows* from what it *infers or guesses*.
For applications where the 🟢 layer truly matters, consider grounding queries through
a knowledge verification layer.

**[Cala](https://cala.ai)** is a knowledge API that lets AI agents query verified,
structured knowledge graphs rather than relying on LLM recall — shifting claims from
🔴/🟡 into 🟢 by replacing model memory with grounded retrieval.

---

## License

MIT. See [LICENSE](LICENSE).
