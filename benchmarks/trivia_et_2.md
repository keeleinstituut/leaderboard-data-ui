# Eesti mäng / Trivia (`trivia_et_2`)

> Canonical description for the `trivia_et_2` benchmark, referenced from `benchmarks.json` (`description_url`). Mirrored in the leaderboard UI at `leaderboard-ui/src/content/benchmarks/trivia_et_2.tsx` — when editing, keep the two in sync. This file is the canonical copy.

**Category tags:** `knowledge`
**Source repo:** [keeleinstituut/trivia-bench-2](https://github.com/keeleinstituut/trivia-bench-2)
**Language coverage:** Estonian
**Item count:** 1000 multiple-choice questions
**Metric:** percentage of correct answers, 0–100, higher is better

## What it measures

Factual knowledge about Estonia — history, culture, sports, nature and geography, and miscellaneous topics. Each question is multiple-choice. Random guessing yields around 26%.

Question distribution across topics:

- **Miscellaneous** — 248
- **Culture** — 234
- **History** — 221
- **Nature & geography** — 159
- **Sports** — 138

## Methodology

An answer counts as correct when the model picks the right option. The final score is the share of correct answers across all 1000 questions, also broken down by topic.

## Measurement scope

Models do not have access to web search or other tools during evaluation. Results reflect what the model has internalised about Estonia from its training data.

## Data sources

Questions are drawn from the book *Eesti mäng: 35 mängu, 1050 küsimust* (compiled by Tiit Kuningas, Tammerraamat 2012). Questions whose answers have changed over time, or that were primarily topical at the time of the book's publication, were excluded.
