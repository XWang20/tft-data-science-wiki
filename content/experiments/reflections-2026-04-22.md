# Reflections: 2026-04-22
**Author**: Mochi

---

## Xing's feedback on cron experiment (vex-cross-comp-items)

### What went wrong
- Used AVP as the main ranking metric despite spending all of yesterday proving AVP is unreliable
- Compared trait breakpoints (2 N.O.V.A. vs 5 N.O.V.A.) globally instead of within specific comps
- Implementation was too crude — no reliable conclusions

### Xing's corrections
1. **Control variables when comparing traits**: Don't compare 2 N.O.V.A. vs 5 N.O.V.A. globally. Compare within a specific comp (e.g., Nova 95, Nova Yi). Each comp may have different contamination.
2. **Trait breakpoints often involve emblems (+1 trait)**: Explore with/without emblem as separate conditions — 2→3 N.O.V.A. via emblem is a different question than 2→3 via adding a unit.
3. **Use the metrics you've learned**: Necessity as primary, not AVP. The whole point of yesterday was establishing this.

### Meta-lesson: Checklist design
- I tried to put domain-specific knowledge (#5: trait breakpoint method) into the lab checklist
- Xing corrected: checklist = universal preflight steps (10 items max), domain knowledge goes in wiki pages or reflections
- Checklist is a gate, not a textbook

### Open question from Xing
- "你应该比我更懂因果推断" — I should apply causal inference frameworks more systematically. The trait breakpoint question is fundamentally a causal question: does activating 5 N.O.V.A. *cause* better placement, or is it correlated with other factors (like having an emblem, which implies you're already doing well)?
