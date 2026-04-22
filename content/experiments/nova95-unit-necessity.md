# Experiment: Which Units Actually Matter in Nova 95?
**Status**: ✅ Complete
**Date**: 2026-04-22
**Module**: 4 (Unit Evaluation — preview)

---

## The Question

Nova 95 has a core of Vex + items, but the surrounding 7 units vary wildly between games. **Which units are truly core (the comp suffers without them), and which are traps (popular but harmful)?**

We apply Unit Necessity — the same metric framework from Module 2, but applied to units instead of items.

## Chapter 1: The Full Necessity Ranking

**Filter**: Vex with 3 items (503,844 games, Overall AVP 4.112)

| Rank | Unit | Games | Play% | AVP | w/o AVP | Necessity | Delta |
|---|---|---|---|---|---|---|---|
| 1 | Blitzcrank | 372k | 74% | 3.90 | 4.71 | **+0.602** | -0.82 |
| 2 | Shen | 361k | 72% | 3.93 | 4.57 | **+0.455** | -0.63 |
| 3 | Morgana | 264k | 52% | 3.88 | 4.37 | **+0.254** | -0.49 |
| 4 | Sona | 128k | 25% | 3.74 | 4.24 | **+0.127** | -0.50 |
| 5 | Fiora | 239k | 47% | 3.99 | 4.22 | **+0.107** | -0.23 |
| 6 | Bard | 173k | 34% | 3.91 | 4.22 | **+0.104** | -0.30 |
| 7 | Aatrox | 197k | 39% | 3.96 | 4.21 | **+0.100** | -0.26 |
| ... | ... | ... | ... | ... | ... | ... | ... |
| 🔴 | Rammus | 176k | 35% | 4.27 | 4.03 | **-0.084** | +0.24 |
| 🔴 | TahmKench | 112k | 22% | 4.44 | 4.02 | **-0.094** | +0.43 |

**Blitzcrank is the single most important unit** — not Fiora, not Shen. When Blitz is absent, the comp's AVP plummets to 4.71 (almost a full placement worse). This is remarkable for a "support" unit.

**Rammus and TahmKench are traps** — both popular (35% and 22% play rate) but with negative necessity. The comp is *better off without them*.

## Chapter 2: The Rammus Mystery

Rammus at 35% play rate but -0.084 necessity is the most interesting finding. Why is a unit that a third of players use actually hurting the comp?

Direct comparison:
- **With Rammus**: 176,454 games, AVP **4.269**
- **Without Rammus**: 327,424 games, AVP **4.028**

That's a 0.24 AVP gap. But is Rammus causing the worse performance, or is Rammus a *marker* for a weaker board state?

### Board Composition Shifts

When Rammus is present, the entire board looks different:

| Unit | With Rammus | Without Rammus | Shift |
|---|---|---|---|
| Bard | 65.5% | 17.4% | **+48.1pp** |
| Karma | 58.6% | 20.6% | +38.0pp |
| Mordekaiser | 63.9% | 26.6% | +37.3pp |
| Shen | 82.4% | 66.0% | +16.5pp |
| Aatrox | 8.8% | 55.5% | **-46.6pp** |
| Akali | 8.6% | 55.8% | **-47.3pp** |
| Nunu | 29.9% | 73.1% | **-43.2pp** |
| Fiora | 23.2% | 60.6% | -37.4pp |
| Morgana | 35.9% | 61.3% | -25.4pp |

**Rammus boards are a completely different variant.** They run Bard/Karma/Mordekaiser/Rammus/Shen as the shell, dropping Nunu/Fiora/Aatrox/Akali. This looks like a "budget" or "level 7" version — using cheaper, easier-to-find units instead of the premium core.

**Rammus isn't bad because Rammus is bad.** Rammus is a marker for boards that couldn't find (or afford) the premium units. This is Simpson's Paradox in action — Rammus doesn't make the comp worse; the weaker board state that leads to using Rammus makes the comp worse.

## Chapter 3: The TahmKench Trap

