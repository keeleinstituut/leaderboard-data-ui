# Oskussõnavara / Terminology (`term_bench`)

> Canonical description for the `term_bench` benchmark, referenced from `benchmarks.json` (`description_url`). Mirrored in the leaderboard UI at `leaderboard-ui/src/content/benchmarks/term_bench.tsx` — when editing, keep the two in sync. This file is the canonical copy.

**Category tags:** `language`
**Source repo:** [keeleinstituut/term-bench](https://github.com/keeleinstituut/term-bench)
**Language coverage:** Estonian, 46 specialist fields
**Item count:** 1380 questions (30 terms × 46 fields)
**Metric:** percentage of correct answers, 0–100, higher is better

## What it measures

How well models understand Estonian terminology across 46 fields, from construction and electrical engineering to folklore, politics, and medicine. Each question gives the model a definition and the name of the field; the model must respond with the appropriate term or an accepted synonym.

## Methodology

An answer is correct when the model produces the term exactly as it appears in the term collection, or uses any registered synonym (including abbreviations). The final score is the share of correct answers across all 1380 questions, also broken down by field.

Models are instructed to return a **single** term; offering an additional synonym alongside is not rewarded.

## Measurement scope

Measures the model's ability to match a definition to the right term without external help. Models do not have access to web search or other tools during evaluation. Results reflect what the model has internalised about Estonian terminology from its training data. The test samples 30 terms per field; it does not cover every term in every field.

## Data sources

The benchmark draws on EKI's [Esterm](https://xn--snaveeb-10a.ee/en/collections#dataset-esterm) term base and [field-specific term collections](https://xn--snaveeb-10a.ee/en/collections) compiled by subject-matter experts. The specific terms for the test were selected together with EKI terminologists.
