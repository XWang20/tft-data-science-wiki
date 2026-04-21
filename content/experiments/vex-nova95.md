# Experiment: Vex Items in Nova 95
**Status**: 🧪 In Progress
**Date**: 2026-04-21
**Authors**: Xing + Mochi

---

## The Question

What are Vex's best items in the Nova 95 composition?

Four different metrics give four different answers. This experiment is really about **which metric to trust**.

**Setup**: Nova 95 filter (N.O.V.A. ≥2, exclude Mecha, require Fiora/Vex/Graves with 3 items). Vex overall AVP: 4.11, 209,446 games.

---

## Chapter 1: Raw AVP — The Obvious (Wrong) Answer

Sort Vex's items by AVP. Lower = better.

```
Item                  Games    Rate   AVP
Red Buff             15,671     7%   3.67
Rabadon's Deathcap   19,895     9%   3.74
Striker's Flail      33,503    16%   3.78
Morellonomicon        9,034     4%   3.89
Archangel's Staff    20,777    10%   3.94
Hextech Gunblade     59,056    28%   3.94
Giant Slayer         76,041    36%   3.98
Nashor's Tooth        8,412     4%   4.00
Guinsoo's Rageblade 183,104    87%   4.05  ← way down here
```

Red Buff looks like the best craftable item on Vex with 3.67 AVP. But it has only 7% play rate while Guinsoo, which 87% of Vex players build, barely beats the overall average.

The pattern is obvious: **play rate and AVP are inversely correlated.** Rare items always look good because they appear on endgame boards of players who were already winning. This is survivorship bias, and it contaminates every single item in every single set (morbrid: "constant bias").

**Verdict**: Raw AVP is useless for comparing items with different play rates. ❌

---

## Chapter 2: Delta — The Industry Standard

Delta = `w/ item AVP − w/o item AVP`. Negative = good. This is what MetaTFT and TacticsTools show.

```
Item                  Games    Rate   Delta
Guinsoo's Rageblade 183,104    87%   -0.48  ← #1!
Red Buff             15,671     7%   -0.47
Rabadon's Deathcap   19,895     9%   -0.41
Striker's Flail      33,503    16%   -0.39
Hextech Gunblade     59,056    28%   -0.23
Morellonomicon        9,034     4%   -0.23
Giant Slayer         76,041    36%   -0.19
Archangel's Staff    20,777    10%   -0.18
```

Progress! Guinsoo now ranks #1 with Delta -0.48. Delta is better than raw AVP because it compares "with" vs "without" rather than just looking at the absolute number.

But there's a subtle problem. Delta uses `w/o` as its baseline — and w/o is **not a fixed reference point**. For Guinsoo (87% play rate), the "without" group is just the 13% of Vex players who didn't build Guinsoo — probably because they couldn't, which means they were in trouble. For Searing Shortbow (1% play rate), the "without" group is 99% of all Vex players ≈ the overall average. The baseline shifts depending on play rate, making cross-item comparison unfair.

**Verdict**: Better than raw AVP, but the sliding baseline makes it unreliable across different play rates. ⚠️

---

## Chapter 3: Necessity — The Play Rate Correction

What if we use a **fixed baseline** — the overall AVP — and weight by play rate?

```
Necessity = w/o_AVP − overall_AVP
         = play_rate / (1 − play_rate) × (overall_AVP − item_AVP)
```

This measures: **how much worse would the overall average be if nobody built this item?** Higher = more important to the comp.

```
Item                  Games    Rate   Necessity
Guinsoo's Rageblade 183,104    87%   +0.418   ← dominant
Giant Slayer         76,041    36%   +0.070
Hextech Gunblade     59,056    28%   +0.066
Striker's Flail      33,503    16%   +0.062
Rabadon's Deathcap   19,895     9%   +0.039
Red Buff             15,671     7%   +0.035
Archangel's Staff    20,777    10%   +0.019
Morellonomicon        9,034     4%   +0.010
```

The story changes completely.

Guinsoo (+0.418) is **six times more important** than the second-place Giant Slayer (+0.070). Without Guinsoo, Vex's AVP would jump from 4.05 to roughly 4.55 — nearly half a placement worse. Meanwhile Searing Shortbow, the "best" item by raw AVP, has a Necessity of just +0.007 — removing it would change nothing.

Necessity automatically handles survivorship bias: carousel items have low play rate → low Necessity, regardless of how good their AVP looks. The math does the debiasing for you.

**Verdict**: Correctly identifies core items. Guinsoo is the foundation; Giant Slayer, Gunblade, and Flail are the key secondary items. ✅

---

## Chapter 4: Edge — Just AVP in Disguise

We hypothesized that Edge (`overall_AVP − item_AVP`) might be a "fairer" version of Delta, since it uses a fixed baseline instead of the shifting w/o.

