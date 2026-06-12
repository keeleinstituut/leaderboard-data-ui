# Keelenõu / Language Advice (`keelenou`)

> Canonical description for the `keelenou` benchmark, referenced from `benchmarks.json` (`description_url`). Mirrored in the leaderboard UI at `leaderboard-ui/src/content/benchmarks/keelenou.tsx` — when editing, keep the two in sync. This file is the canonical copy.

**Category tags:** `language`
**Source repo:** [keeleinstituut/keelenou-bench](https://github.com/keeleinstituut/keelenou-bench)
**Language coverage:** Estonian
**Item count:** 240 questions
**Metric:** percentage of correct answers, 0–100, higher is better

## What it measures

How well models can answer different types of questions about Estonian spelling, inflectional forms, word choice, and other language-norm areas. The questions are based on authentic queries submitted by users to EKI's [language advice service](https://eki.ee/keeleinfo/keelenou/annamekeelenou/). A 100% result would mean the model answers questions about Estonian as well as a human language expert.

The benchmark contains 240 questions across four task types:

- **true/false** — single decision
- **multiple-choice** — weigh alternatives
- **short-answer** — reply with the right word or word form
- **open-ended** — model reasoning is compared with a language expert's answer

True/false and multiple-choice questions yield around 25% from random guessing alone.

## Methodology

For true/false and multiple-choice questions, the answer counts as correct when the model picks the right option. For short-answer questions, the model's answer is compared against the expected word or word form. For open-ended questions, a judge model evaluates the model's reasoning against the language advisor's reference answer. The final score is reported both as an overall correctness rate and broken down by question type.

## Measurement scope

Models do not have access to web search or other tools during evaluation. Results reflect what the model has internalised about Estonian from its training data.

## Data sources

Questions are based on authentic queries submitted to [EKI's language advice service](https://eki.ee/keeleinfo/keelenou/annamekeelenou/). Expert answers from the language advisors form the basis for the reference answers.
