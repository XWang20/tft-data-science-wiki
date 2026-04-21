# Experiment: Vex Items in Nova 95
**Status**: 🧪 In Progress
**Date**: 2026-04-21
**Authors**: Xing + Mochi

---

## The Question

What are Vex's best items in the Nova 95 composition?

We tried four different metrics. Each told a different story. The real question became: **which metric should we trust?**

**Setup**: Nova 95 filter (N.O.V.A. ≥2, exclude Mecha, require Fiora/Vex/Graves with 3 items). Vex overall AVP: 4.11, 209,755 games. Only craftable items included.

---

## Chapter 1: Raw AVP

Sort by AVP. Lower = better.

```
Item                  Games    Rate   AVP   Top4%
Red Buff             15,697     7%   3.67  63.8%
Rabadon's Deathcap   19,927    10%   3.74  63.1%
Striker's Flail      33,525    16%   3.79  62.3%
Morellonomicon        9,047     4%   3.89  59.9%
Hextech Gunblade     59,140    28%   3.94  59.5%
Archangel's Staff    20,807    10%   3.94  59.5%
Giant Slayer         76,178    36%   3.99  58.6%
Nashor's Tooth        8,427     4%   4.00  58.5%
Guinsoo's Rageblade 183,379    87%   4.05  57.4%
Jeweled Gauntlet     46,764    22%   4.12  55.4%
Void Staff           23,843    11%   4.26  52.8%
```

Red Buff is "the best item on Vex." But 7% play rate vs Guinsoo's 87%. And there's a clear pattern: **lower play rate → lower (better) AVP.** This is survivorship bias — rare items appear disproportionately on late-game boards of players who were already winning.

---

## Chapter 2: Delta

Delta = `w/ - w/o`. Negative = good. The industry standard (MetaTFT, TacticsTools).

```
Item                  Games    Rate   Delta
Guinsoo's Rageblade 183,379    87%   -0.476
Red Buff             15,697     7%   -0.470
Rabadon's Deathcap   19,927    10%   -0.405
Striker's Flail      33,525    16%   -0.385
Hextech Gunblade     59,140    28%   -0.234
Morellonomicon        9,047     4%   -0.225
Giant Slayer         76,178    36%   -0.193
Archangel's Staff    20,807    10%   -0.184
```

Better. Guinsoo rises to #1. But Delta has a structural issue: the w/o baseline **shifts with play rate**. For Guinsoo (87% play rate), the "without" group is just 13% of players — likely those who couldn't get Guinsoo, meaning they were already struggling. For Red Buff (7%), the "without" group is 93% ≈ the overall average.

This means Guinsoo's Delta is inflated by a terrible w/o group, and Red Buff's Delta is deflated by a near-normal w/o group. The comparison is structurally unfair.

---

## Chapter 3: Necessity

Necessity = `w/o - overall`. How much worse would the overall be if this item didn't exist?

```
Necessity = play_rate / (1 − play_rate) × (overall − item_AVP)
```

```
Item                  Games    Rate   Necessity
Guinsoo's Rageblade 183,379    87%   +0.416
Giant Slayer         76,178    36%   +0.070
Hextech Gunblade     59,140    28%   +0.066
Striker's Flail      33,525    16%   +0.062
Rabadon's Deathcap   19,927    10%   +0.038
Red Buff             15,697     7%   +0.035
Archangel's Staff    20,807    10%   +0.018
Morellonomicon        9,047     4%   +0.010
```

Guinsoo (+0.416) is six times more important than the second-place Giant Slayer (+0.070). Without Guinsoo, Vex's AVP would go from 4.05 to roughly 4.55 — nearly half a placement worse.

Red Buff drops from #1 (raw AVP) / #2 (Delta) to #6 (Necessity). Its low play rate means its contribution to the overall is small, even though it performs well when it does appear.

---

## Chapter 4: Edge

Edge = `overall − item_AVP`. Our experimental metric — uses a fixed baseline.

```
Item                  Games    Rate   Edge
Red Buff             15,697     7%   +0.435
Rabadon's Deathcap   19,927    10%   +0.366
Striker's Flail      33,525    16%   +0.324
Morellonomicon        9,047     4%   +0.215
Hextech Gunblade     59,140    28%   +0.168
Archangel's Staff    20,807    10%   +0.166
Giant Slayer         76,178    36%   +0.123
Guinsoo's Rageblade 183,379    87%   +0.060
```