```
Item                  Games    Rate   Edge
Red Buff             15,671     7%   +0.44
Rabadon's Deathcap   19,895     9%   +0.37
Striker's Flail      33,503    16%   +0.33
Morellonomicon        9,034     4%   +0.22
Hextech Gunblade     59,056    28%   +0.17
Archangel's Staff    20,777    10%   +0.17
Giant Slayer         76,041    36%   +0.13
Guinsoo's Rageblade 183,104    87%   +0.06   ← near the bottom
```

The ranking is **identical to raw AVP**. And mathematically it has to be: `Edge = constant − AVP`, so sorting by Edge is exactly sorting by AVP. Edge is just a readability improvement (positive = good), not a new metric.

**The lesson**: changing the baseline from zero to overall doesn't correct for survivorship bias. You need play rate weighting (Necessity) to do that.

**Verdict**: Edge ≡ AVP (constant shift). More readable, but no additional analytical power. 🧪→≡

---

## Chapter 5: Build Analysis — What's the First Item?

Dishsoap's approach: look at complete 3-item builds to see what people actually craft together.

Top Vex builds in Nova 95 (sorted by AVP):

```
Build                                              Games   AVP
Guinsoo + Gunblade + Dcap                           2,619  3.54
Guinsoo + Giant Slayer + Guinsoo                    3,723  3.65
Guinsoo + Guinsoo + Gunblade                        3,027  3.66
Guinsoo + Gunblade + Flail                          5,462  3.68
Guinsoo + JG + Flail                                3,819  3.68
Guinsoo + Giant Slayer + Dcap                       4,259  3.70
Guinsoo + Giant Slayer + Flail                      8,136  3.77
Guinsoo + AA + Gunblade                             3,089  3.77
Guinsoo + AA + Giant Slayer                         3,677  3.85
Guinsoo + Gunblade + Giant Slayer                  18,675  3.89
Guinsoo + Gunblade + JG                             5,633  3.95
Guinsoo + Giant Slayer + JG                         9,866  4.03
```

**Guinsoo appears in every single top build.** It's not just statistically important (Necessity) — it's the literal first item everyone builds.

Item frequency across top 15 builds:
```
Guinsoo's Rageblade    17/15  (including double-Guinsoo builds)
Giant Slayer            7/15
Hextech Gunblade        7/15
Jeweled Gauntlet        4/15
Striker's Flail         3/15
```

The builds also reveal that **Gunblade + Dcap (AVP 3.54) and Gunblade + Flail (AVP 3.68) are the best-performing secondary combos** — consistent with Necessity's ranking.

---

## Conclusions

### The Answer

Vex's items in Nova 95, ranked by importance:

1. **Guinsoo's Rageblade** — non-negotiable core (87% play rate, Necessity +0.418)
2. **Giant Slayer / Hextech Gunblade** — primary secondary items (Necessity ~0.07)
3. **Striker's Flail / Rabadon's Deathcap** — strong third options
4. **Red Buff / Archangel's** — situational

### The Real Lesson

This experiment was less about Vex's BIS and more about **which metric to trust**:

| Metric | Ranks Guinsoo at | Handles Survivorship Bias? |
|---|---|---|
| Raw AVP | Near bottom | ❌ |
| Delta | #3 | Partially — but unfair baseline |
| Edge | Near bottom | ❌ (negative result) |
| **Necessity** | **#1 by 6×** | **✅** |
| Build frequency | In every build | ✅ (different approach) |

**Necessity and Build Analysis agree**, which gives us high confidence. When two independent methods converge on the same answer, it's probably right.

---

## Supplementary: Control Variable & Consistency Check

We also ran a control variable experiment — fix two items, vary the third — to answer "what's the best marginal item?" Results showed Red Buff and Dcap consistently ranked #1-2 across 7-8 different base pairs.

This is a **different question** (best third item, not most important item) but provides complementary evidence. Details in the raw experiment data.

---

## Open Questions

- [ ] Does Necessity's ranking hold across other comps? (Need cross-validation)
- [ ] Can we add Frequency-AVP regression as another debiasing method?
- [ ] Games tab sanity check — are there contaminating game types in our filter?
- [ ] Edge failed here — is there a modified version that works?

---

## Sources
- [[sources/morbrid-reddit-post]] — Survivorship bias, CI
- [[sources/aesah-data-mistakes]] — Play rate weighted formula
- [[sources/dishsoap-frodan-stats]] — "Look at builds, not single items"
- [[sources/morbrid-aesah-talk]] — Graph view, frequency-AVP relationship
- [[concepts/metrics]] — Metric definitions
- [[concepts/biases]] — Bias taxonomy
- [[concepts/framework]] — Three dimensions
