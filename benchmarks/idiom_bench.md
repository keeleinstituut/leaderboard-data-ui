# Kujundlikud väljendid / Idioms (`idiom_bench`)

> Canonical description for the `idiom_bench` benchmark, referenced from `benchmarks.json` (`description_url`). Mirrored in the leaderboard UI at `leaderboard-ui/src/content/benchmarks/idiom_bench.tsx` — when editing, keep the two in sync. This file is the canonical copy.

**Category tags:** `language`
**Source repo:** [keeleinstituut/idiom-bench](https://github.com/keeleinstituut/idiom-bench)
**Language coverage:** Estonian
**Item count:** 300 fill-in-the-blank tasks
**Metric:** percentage of correct answers, 0–100, higher is better

## What it measures

How well models master figurative language: metaphors, phraseologisms, and fixed expressions. Each task gives the model a sentence with one or more words replaced by a blank, plus a hint describing the intended meaning. The model must fill the blank with the word or phrase that restores the original idiom or expression.

The 300 tasks contain three kinds of figurative expressions:

- **Estonian-specific** — known to occur only in Estonian
- **Universal** — appearing with minor variations across multiple languages
- **Ambiguous** — resembling an expression used in another language, but not directly transferable

Examples:

- *"Kõik tegijad on sellised, et ____ üks ja ____ teist."* — both equally bad — Estonian-specific
- *"Nende sinelid on sõjas ____põhjaks muutunud."* — to become full of holes — ambiguous
- *"Mul oli küll võimalus volinike ees esineda, kuid ma rääkisin nagu ____."* — speaking to no reaction — universal

## Methodology

An answer counts as correct when the model produces the expected word or phrase in exactly the right form, or supplies another word that fits both semantically and grammatically. Accepted answer variants were vetted by EKI linguists.

A grammatically inappropriate form is wrong. Modifying the given sentence — changing word order, sentence length, or substituting other words — is not allowed. The final score reflects the share of correct answers across all 300 tasks and is broken down by expression type, showing whether the model handles universal or distinctively Estonian figures better.

## Measurement scope

Models do not have access to web search or other tools during evaluation. Results reflect what the model has internalised about Estonian figurative language from its training data.

## Data sources

Compiled using the *Fraseoloogiasõnaraamat* (Asta Õim, Eesti Keele Sihtasutus, Tallinn 2000) and the [EKI Combined Dictionary](https://xn--snaveeb-10a.ee/collections#dataset-eki).
