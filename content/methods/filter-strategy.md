# Filter Strategy
**Status**: ✅ verified

## Why Filtering is the Foundation

TFT match data is high-dimensional: comp, items, traits, rank, server, stage, augments...

Directly comparing aggregate statistics across these dimensions produces **Simpson's Paradox**: the same item can be BIS in one comp and terrible in another (e.g., Zoe's BIS flips between Rebel and Sorc — Dishsoap example).

In econometrics terms: you can't run an OLS regression without controlling for confounders and expect meaningful coefficients.

**Filter = controlling for confounders.**

## Filter Checklist

```
□ Lock composition: add trait + key unit filters
□ Exclude interference: secondary carry 3-item, special game modes
□ Sanity check: Games tab — look at real games, verify no garbage
□ Preserve sample: don't overfilter below 1000 games
□ Consider rank: Plat+ for general, GM+ for optimization questions
□ Consider region: KR/NA/VN have different metas
```

## Techniques

### Add Context First (Dishsoap)
Don't search "Zoe items". Search "7 Rebel Zoe items" or "6 Sorc Zoe items".

### Exclude → Toggle On (morbrid)
To measure how important a category of items is (e.g., anti-heal):
1. Exclude all anti-heal items (Red Buff, Morello, Sunfire)
2. Note the AVP without any anti-heal
3. Toggle them back on one by one
4. The AVP jump = importance of that category

### Games Tab Sanity Check (morbrid)
After setting filters, always check the Games tab:
- Are these the kinds of games you want to analyze?
- Any Golden Ox / cash out / disconnected boards?
- Is the rank distribution what you expect?

Click a suspicious outlier → add to filter → look at its games → exclude if garbage.

### Don't Overfilter
Every filter reduces sample size. Three filters might be enough. Seven filters might leave you with 200 games and pure noise.

**The art is finding the minimum filters that isolate what you want to study.**

## Common Filters

| Filter | Purpose |
|---|---|
| Trait (e.g., N.O.V.A. ≥2) | Lock composition |
| Key units with 3 items | Ensure primary carry setup |
| Exclude specific units | Remove comp variants you don't want |
| Exclude 3-item secondary carry | Remove "winning so hard I itemize everyone" games |
| Rank (GM+) | See what good players do |
| Star level (don't specify) | morbrid: specifying stars introduces bias |

## Sources
- [[sources/dishsoap-frodan-stats]]: "Add context first", don't just put the unit in
- [[sources/morbrid-aesah-talk]]: Games tab, exclude→toggle, don't overfilter
- [[sources/aesah-data-mistakes]]: Filter to see primary carry items
