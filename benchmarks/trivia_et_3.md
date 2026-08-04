# Mälumäng / Trivia Hard (`trivia_et_3`)

> Canonical description for the `trivia_et_3` benchmark, referenced from `benchmarks.json` (`description_url`). Mirrored in the leaderboard UI at `leaderboard-ui/src/content/benchmarks/trivia_et_3.tsx` — when editing, keep the two in sync. This file is the canonical copy.

**Category tags:** `knowledge`
**Source repo:** [keeleinstituut/trivia-bench-3](https://github.com/keeleinstituut/trivia-bench-3)
**Language coverage:** Estonian
**Item count:** 800 open-answer questions (80 per topic across 10 topics)
**Metric:** percentage of correct answers, 0–100, higher is better

## What it measures

Factual knowledge about Estonia across politics, history, sports, nature, geography, literature, the Estonian language, art, music, and miscellany. Unlike *Eesti mäng* (`trivia_et_2`), questions are open-answer rather than multiple-choice.

Example questions translated to English:

- *"What does the South Estonian word 'kõgekogo' mean? The word was coined by the philosopher of science Enn Kasak."*
- *"The world's most common surname is Li. In China alone nearly 100 million people are said to bear it. If 'Li' is translated into Estonian, it turns out that many people in Estonia carry this surname too. What is the Estonian equivalent of Li?"*
- *"The current Riigikogu (Estonia's parliament) has 101 members. How many members did the Riigikogu have under the constitution adopted in 1920?"*

Questions are evenly distributed — 80 questions in each of the 10 topics:

- **History** — 80
- **Politics** — 80
- **Geography** — 80
- **Nature** — 80
- **Sports** — 80
- **Estonian language** — 80
- **Literature** — 80
- **Art** — 80
- **Music** — 80
- **Miscellaneous** — 80

## Question selection

Questions are drawn from *Mälumänguraamat: 5555 küsimust ja vastust Eestist*, parts I and II (compiled by Lembit Ainsoo and Uno Ainsoo, AS Eesti Meedia, 2017). Questions were chosen so that their correct answers are one or two words long. The final selection favours the "harder" questions: based on a trial run, questions that older models already answered correctly were excluded.

## Scoring

An answer counts as correct when the model answers exactly correctly (differences in upper and lower case are allowed). When the model's answer does not match the reference, a judge model (here GPT-5.4-nano) assesses whether the model's answer is correct. If the model's answer is verbose and does not reach a single clear conclusion within the allowed token budget, it is counted as incorrect. The final score is the share of correct answers across all 800 questions, also broken down by topic.

## Measurement scope

Models do not have access to web search or other tools during evaluation. Results reflect what the model has internalised about Estonia from its training data.
