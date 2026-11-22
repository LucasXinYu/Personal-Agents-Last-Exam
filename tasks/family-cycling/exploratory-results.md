# Separate exploratory calibration (2026-11-21)

This is a different, ten-event/ten-candidate extension, not the approved two-session task. Four preselected history variants of one synthetic family were evaluated with separate sealed memory (M), relevance (R), and ranking (K) stages. Fresh context per stage; original sources remained retrievable. All variants and events are correlated, not independent user samples.

GPT configuration: gpt-6.2-astra, high, signed-in Codex CLI; 40 events / 120 stage submissions completed. No native tool calls, future records or receipt mismatches were found. Local CPU orchestrated and scored remote model inference. The model received no private labels or scores.

| Metric | Raw % | Declared random % | Relative to random % |
| --- | ---: | ---: | ---: |
| Historical memory value accuracy | 100 | 42.3889 | 100 |
| Per-card 0–4 grade agreement | 78 | 20 | 72.5 |
| Strict-pair ranking agreement | 97.8601 | 50 | 95.7202 |
| Whole-list exact (ties allowed) | 67.5 (27/40) | 0.080853 | 67.4737 |
| nDCG | 99.7339 | 67.1167 | 99.1907 |

Relative improvement = 100 × (mean raw − matching mean random)/(100 − matching mean random), with negatives retained. No weighted total is introduced. Always predicting grade zero gives 42%, a stronger trivial grade baseline than uniform guessing. The three-stage exact conjunction is 6/40; it has no invented random-prose baseline and is not an official pass rate.

164/164 historical values were correct; 156 citations matched known sufficient source sets and 8 required further review. All 400 per-card reasons still need independent semantic review. Changed/invariant state-pair checks were 5/5 and 31/31. All 40 R stages read the current M artifact; all 40 K stages read R. Access does not establish causal reliance.

The result does not establish adequate difficulty. Of 88 grade mismatches, 83 differed by one grade; examples include another-day references scored 1 versus 0, or useful equipment checks scored 3 versus 4. Larger gaps also involved judging a backup that does not satisfy the child's explicit quick-release preference. These boundaries need independent adjudication. Correct fact retrieval plus ambiguous grade matching must not be presented as a new reasoning failure.

On exactly the same 40 case/events, the previous ranking-only protocol achieved 80% whole-list exactness versus 67.5% here; the protocol changed, so this is descriptive, not a causal difficulty claim. Old runs have no retrospective M/R scores.

Claude Opus 5.5 Extra blind evaluation resumed after its provider quota reset. Coverage and results will be reported only for actually sealed, transport-verified stages; the planned matrix is four worlds / 40 events. These are exploratory provider-access runs, not the official designated GPT/Claude/Gemini validation roster. No acceptance or 50% difficulty target is claimed.