The ranking is identical to raw AVP. Mathematically it must be: `Edge = constant − AVP`. Edge is just AVP with a readability improvement (positive = good). It doesn't correct for survivorship bias.

---

## Chapter 5: Build Analysis

What do the best-performing complete builds look like? Sorted by AVP.

```
Build                                            Games   AVP   Top4%
Guinsoo + Dcap + Red Buff                          680  3.23   71%
Guinsoo + Guinsoo + Dcap                           831  3.35   71%
AA + Guinsoo + Red Buff                            629  3.36   70%
Guinsoo + Red Buff + Flail                       1,596  3.45   68%
AA + Guinsoo + Dcap                                727  3.48   69%
Giant Slayer + Guinsoo + Red Buff                2,487  3.51   67%
Guinsoo + Gunblade + Red Buff                    1,947  3.51   66%
Guinsoo + Gunblade + Dcap                        2,619  3.54   67%
```

Guinsoo appears in **every single top build**. But the top builds by AVP also heavily feature Red Buff and Dcap — the same items that raw AVP ranked high.

Is this also survivorship bias? Possibly. Low-frequency builds (680, 831 games) dominate the top. The most popular build (Guinsoo + Gunblade + Giant Slayer, 18,675 games) has a much worse AVP of 3.89.

Item frequency in top 20 builds:
```
Guinsoo's Rageblade    25/20  (including double-Guinsoo builds)
Striker's Flail         7/20
Rabadon's Deathcap      6/20
Red Buff                6/20
Hextech Gunblade        5/20
```

---

## Combined View

```
Item                  Games    Rate   AVP   Delta   Neces.  Edge
Guinsoo's Rageblade 183,379    87%   4.05  -0.476  +0.416  +0.06
Giant Slayer         76,178    36%   3.99  -0.193  +0.070  +0.12
Hextech Gunblade     59,140    28%   3.94  -0.234  +0.066  +0.17
Striker's Flail      33,525    16%   3.79  -0.385  +0.062  +0.32
Rabadon's Deathcap   19,927    10%   3.74  -0.405  +0.038  +0.37
Red Buff             15,697     7%   3.67  -0.470  +0.035  +0.44
Archangel's Staff    20,807    10%   3.94  -0.184  +0.018  +0.17
Morellonomicon        9,047     4%   3.89  -0.225  +0.010  +0.22
```

Every metric tells a different story. AVP/Edge say Red Buff. Delta says Guinsoo (but for the wrong reason — inflated by terrible w/o group). Necessity says Guinsoo (for a defensible reason — play rate weighting).

---

## What We Learned

### About Vex's items
- **Guinsoo is the core identity item** — confirmed by Necessity (#1) and build analysis (in every build)
- **Giant Slayer, Gunblade, Flail** are the key secondary items — all have Necessity around +0.06-0.07
- **Red Buff and Dcap appear in the best builds** but have low play rate — their strength may be real, but the data can't definitively prove it due to sample size and survivorship bias

### About metrics
- **AVP and Edge rank identically** — Edge = constant − AVP, no additional information
- **Delta surfaces Guinsoo** but has a structural fairness problem with the shifting w/o baseline
- **Necessity correctly weights by play rate** and agrees with build analysis — two independent methods converging
- **No metric fully solves survivorship bias** — even Necessity assumes play rate is a sufficient proxy, which may not always hold

### Open questions
- [ ] Does Necessity's ranking hold across other comps?
- [ ] Can Frequency-AVP regression provide a fifth perspective?
- [ ] Are the top builds by AVP (with Red Buff, Dcap) truly the best, or just surviving late?
- [ ] Games tab sanity check — what's in our filter?

---

## Supplementary: Control Variable & Consistency Check

We also explored the question "what's the best third item?" by fixing two items and varying the third across 8 base pairs. Red Buff and Dcap consistently ranked #1-2. This answers a different question (marginal item selection) and provides complementary evidence.

---

## Sources
- [[sources/morbrid-reddit-post]] — Survivorship bias, CI
- [[sources/aesah-data-mistakes]] — Play rate weighted formula
- [[sources/dishsoap-frodan-stats]] — "Look at builds, not single items"
- [[sources/morbrid-aesah-talk]] — Graph view, frequency-AVP relationship
- [[concepts/metrics]] — Metric definitions
- [[concepts/biases]] — Bias taxonomy
- [[concepts/framework]] — Three dimensions
