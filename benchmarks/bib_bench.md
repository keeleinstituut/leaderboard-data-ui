# Raamatusoovitused / Book Recommendations (`bib_bench`)

> Canonical description for the `bib_bench` benchmark, referenced from `benchmarks.json` (`description_url`). Mirrored in the leaderboard UI at `leaderboard-ui/src/content/benchmarks/bib_bench.tsx` — when editing, keep the two in sync. This file is the canonical copy.

**Category tags:** `knowledge`
**Source repo:** [keeleinstituut/bib-bench](https://github.com/keeleinstituut/bib-bench)
**Language coverage:** Estonian (the books are Estonian-language)
**Item count:** 40 prompts × 4 recommendations = 160 (title, author) pairs
**Metric:** percentage of recommendations that match a real book, 0–100, higher is better

## What it measures

How well a model sticks to real information when asked for Estonian book recommendations. A low score means the model confidently produces invented titles. A strong score points to a solid grasp of the Estonian literary canon — and possibly of Estonian culture more broadly.

The model is asked for 160 recommendations spread across 8 genres and 5 qualifying criteria. Each recommendation is checked against the [Estonian National Bibliography](https://doi.org/10.5334/johd.280) (~317,000 titles). Anything without a sufficiently close match in the data is counted as a hallucination.

**Genres:** fiction, poetry, history, crime, children's, popular science, biography, fantasy.
**Criteria:** classic, mainstream, lesser-known, recent, translated.

## Methodology

The model receives 40 prompts, each asking for 4 book recommendations in one genre and matching one criterion. Every recommendation must include both a title and an author.

Each recommendation is a (title, author) pair checked against the National Bibliography. It counts as correct when the title and the author's surname are sufficiently similar to a real record. If no author is given, the recommendation does not count — the test deliberately requires the model to commit to a specific author. Refusals, short answers, and over-long lists all reduce the score. The final score is the share of correct recommendations across all 160, broken down by genre and criterion.

## Measurement scope

Models do not have access to web search or other tools during evaluation. Results reflect what the model has internalised about Estonian-language books from its training data.

## Data sources

Recommendations are checked against the [Estonian National Bibliography](https://doi.org/10.5334/johd.280), which catalogues every book published in Estonian, in Estonia, or by Estonian authors.
