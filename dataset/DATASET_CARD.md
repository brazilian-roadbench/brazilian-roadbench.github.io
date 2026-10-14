# Dataset Card: Brazilian RoadBench

## Summary

Brazilian RoadBench is a text-only benchmark for Brazilian Portuguese L2+/ADAS road-safety scenario interpretation. It tests whether a language model can map short road-safety descriptions to structured reference labels covering context, actors, hazard, risk, ADAS function, and recommended driver-facing action.

The public benchmark contains 200 evaluation prompts: 100 reviewed canonical prompts and 100 GPT-drafted Brazilian variation prompts paired by scenario.

## Intended Use

Use this dataset to evaluate structured scenario interpretation and robustness to Brazilian Portuguese variation. The recommended input file is `data/scenarios_eval_paired.jsonl`.

## Out-of-Scope Use

Brazilian RoadBench is not an autonomous-driving control benchmark, not a perception benchmark, and not a safety validation suite for deployed ADAS systems. It should not be used to make claims about real-world vehicle control or perception performance.

## Data Composition

- 100 canonical scenarios.
- 100 GPT Brazilian variants.
- 8 scenario categories.
- 7 structured label fields per prompt.

Each canonical scenario has exactly one paired GPT Brazilian variant with copied reference labels.

## Generation and Review

Canonical scenarios were drafted with GPT-5.5 and manually reviewed. GPT-5.5 also drafted one Brazilian variant per canonical scenario. GPT-5.5 is not evaluated on the benchmark.

The generated scenarios are text-only and designed to be understandable without images, video, sensors, vehicle telemetry, or maps.

## Brazilian Portuguese Variation

Variants intentionally include realistic Brazilian linguistic and cultural variation when appropriate. Examples include informal traffic vocabulary, regional lexical markers, rural road references, and Brazilian road-infrastructure terms. The goal is robustness testing, not caricature.

## Reference Labels

Reference labels are intended for benchmark evaluation. They should be treated as paper/reference labels rather than operational driving instructions.

## Known Limitations

- The benchmark is synthetic and text-only.
- It contains 100 base scenarios, so statistical claims should be appropriately scoped.
- It focuses on structured interpretation, not perception or vehicle control.
- Driver-facing explanation quality may require separate human evaluation beyond structured label accuracy.

## License

CC BY 4.0. See `LICENSE`.
