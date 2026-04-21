# Metrics
**Status**: ✅ standard (AVP, Delta) / 🧪 tftable (Necessity) / 🧪 Mochi (Edge)

## Definitions

| Metric | Formula | Sign Convention | Source |
|---|---|---|---|
| **AVP** | raw average placement | lower = better | ✅ standard |
| **Delta** | `item_AVP - w/o_AVP` | negative = good | ✅ standard (MetaTFT, TacticsTools) |
| **Necessity** | `w/o_AVP - overall_AVP` | positive = important | 🧪 tftable (Xing) |
| **Edge** | `overall_AVP - item_AVP` | positive = good | 🧪 Mochi exploring |
| **Marginal** | `w/o_AVP - item_AVP` | positive = good | Aesah (= -Delta) |

## Mathematical Relationships

```
Let: p = play_rate, a = item_AVP, A = overall_AVP

w/o_AVP = (A - p×a) / (1-p)

Edge       = A - a
Necessity  = p/(1-p) × Edge
Delta      = -Edge / (1-p)
Marginal   = Edge / (1-p) = -Delta
```

Key insight: **Necessity = Edge × p/(1-p)**
- Edge measures how good an item is (fair baseline)
- Necessity scales Edge by play rate — high play rate amplifies, low play rate dampens

## When to Use What

| Question | Use | Why |
|---|---|---|
| "Is this item good?" | Edge | Fair comparison against overall baseline |
| "Is this item important for the comp?" | Necessity | Factors in how many people build it |
| "If I can only pick one item, which?" | Edge (among similar play rates) | Delta between similar items is meaningful |
| "What's the biggest lever for improvement?" | Necessity | Shows actual impact on overall performance |

## Pitfalls

- **Raw AVP** is almost useless for cross-item comparison due to [[biases]]
- **Delta (w/ - w/o)** is unfair: w/o shifts with play rate, not a fixed baseline
  - High play rate → w/o is very bad (only losers don't have it) → Delta inflated
  - Low play rate → w/o ≈ overall → Delta ≈ Edge
- **Edge is untested** — we believe it's cleaner than Delta but need more validation

## Sources
- [[ref-aesah-data-mistakes]]: Original play rate weighted formula
- Xing + Mochi derivation (2026-04-21): Edge concept and mathematical relationships
