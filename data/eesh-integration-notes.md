# EESH Data Integration — Notes (this Part)

Source: Grok EESH analysis (2021 multi-variation, 2020 compilation, 2019
Variation A). The source's own stated limitation applies throughout —
**no official answer keys were present**, so `correctAnswer` is set to
`"Not provided in source PDF"` on all 164 rows. No answer was invented
or inferred.

## Row counts populated
| File | Rows |
|---|---|
| eesh-grammar.json | 50 |
| eesh-vocabulary.json | 45 |
| eesh-reading.json | 12 |
| eesh-communication.json | 8 |
| eesh-part2.json | 10 |
| eesh-tricks.json | 11 |
| eesh-highyield.json | 20 |
| eesh-years.json | 8 |
| **Total** | **164** |

## sourceStatus breakdown
- `source-observed`: 120 rows — topic/pattern/points content taken
  directly from explicit statements in the analysis (e.g. per-question
  examples, confirmed uniform point values like "12x1=12").
- `inferred`: 44 rows — used only where:
  - 2021/2020 Grammar per-question **points** required mapping a
    numbered example (Q1, Q2…) onto a stated point-subgroup (A/B/C/D)
    whose exact question-number boundaries weren't spelled out
    verbatim, even though the subgroup counts match the question range
    exactly (e.g. 2021 Grammar A6+B6+C4+D3 = 19 = Q1–19).
  - 2021 B/C/D and 2020 B/C exam variations, which the source notes
    exist but only details structurally for Variation A ("nearly
    identical" / "visible" but not itemized).
  - One High-Yield Reading row (Purpose / Vocabulary in context),
    where a priority tier wasn't explicitly named in the source's
    MUST MASTER / HIGH / MEDIUM / LOW map and had to be placed based
    on its relative ranking position instead.
- `verified`: 0 rows (by design — no answer key exists to confirm any
  row against).

Every row also carries a `note` field (outside the required schema)
spelling out exactly which part of that row was directly stated vs.
positionally inferred, so nothing here is a "confirmed fact" not
already flagged as such in the row itself.

## What was intentionally left out
- No new question bank, lesson, or practice content was created —
  only structural/analytical data.
- No content for years/variations the source didn't independently
  detail (2021 B/C/D, 2020 B/C) beyond noting their existence.
- The existing ЕЭШ view UI, Level Test, Grammar, Vocabulary, Progress,
  and Roadmap systems were not touched. The main HTML file is
  byte-identical to the previous Part's output — only the `data/eesh-*.json`
  files changed.

## Validation
Every row was run through a Python replica of the app's exact
`eeshValidateRow`/`eeshValidateCategory` logic (required fields, array
fields, enum checks, mandatory `sourceStatus`) before being shipped.
Result: 164/164 rows pass with zero rejections.
