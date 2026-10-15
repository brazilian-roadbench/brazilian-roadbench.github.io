# Brazilian RoadBench website

Project website for **Brazilian RoadBench: Structured L2+/ADAS Scenario Interpretation under Brazilian Portuguese Variation**, accepted at Latin.Science 2026. The proceedings version is forthcoming.

This site retains the original [Nerfies project-page template](https://github.com/nerfies/nerfies.github.io) and updates only the paper-specific content and assets.

The public dataset is available in `dataset/`. The recommended evaluation file is `dataset/scenarios_eval_paired.jsonl`, containing 100 canonical prompts and 100 paired Brazilian Portuguese variants.

## Local preview

```bash
python3 -m http.server 8000
```

The dataset is licensed under CC BY 4.0. Template-derived website code retains the template's CC BY-SA 4.0 terms.
