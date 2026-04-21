# Experiment: Vex Items in Nova 95
**Status**: 🧪 In Progress
**Date**: 2026-04-21
**Authors**: Xing + Mochi

---

## The Question

What are Vex's best items in the Nova 95 composition?

This sounds simple. It isn't. The journey to answer it taught us more about **how to think about TFT stats** than about Vex's actual BIS.

---

## Chapter 1: The Naive Approach

We started where everyone starts — pull Vex's item data from MetaTFT, sort by AVP.

```
Guinsoo's Rageblade    175,826 games   AVP 4.05
Giant Slayer            72,779         AVP 3.99
Hextech Gunblade        56,575         AVP 3.94
Striker's Flail         32,391         AVP 3.78
Rabadon's Deathcap      19,021         AVP 3.74
Red Buff                15,171         AVP 3.67  ← "best"?
```

Red Buff looks like the best item on Vex. But something's off — only 15k games vs Guinsoo's 175k. Why is the least-built item the "best"?

**Enter survivorship bias.** We'd just read morbrid's Reddit post ([[sources/morbrid-reddit-post]]) explaining that low play rate items get inflated AVP because they're often picked up from late-game carousels — and you only reach late game if you're already winning.

**Lesson 1: Raw AVP is useless for cross-item comparison.** ❌

---

## Chapter 2: Can We Isolate an Item's Real Contribution?

If raw single-item AVP is contaminated, what if we **hold other variables constant** — like a science experiment?

Dishsoap's advice ([[sources/dishsoap-frodan-stats]]): "Look at item combos and full builds — that knocks out a lot of the bias."

The idea: if we compare complete three-item builds, everyone in the comparison has a fully-itemized Vex. No one got Red Buff from a late carousel while already winning — they all have three items. That removes a big chunk of survivorship bias.

But there's a problem: with 57 different builds above 200 games, we can't compare them all at once. So we borrowed from experimental design — **fix two items, vary one.** Same base, different treatment. If Guinsoo + Giant Slayer is the base:

```
Guinsoo + Giant Slayer + ???
Red Buff          2,408 games   AVP 3.48
2× Guinsoo        3,577         AVP 3.67
Dcap              4,026         AVP 3.69
Flail             7,896         AVP 3.78
Gunblade         17,815         AVP 3.89
JG                9,423         AVP 4.04
```

Red Buff still #1. But is it real? Two concerns:
1. Only 2,408 games — could be noise
2. We're only looking at **one** base pair — what if Red Buff is only good with Guinsoo + Giant Slayer specifically?

To answer this, we need to check: **does the ranking hold across different base pairs?**

---

## Chapter 3: The Consistency Check

This became our most convincing experiment. For each item, we asked: across all the base pairs where it appears, what's its average rank percentile?

```
Item          #Pairs  Avg Rank%  Verdict
Red Buff         7     10.9%     ✅ #1 in every pair
Dcap             8     17.4%     ✅ Top 2 almost everywhere
Flail            9     38.5%     ⚠️ Above average
Gunblade         9     63.7%     — Average
Giant Slayer    11     65.2%     — Average
JG               9     83.3%     ❌ Consistently weak
Void Staff       8     95.1%     ❌ Consistently last
```

Red Buff is #1 in **every single** base pair. That's hard to explain with bias alone. Dcap is similarly consistent.

But wait — survivorship bias can still exist within builds. A build with Red Buff might still be more likely to appear on late-game boards.

---

## Chapter 4: The Aesah Method (Play Rate Weighting)

Then we learned from Aesah ([[sources/aesah-data-mistakes]]) a much simpler approach: **weight by play rate**.

```
no_item_AVP = (overall - p × item_AVP) / (1 - p)
Necessity = no_item_AVP - overall
```

After fixing a bug where we calculated overall_AVP from items (double-counting!) instead of from the unit directly, we got:

```
Item              Rate   AVP   Edge  Necessity
Guinsoo           88%   4.05  +0.06  +0.443   ← Most important by far
Giant Slayer      36%   3.98  +0.13  +0.072
Gunblade          28%   3.94  +0.17  +0.069
Flail             16%   3.78  +0.33  +0.063
Dcap              10%   3.74  +0.37  +0.039
Red Buff           7%   3.67  +0.44  +0.036
```

This tells a completely different story. **Guinsoo is the most important item** (Necessity +0.443) — without it, Vex's AVP drops from 4.05 to ~4.55, nearly half a placement. Red Buff? Necessity only +0.036.

---

## Chapter 5: What We Learned

### The methods disagree — and that's informative

| Method | Winner | What it measures |
|---|---|---|
| Raw AVP | Red Buff (3.67) | Contaminated by survivorship bias |
| Control Variable | Red Buff (consistent #1) | Best item **given you already have 2 good items** |
| Necessity | Guinsoo (+0.443) | Most important item for the comp to function |

These aren't contradictory. They answer different questions:
- **Necessity** answers: "What's the most critical item?" → Guinsoo (core identity)
- **Consistency check** answers: "What's the best marginal item?" → Red Buff / Dcap (best 3rd item)
- **Raw AVP** answers: nothing useful ❌

### Open problems

1. **Survivorship bias in builds**: Even the control variable method may be contaminated. A three-item build with Red Buff might disproportionately appear on late-game boards. We don't have a way to control for game stage.

2. **Edge vs Necessity**: We proposed Edge (`overall - w/`) as a "fairer" version of Delta. But its practical advantage over standard Delta is unproven. Need more experiments across different comps.

3. **Missing dimension — filter quality**: We filtered for nova_95 but didn't check the Games tab (morbrid's advice). Are there Golden Ox games? Cash out games? Are some of these Vex-as-secondary-carry games?

4. **Sample size for builds**: Many three-item builds have only 200-2000 games. The CI is wide. Are the consistency check results robust to CI?

5. **The Frequency-AVP regression**: morbrid's graph view method could directly model the survivorship bias curve. We haven't tried it yet.

---

## Next Steps

- [ ] Add Frequency-AVP regression analysis
- [ ] Games tab sanity check on the nova_95 filter
- [ ] Repeat on 2-3 other comps to validate methodology
- [ ] Compare Edge vs Delta empirically across comps
- [ ] Add CI to consistency check results

---

## Sources
- [[sources/morbrid-reddit-post]] — Survivorship bias awareness
- [[sources/aesah-data-mistakes]] — Play rate weighted formula
- [[sources/dishsoap-frodan-stats]] — "Look at builds, not single items"
- [[sources/morbrid-aesah-talk]] — Games tab, graph view
- [[concepts/metrics]] — Edge, Necessity definitions
- [[concepts/biases]] — Three bias types
- [[concepts/framework]] — Three dimension framework
