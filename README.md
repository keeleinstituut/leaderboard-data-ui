# Leaderboard Data

Aggregated results from the [runner](https://github.com/keeleinstituut/leaderboard-runner), served to the [UI](https://github.com/keeleinstituut/leaderboard-ui) via GitHub raw URLs.

## Files

| File | Description |
| --- | --- |
| `models.json` | Model metadata (name, provider, parameters) |
| `benchmarks.json` | Benchmark metadata (name, description) |
| `results.json` | Aggregated scores per model per benchmark |
| `results.jsonl` | Individual run records |

## How it's updated

The runner's CI pushes here automatically after each full (non-limit) benchmark run. See [`run.yml`](https://github.com/keeleinstituut/leaderboard-runner/blob/main/.github/workflows/run.yml).