TahmKench is even more negative (-0.094) at 22% play rate:
- **With TahmKench**: 111,552 games, AVP **4.443**
- **Without TahmKench**: 392,325 games, AVP **4.018**

That's a 0.43 gap — twice as bad as Rammus. TahmKench at 22% is likely a "desperate frontline" when players can't find Blitz/Shen/Morgana.

## Chapter 4: The Blitzcrank Supremacy

Blitzcrank's numbers are extraordinary:
- **With Blitz**: 372,209 games, AVP **3.899**
- **Without Blitz**: 131,665 games, AVP **4.714**

The 0.815 gap is massive. But again — the same causal question applies. Is Blitz the reason, or does "having Blitz" correlate with "having a complete board"?

The Necessity metric partly accounts for this through play rate weighting. At 74% play rate, Blitz is nearly universal — yet its AVP is still 0.21 better than the overall. The w/o group (26% of games) performs terribly. This suggests Blitz is genuinely core, not just a correlation.

**Blitz's Necessity (+0.602) is 2.4x Shen's (+0.455)** despite similar play rates (74% vs 72%). Blitz contributes something unique that Shen cannot substitute for.

## Chapter 5: Sona — The Hidden Gem

Sona at 25% play rate has Necessity +0.127 and the **best AVP of any unit** (3.74). Her Delta (-0.50) is also strong. But she's only in 25% of games.

This smells like the item-level finding from Module 2: Sona could be genuinely good *but under-built*, or Sona could be a "highroll marker" (players who find Sona are already ahead). At 25% play rate, the Necessity metric suppresses carousel-like bias but doesn't eliminate it.

## Chapter 6: Graves — The Invisible Carry

Graves is in the filter (part of the OR group for Nova 95), at 45% play rate but Necessity ≈ 0 (-0.003). This means Graves is a **neutral slot** — games with Graves perform the same as without. Graves is likely an alternative carry that some players flex into, but doesn't define the comp's success.

## What I Learned

1. **Unit Necessity works beautifully** — it cleanly separates core (Blitz/Shen/Morgana) from traps (Rammus/TahmKench) despite both groups having high play rates
2. **High play rate ≠ high necessity** — Rammus (35%) and Nunu (58%) are popular but contribute little/nothing
3. **Negative necessity units are variant markers** — Rammus doesn't make the comp worse; it marks a weaker variant (budget frontline). This is Simpson's Paradox applied to unit selection
4. **Support units can have higher necessity than carries** — Blitzcrank (+0.602) >> Fiora (+0.107), suggesting the shell matters more than the secondary carry
5. **The same bias concerns from item analysis apply to units** — but with higher play rates, the signal is stronger

## Open Questions

- [ ] What traits do Rammus boards activate vs non-Rammus boards? (Is it a Bastion variant?)
- [ ] Can we use Sona's low play rate + high performance to test if she's genuinely under-built?
- [ ] Blitz's hook mechanic disrupts enemy positioning — is there a way to measure displacement value from data?
- [ ] How does this ranking compare with tftable's unit priority for Nova 95?

## Questions for Xing

1. **Rammus as variant marker**: I found that Rammus boards run a completely different shell (Bard/Karma/Morde instead of Nunu/Fiora/Akali). Is there a standard term for this? "Confounded by composition variant" feels clumsy. In clinical trials this would be like discovering your "treatment group" is actually a different patient population.

2. **Blitz > Shen in Necessity despite similar play rates**: Both are ~73% play rate, but Blitz's Necessity is 2.4x higher. This means Blitz's AVP impact is much stronger. Is this strong enough evidence to say "Blitz is more important than Shen," or could there be a confound I'm missing?

3. **Unit Necessity vs tftable's unitPriority**: tftable shows unit priority for comps. How does their method differ from what we computed here? Is it the same underlying math, or do they use a different approach?

---

## Sources
- MetaTFT Explorer API: total, units_unique (with/without unit filters)
- [[concepts/metrics]] — Necessity formula
- [[experiments/vex-nova95]] — same metric framework applied to items
- [[experiments/nova-trait-breakpoint]] — "universal improvement = bias" test
