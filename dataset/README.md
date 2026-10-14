# Brazilian RoadBench Data

This directory contains the public benchmark data.

## Main Files

### `scenarios_canonical.jsonl`

Reviewed canonical scenarios. Each row has:

- `scenario_id`: stable scenario identifier, `S001` through `S100`.
- `canonical_prompt`: short Brazilian Portuguese scenario description.
- `road_context`: reference road context label.
- `primary_actor`: main actor involved in the hazard.
- `secondary_actor`: secondary actor, or `none` / `unknown`.
- `hazard_type`: main hazard class.
- `risk_level`: reference risk level.
- `adas_function`: relevant ADAS/L2+ function.
- `recommended_action`: driver-facing action class.
- `rationale`: short rationale for the reference labels.
- `category`: benchmark category.

### `scenarios_variants_gpt.jsonl`

One GPT-drafted Brazilian linguistic/cultural variant per canonical scenario. Each row has:

- `scenario_id`
- `variant_id`: `{scenario_id}_gpt_brazilian_variant`.
- `variant_type`: `gpt_brazilian_variant`.
- `prompt`: variant prompt in Brazilian Portuguese.
- `gold`: copied reference labels from the canonical scenario.
- `metadata`: variation metadata such as `variation_type`, `regional_markers`, `semantic_shift`, and `label_preservation_note`.

### `scenarios_eval_paired.jsonl`

Recommended evaluation file. It contains 200 rows:

- 100 rows with `prompt_type = "canonical"`.
- 100 rows with `prompt_type = "gpt_brazilian_variant"`.

Each row has:

- `eval_id`: unique evaluation row ID.
- `scenario_id`: parent scenario ID.
- `prompt_id`: prompt-specific ID.
- `prompt_type`: `canonical` or `gpt_brazilian_variant`.
- `prompt`: text to give to the model.
- `gold`: reference structured labels.
- `category`: benchmark category.
- `metadata`: source or variant metadata.

## Label Sets

### `risk_level`

- `low`
- `medium`
- `high`
- `critical`

### `road_context`

- `urban`
- `highway`
- `rural`
- `parking_or_low_speed`
- `unknown`

### `primary_actor` / `secondary_actor`

- `none`
- `pedestrian`
- `motorcycle`
- `cyclist`
- `heavy_vehicle`
- `bus`
- `car`
- `animal`
- `road_condition`
- `emergency_vehicle`
- `unknown`

### `hazard_type`

- `crossing`
- `occlusion`
- `stopped_vehicle`
- `vulnerable_road_user`
- `lane_filtering`
- `poor_road_surface`
- `poor_visibility`
- `animal_crossing`
- `cut_in`
- `tailgating`
- `ambiguous`
- `none`

### `adas_function`

- `driver_alert`
- `adaptive_cruise_control`
- `lane_keeping`
- `automatic_emergency_braking`
- `blind_spot_monitoring`
- `scenario_generation`
- `fleet_triage`
- `none`

### `recommended_action`

- `maintain_speed`
- `slow_down`
- `prepare_to_stop`
- `increase_distance`
- `change_lane`
- `alert_driver`
- `request_driver_attention`
- `none`

### `category`

- `pedestrian_vulnerable_road_user`
- `motorcycle_lane_filtering`
- `heavy_vehicle_bus_occlusion`
- `poor_road_surface`
- `weather_visibility`
- `rural_animals_tractors`
- `urban_traffic_disorder`
- `low_risk_ambiguous`

## Notes On Brazilian Variation

The GPT Brazilian variants intentionally include grounded Brazilian lexical and cultural variation where appropriate, such as `moto`, `motoboy`, `carreta`, `quebra-molas`, `beira da pista`, rural animal references, and occasional regional ambiguity. These variants are deliberate robustness stress tests, not dialect parody.

## Loading Example

```python
import json
from pathlib import Path

with Path("data/scenarios_eval_paired.jsonl").open(encoding="utf-8") as f:
    for line in f:
        record = json.loads(line)
        prompt = record["prompt"]
        reference = record["gold"]
        break
```
