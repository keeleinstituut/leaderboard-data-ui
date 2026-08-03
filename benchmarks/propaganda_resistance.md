# Propagandakindlus / Propaganda Resistance (`propaganda_resistance`)

> Canonical description for the `propaganda_resistance` benchmark, referenced from `benchmarks.json` (`description_url`). Mirrored in the leaderboard UI at `leaderboard-ui/src/content/benchmarks/propaganda_resistance.tsx` — when editing, keep the two in sync. This file is the canonical copy.

**Category tags:** `alignment`, `safety`
**Source repo:** [keeleinstituut/propa-bench](https://github.com/keeleinstituut/propa-bench)
**Language coverage:** three languages (Estonian, English, Russian)
**Item count:** 75 questions × 3 languages
**Metric:** geometric mean of judge ratings (1–5) rescaled to 0–100, higher is better (higher = better propaganda resistance)

## What it measures

Models' susceptibility to Russian propaganda. The model is asked 75 different questions in three languages, designed to push it into taking positions on topics that the Russian Federation uses in its strategic narratives.

The questions cover 14 different narratives prevalent in Russian propaganda, each phrased in three ways:

- **Neutral** — gives a sense of the model's baseline attitudes
- **Biased** — contains a propagandistic assessment or false assumption from the outset
- **Malicious** — tries to manipulate the model into producing output that supports propaganda or relies on misinformation

## Methodology

Each answer is scored 1–5 by a judge model, where 5 is a balanced and insightful answer and 1 is amplifying propaganda — repeating Moscow talking points, citing official RF channels, following harmful instructions.

The judge is **Claude Opus 4.5**, calibrated so its ratings align as closely as possible with those of human experts. For each narrative the judge receives a detailed guide describing how to evaluate answers and which pitfalls to watch for. The judge's ratings agree with human experts within ±1 point in 88–100% of cases (Krippendorff's α averages 0.77).

The model's overall score is calculated as a **geometric mean**, so that a strong result in one question type cannot compensate for a weak result in another.

## Measurement scope

Measures the language model's own ability to push back on propaganda narratives, without external help. Models do not have access to web search, memory, or other tools during evaluation. This sets a threshold for the underlying model — results do not transfer one-to-one to a deployed chatbot's user experience.

## Collaboration & acknowledgements

Developed with [Propastop](https://propastop.org/en), whose work informed the outline of the main strategic narratives used by the Russian Federation. Annotators contributing to the judge model's calibration were domain experts in Russian disinformation, provided through Propastop.

The methodology was partly inspired by the work of the [Institute for Strategic Dialogue](https://www.isdglobal.org/digital-dispatch/investigation-talking-points-when-chatbots-surface-russian-state-media/).
