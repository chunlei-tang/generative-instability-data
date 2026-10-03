# Revised 20-Run Experiments

This folder documents the revised experimental phase of the study.

## Models

- GPT-6 Astra Medium
- Gemini 3.1 Pro

## Repeated Runs

Each item was evaluated across 20 repeated runs.

The revised experiments were conducted through the models' user-facing interfaces between September 17 and September 21, 2026.

GPT-6 Astra was evaluated using the Medium reasoning setting. No separate reasoning setting was selected for Gemini 3.1 Pro.

No external browsing or auxiliary tools were enabled during inference. Temperature and top-p were not manually specified where these parameters were not exposed through the user-facing interface.

## Experimental Conditions

The revised experiments included:

- E1 baseline: conflict condition with structured evidentiary tension
- E1 intervention: conflict condition with structured evidence attribution
- E2 baseline: standardized condition without evidentiary contradiction

## Experimental Execution

For each repeated run, items were submitted using standardized batch prompts.

A new model session was initiated for each repeated run.

E1 items were submitted as standardized batches of 9 evidence packs, and E2 items were submitted as standardized batches of 50 items.

Models were instructed to evaluate each item independently and not to use information, reasoning, or conclusions from one item when answering another.

Models returned structured outputs using the predefined response schema.

## Decision Structure

Model responses were represented using a predefined structured output framework comprising three hierarchical decision levels represented by four analytical decision fields:

- `Policy_Decision` (Level 1: Policy framing)
- `Operational_Strategy` (Level 2: Operational implementation)
- `Operational_Interval` (Level 2: Operational implementation)
- `Evidence_Priority` (Level 3: Evidence attribution)

`Operational_Strategy` and `Operational_Interval` together represent operational implementation (Level 2).

## Primary Analysis

The revised 20-run experiments constitute the primary dataset used for the statistical analyses reported in the revised manuscript.

Variability was quantified using Shannon entropy separately across four analytical decision fields:

- `Policy_Decision`
- `Operational_Strategy`
- `Operational_Interval`
- `Evidence_Priority`

For the revised experiments, entropy was calculated separately for each item across 20 repeated runs and then summarized across items within each model and experimental condition.

Because the predefined response categories differed across analytical decision fields, normalized entropy was additionally calculated as `Hnorm = H/log2(K)`, where:

- `Policy_Decision`: K = 3
- `Operational_Strategy`: K = 3
- `Operational_Interval`: K = 4
- `Evidence_Priority`: K = 4

Raw and normalized entropy were both reported in the revised analyses.

Verbalized confidence was also analyzed using the model-generated `Confidence` score on a 0–100 scale.

## Evidence Attribution Intervention

The E1 intervention used the same evidence materials, structured output schema, and repeated-run protocol as the E1 baseline condition, with an additional requirement that models explicitly evaluate and prioritize the supplied evidence before selecting the final policy and operational recommendation.

Intervention effects were evaluated separately across:

- `Policy_Decision`
- `Operational_Strategy`
- `Operational_Interval`
- `Evidence_Priority`

Changes in entropy were used to characterize whether structured evidence attribution altered the magnitude or location of variability within the three-level decision hierarchy.

## Verbalized Confidence

The `Confidence` field represents a model-generated score and is treated as verbalized confidence.

It should not be interpreted as:

- a calibrated probability,
- a token-level uncertainty estimate,
- or a direct measure of epistemic uncertainty.

## Cross-Phase Comparison

Results from the revised 20-run experiments are compared descriptively with the initial 7-run experiments.

Because model versions, number of repeated runs, and execution protocols differed between phases, cross-phase differences should not be interpreted as causal estimates of improvement across model generations.
