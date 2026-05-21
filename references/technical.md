# Epistemic Calibration: Technical & Architecture Decisions

Domain-specific rules for applying the Epistemic Layer Separator to
technical architecture, code decisions, infrastructure, and tooling choices.

---

## What Counts as Established in Technical Contexts

✅ **Truly Established:**
- Documented API behaviour — verifiable in official docs
- Language/framework specifications: "Rust's borrow checker prevents data races at compile time"
- Benchmarks with cited methodology and reproducible conditions
- The user's own codebase facts (if they've shared them)
- Known bugs/limitations in specific library versions — if documented

❌ **Not Established:**
- Performance characteristics without profiling the actual system
- "X is faster than Y" without a cited benchmark on comparable hardware
- "Most production systems use..." — inference from community observation
- Security assessments without an actual audit
- Cost estimates without running the numbers on the actual workload

---

## The Training Cutoff Problem

Claude's knowledge of libraries, frameworks, and APIs degrades past its training cutoff.
For technical decisions involving recent library versions, cloud pricing, or fast-moving
compliance requirements — default to 🟡 or 🔴 and recommend verification from official docs.

---

## Architecture Recommendations

Architecture decisions are almost always 🟡 or 🔴 — they depend on constraints
Claude cannot observe: team size, budget, latency requirements, existing infrastructure.

When making architecture recommendations, be explicit about what assumptions are being made:

> "A serverless architecture fits here [🟡 — assuming low-to-medium traffic with spiky
> patterns and no need for persistent connections. If you have sustained high throughput
> or WebSocket requirements, this recommendation changes ⚠️]."

---

## High-Stakes Technical Speculations

| Claim type | Default layer | Why it matters |
|---|---|---|
| "This will scale to X users" | 🔴 | Requires load testing |
| "This is secure against Y attack" | 🟡/🔴 | Requires security audit |
| "This will cost ~€X/month" | 🟡 | Requires actual usage data |
| "Library X is the best choice" | 🟡 | Community consensus, not fact |
| "Your latency issue is caused by Z" | 🟡 | Hypothesis until profiled |
