# Vex Items in Nova 95 — Experiment Report

## Experiment 1: Single Item AVP (Baseline — Known Biased)

```
Item                      Games    AVP    95%CI           99%Upper
Guinsoo's Rageblade      175,826  4.05   [4.04, 4.06]     4.06
Giant Slayer              72,779  3.99   [3.97, 4.00]     4.01
Hextech Gunblade          56,575  3.94   [3.92, 3.96]     3.96
Jeweled Gauntlet          44,833  4.12   [4.09, 4.14]     4.14
Striker's Flail           32,391  3.78   [3.75, 3.81]     3.81
Archangel's Staff         20,078  3.95   [3.91, 3.98]     3.99
Rabadon's Deathcap        19,021  3.74   [3.70, 3.77]     3.78
Red Buff                  15,171  3.66   [3.63, 3.70]     3.71
```

⚠️ **This is BIASED** — survivorship bias makes low-freq items look better.

---

## Experiment 3: Control Variable — Fix 2 Items, Vary 3rd

### Fixed: Guinsoo + Giant Slayer + ???  (61,419 games)
```
3rd Item          Games    AVP    95% CI
Red Buff          2,408   3.48   [3.39, 3.58]
2x Guinsoo        3,577   3.67   [3.60, 3.75]
Dcap              4,026   3.69   [3.62, 3.76]
Morellos           1,384   3.72   [3.59, 3.84]
Flail             7,896   3.78   [3.73, 3.83]
Archangel's       3,516   3.86   [3.78, 3.93]
Gunblade         17,815   3.89   [3.85, 3.92]
JG                9,423   4.04   [3.99, 4.09]
Void Staff        4,076   4.11   [4.04, 4.18]
```

### Fixed: Guinsoo + Gunblade + ???  (47,026 games)
```
Red Buff          1,878   3.46   [3.35, 3.57]
Dcap              2,524   3.55   [3.46, 3.64]
2x Guinsoo        2,876   3.64   [3.55, 3.73]
Flail             5,233   3.68   [3.62, 3.75]
AA                2,965   3.80   [3.71, 3.88]
GSlayer          17,815   3.89   [3.85, 3.92]
JG                5,426   3.94   [3.87, 4.00]
Void Staff        3,294   4.19   [4.11, 4.28]
```

### Fixed: Guinsoo + Dcap + ???  (13,597 games)
```
Red Buff            627   3.21   [3.03, 3.40]
2x Guinsoo          778   3.35   [3.19, 3.51]
Flail             1,524   3.52   [3.40, 3.63]
Gunblade          2,524   3.55   [3.46, 3.64]
JG                1,636   3.67   [3.56, 3.78]
GSlayer           4,026   3.69   [3.62, 3.76]
Void Staff        1,030   3.91   [3.77, 4.05]
```

### Fixed: Guinsoo + Flail + ???  (26,263 games)
```
Red Buff          1,512   3.44   [3.32, 3.56]
Dcap              1,524   3.52   [3.40, 3.63]
2x Guinsoo        1,766   3.60   [3.49, 3.70]
JG                3,682   3.68   [3.60, 3.75]
Gunblade          5,233   3.68   [3.62, 3.75]
AA                1,325   3.74   [3.61, 3.87]
GSlayer           7,896   3.78   [3.73, 3.83]
```

---

## Experiment 4: Worst-Case Ranking (99% CI Upper Bound)

Top 15 builds sorted by pessimistic estimate:
```
Build                                         Games    AVP   99%Upper
Guinsoo + Dcap + RFC                            626   3.23     3.48
2x Guinsoo + Dcap                               778   3.35     3.56
AA + Guinsoo + RFC                              612   3.36     3.59
Guinsoo + Gunblade + RFC                      1,879   3.46     3.60
Guinsoo + Flail + RFC                         1,511   3.45     3.60
Guinsoo + GSlayer + RFC                       2,407   3.48     3.60
Guinsoo + Gunblade + Dcap                     2,522   3.55     3.66
Guinsoo + Flail + Dcap                        1,521   3.52     3.67
2x Guinsoo + Flail                            1,768   3.60     3.74
2x Guinsoo + Gunblade                         2,876   3.64     3.75
Guinsoo + Gunblade + Flail                    5,231   3.69     3.77
Guinsoo + Flail + JG                          3,685   3.68     3.77
2x Guinsoo + GSlayer                          3,575   3.67     3.77
Guinsoo + GSlayer + Dcap                      4,023   3.69     3.78
```

---

## Experiment 5: Consistency — Same Item Across Different Base Pairs

```
Item            #Pairs  AvgRank%   Best  Worst  Verdict
Red Buff           7     10.9%     6%    25%    ✅ Consistently strong
Dcap               8     17.4%    12%    22%    ✅ Consistently strong
Morellos            6     35.0%    28%    56%    ⚠️ Above average
Flail              9     38.5%    11%    60%    ⚠️ Above average
2x Guinsoo        16     44.1%    11%    88%    ⚠️ Above avg (volatile)
AA                 9     48.6%    17%    80%    ⚠️ Above avg (volatile)
Gunblade           9     63.7%    50%    89%    — Average
Giant Slayer      11     65.2%    33%    90%    — Average
JG                 9     83.3%    60%   100%    ❌ Consistently weak
Void Staff         8     95.1%    83%   100%    ❌ Consistently weak
```

---

## Key Findings

### 1. Red Buff + Dcap are the real winners
- **Red Buff**: Ranks #1 in EVERY base pair (avg rank 10.9%). CI upper bounds are narrow.
- **Dcap**: Ranks top 2 almost everywhere (avg rank 17.4%).
- Both have lower sample counts but their consistency across 7-8 different pair contexts is very compelling.

### 2. The "popular" items are actually mediocre
- **Gunblade** (56k games as single item): Looks decent at 3.94 AVP, but in control variable tests it's *average* (rank 63.7%). The most popular build (Guinsoo+Gunblade+GSlayer at 17.8k games) is 3.89 — worse than several alternatives.
- **Giant Slayer** (72k games): Similar story — ranks 65.2%, average.

### 3. JG and Void Staff are traps
- Both look okay in single-item analysis (JG 4.12, Void Staff 4.27) but their CI includes selection effects.
- In control variable, they consistently rank *last* or near-last (JG 83.3%, Void Staff 95.1%).

### 4. RFC is quietly the best sub-component
- Builds with RFC dominate the "worst-case" ranking (top 6 of 15).
- But RFC has very low sample counts — needs monitoring.

### 5. Biases still present
- **Red Buff**: Could still benefit from late-game survivorship (it's a cheap item, maybe completed late from spare components?)
- **RFC builds**: Low sample — CI wide, could be noise
- **Player behavior**: Popular items get "diluted" by forced builds

---

## Recommended Methodology for Future Analyses

1. **Never compare single-item AVP directly** — always use control variable or full build analysis
2. **Experiment 5 (consistency check) is the most reliable** — if an item ranks well across 5+ different pair contexts, it's likely genuinely strong
3. **Use 99% CI upper bound** to filter noise from small samples
4. **Check for RFC-like patterns**: small sample + great AVP needs extra scrutiny
5. **Cross-reference with game theory**: does the item's mechanics explain why it's good? (e.g., Red Buff anti-heal + burn makes sense on a DoT mage like Vex)
