# TFT Data Science Wiki — Change Log

Append-only chronological record. Parseable with: `grep "^## \[" log.md | tail -5`

---

## [2026-04-21] init | Wiki created
- Architecture: Karpathy LLM Wiki pattern (3 layers)
- Folders: concepts/, methods/, tools/, sources/, experiments/, people/
- Contributors: Xing, Mochi

## [2026-04-21] ingest | morbrid Reddit Post
- Source: Reddit post on sample size, CI, biases
- Pages created: sources/morbrid-reddit-post
- Pages updated: concepts/biases, concepts/metrics

## [2026-04-21] ingest | Aesah "Avoid These Data Mistakes"
- Source: YouTube video transcript
- Pages created: sources/aesah-data-mistakes
- Pages updated: concepts/metrics (Edge, Necessity derivation)

## [2026-04-21] ingest | morbrid + Aesah Live Session
- Source: YouTube live session transcript
- Pages created: sources/morbrid-aesah-talk
- Pages updated: concepts/biases, methods/filter-strategy (exclude→toggle, graph view)

## [2026-04-21] ingest | Dishsoap + Frodan "How to Climb with Stats"
- Source: YouTube video transcript (TFT Study Hall)
- Pages created: sources/dishsoap-frodan-stats
- Pages updated: methods/filter-strategy, methods/build-analysis

## [2026-04-21] experiment | Vex Items in Nova 95
- 5 analysis methods compared on same dataset
- Result: consistency check (cross-pair ranking) most reliable
- Pages created: experiments/vex-nova95 (pending migration)
- Pages updated: methods/build-analysis

## [2026-04-21] concept | Edge metric proposed
- Formula: overall_AVP - item_AVP (fair baseline, no w/o dependency)
- Status: 🧪 exploring — needs cross-validation on more comps
- Pages updated: concepts/metrics

## [2026-04-21] tool | metatft_query.py updated
- Added Edge + Necessity columns to items output
- Fixed overall_AVP bug (was using items weighted avg, now uses units_unique)
- Pages updated: tools/metatft-api
