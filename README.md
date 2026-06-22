# Leaderboard data

Source data for **Keelemudelite mõõdupuu** — Independent LLM leaderboard for Estonian by the Institute of the Estonian Language

* **Live site:** [https://moodupuu.eki.ee](https://moodupuu.eki.ee)
* **License:** [CC BY 4.0](LICENSE) — free to share and adapt, including commercially, with attribution

> **Attribution.** This data is © [Eesti Keele Instituut (Institute of the Estonian Language)](https://www.eki.ee) and licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). You are free to share and adapt it for any purpose, provided you give appropriate credit and link to the license. Suggested credit:
>
> > *Keelemudelite mõõdupuu: Independent LLM leaderboard for Estonian.* Eesti Keele Instituut. https://moodupuu.eki.ee — licensed under CC BY 4.0.

## Quick start for agents

|You want…|Fetch this|
|-|-|
|A flat table (one row per model)|[`summary.csv`](summary.csv) — model\_id, provider, release\_date, overall, per-benchmark scores|
|What each benchmark measures|[`benchmarks/{id}.md`](benchmarks/) — full description, methodology, metric, sources|
|Model metadata|[`models.json`](models.json) — id, name, provider, release date, tags|
|Benchmark registry|[`benchmarks.json`](benchmarks.json) — id, bilingual names, tags, pointer to per-benchmark Markdown|
|Detailed nested scores incl. category breakdowns|[`results.json`](results.json) (≈290 KB; truncates in GitHub's HTML viewer past line 1000)|
|Raw run records, one per (model, benchmark)|[`results.jsonl`](results.jsonl)|

Raw base URL: `https://raw.githubusercontent.com/keeleinstituut/leaderboard-data-ui/main/`

## Aggregation rule

`overall` is the **unweighted arithmetic mean** of a model's per-benchmark scores, computed over whatever benchmarks the model has been run on. Models missing some benchmarks are **not penalised** — they are averaged over only what they ran.

Use `benchmarks\_covered` in `summary.csv` (or `len(scores)` in `results.json`) to filter out partial runs if you want like-for-like comparisons.

## Schema

### `models.json`

Array of model entries.

```json
{
  "id": "openai/gpt-5.5",
  "name": "GPT-5.5",
  "provider": "OpenAI",
  "release": "2026-04-23",
  "tags": ["open"]
}
```

|Field|Type|Notes|
|-|-|-|
|`id`|string|OpenRouter-format id; stable key joining models ↔ results|
|`name`|string|Display name|
|`provider`|string|OpenAI, Anthropic, Google, etc.|
|`release`|string|ISO 8601 date (`YYYY-MM-DD`). Optional.|
|`tags`|string\[]|Optional. Currently used: `open` for open-weights models.|

### `benchmarks.json`

Array of benchmark entries. Only benchmarks that have at least one result appear here.

```json
{
  "id": "keelenou",
  "name_en": "Language Advice",
  "name_et": "Keelenõu",
  "tags": ["language"],
  "description_url": "benchmarks/keelenou.md",
  "description_short_en": "240 Estonian language-norm questions sourced from EKI's language advice service…",
  "description_short_et": "240 eesti keele õigekeelsuse küsimust EKI keelenõuandest…"
}
```

|Field|Type|Notes|
|-|-|-|
|`id`|string|Stable key joining benchmarks ↔ results|
|`name\_en` / `name\_et`|string|Display names|
|`tags`|string\[]|Optional. Currently used: `language`, `knowledge`, `alignment`, `safety`.|
|`description\_url`|string|Relative path to a Markdown file with full description and methodology|
|`description\_short\_en` / `description\_short\_et`|string|One-sentence summary for inline rendering|

### `summary.csv`

One row per model that has at least one result. Columns in order:

```
model_id, name, provider, release_date, tags, overall, benchmarks_covered,
<benchmark_id_1>, <benchmark_id_2>, …
```

* `tags` is a space-separated string (`""` if no tags). E.g. `open` or `open beta`.
* Per-benchmark cells are floats (percent or geometric-mean score, 0–100). Empty cell = the model was not evaluated on that benchmark. **Do not treat empty as zero.**
* `benchmarks\_covered` is the count of non-empty per-benchmark cells.
* Rows sorted by `overall` descending.

### `results.json`

Array of per-model entries, sorted by `overall` descending.

```json
{
  "modelId": "openai/gpt-5.5",
  "scores": { "keelenou": 65.21, "bib_bench": 75.44, ... },
  "overall": 72.98,
  "details": { "keelenou": { "by_type": { "mcq": 88.0, ... } }, ... }
}
```

|Field|Type|Notes|
|-|-|-|
|`modelId`|string|Joins to `models.json` `id`|
|`scores`|object|benchmark\_id → score (0–100)|
|`overall`|number|Mean of `scores.values()`. See aggregation rule above.|
|`details`|object|Optional. benchmark\_id → benchmark-defined breakdown (categories, topics, types). Schema varies per benchmark.|

### `results.jsonl`

One JSON object per line — one record per (model, benchmark) run. Useful for streaming and for tracking when each evaluation happened.

```json
{"model_id": "openai/gpt-3.5-turbo", "benchmark_id": "trivia_et_2", "score": 35.3, "timestamp": "2026-04-07T12:21:22Z", "details": {...}}
```

|Field|Type|Notes|
|-|-|-|
|`model\_id`|string|Joins to `models.json` `id`|
|`benchmark\_id`|string|Joins to `benchmarks.json` `id`|
|`score`|number|0–100|
|`timestamp`|string|ISO 8601 UTC|
|`details`|object|Optional benchmark-defined breakdown|
|`partial`|boolean|Optional. `true` if some LLM calls errored during the run.|

### `benchmarks/{id}.md`

Plain Markdown — one file per benchmark `id`, with title, what-it-measures, methodology, metric, language coverage, item count, and source link. These are the canonical descriptions; the leaderboard UI mirrors the same prose in JSX for display.

## How updates happen

EKI's custom runner CI pushes `models.json`, `benchmarks.json`, `results.json`, `results.jsonl`, and `summary.csv` here automatically after each full (non-limit) benchmark run. The runner does **not** overwrite per-benchmark Markdown files or any extra fields in `benchmarks.json` it doesn't own — those are authored directly in this repo.

## License \& citation

This data is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). You are free to share and adapt it for any purpose, including commercially, provided you give appropriate credit, link to the license, and indicate if changes were made.

Suggested citation:

> *Keelemudelite mõõdupuu: Independent LLM leaderboard for Estonian.* Eesti Keele Instituut (Institute of the Estonian Language). https://moodupuu.eki.ee — licensed under CC BY 4.0.

For questions about reuse or collaboration, contact [Eesti Keele Instituut](https://www.eki.ee).

