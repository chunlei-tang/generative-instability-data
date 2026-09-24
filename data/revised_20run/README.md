# Revised 20-Run Experiments

This folder documents the revised experimental phase of the study.

## Models

- GPT-6 Astra Medium
- Gemini 3.1 Pro

## Repeated Runs

Each item was evaluated across 20 repeated runs.

## Experimental Conditions

The revised experiments included:

- E1 baseline: conflicting evidence condition
- E1 intervention: conflicting evidence with structured evidence attribution
- E2 baseline: standardized comparison condition

## Experimental Execution

For each repeated run, items were submitted using standardized batch prompts.

A new model session was initiated for each repeated run.

Models were instructed to evaluate each item independently and to return structured outputs using the predefined response schema.

## Primary Analysis

The revised 20-run experiments constitute the primary dataset used for the statistical analyses reported in the revised manuscript.

Variability was quantified using Shannon entropy across three decision dimensions:

- Policy_Decision
- Operational_Interval
- Evidence_Priority

Verbalized confidence was also analyzed using the model-generated `Confidence` score on a 0–100 scale.

## Verbalized Confidence

The `Confidence` field represents a model-generated score and is treated as verbalized confidence.

It should not be interpreted as:

- a calibrated probability,
- a token-level uncertainty estimate,
- or a direct measure of epistemic uncertainty.

## Cross-Phase Comparison

Results from the revised 20-run experiments are compared descriptively with the initial 7-run experiments.

Because model versions, number of repeated runs, and execution protocols differed between phases, cross-phase differences should not be interpreted as causal estimates of improvement across model generations.
