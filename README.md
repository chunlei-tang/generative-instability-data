# Data for: Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems

This repository contains evidence prompts, model-generated outputs, and supporting materials associated with the manuscript:

**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study**

The repository is intended to support transparency and reproducibility of the experimental framework used to examine decision stability under conflicting and standardized evidence conditions.

---

## Contents

- `data/evidence_packs/`  
  Shared experimental prompt materials and structured evidence packs used across the study.

- `data/initial_7run/`  
  Materials and representative outputs from the initial experimental phase using ChatGPT 5.1 Thinking and Gemini 3 Pro with 7 repeated runs per item.

- `data/revised_20run/`  
  Materials and representative outputs from the revised experimental phase using GPT-6 Astra Medium and Gemini 3.1 Pro with 20 repeated runs per item.

  The revised phase includes:
  - E1 baseline
  - E1 evidence-attribution intervention
  - E2 standardized comparison condition

Complete repeated-run datasets used for the primary revised analyses are provided as supplementary study materials.

---

## Experimental Phases

The study includes two experimental phases.

### Initial Experiments

The initial experiments evaluated:

- ChatGPT 5.1 Thinking
- Gemini 3 Pro

Each item was evaluated across 7 repeated runs.

The initial phase included:

- **E1:** conflicting-evidence condition
- **E2:** standardized comparison condition

These experiments provided the initial characterization of decision variability under conflicting and standardized evidence conditions.

### Revised Experiments

During revision, the experiments were repeated using newer model versions:

- GPT-6 Astra Medium
- Gemini 3.1 Pro

Each item was evaluated across 20 repeated runs.

The revised phase included:

- **E1 baseline:** conflicting-evidence condition
- **E1 intervention:** conflicting evidence with structured evidence attribution
- **E2 baseline:** standardized comparison condition

The primary statistical analyses reported in the revised manuscript are based on the revised 20-run experiments.

Results from the initial 7-run experiments are retained for descriptive comparison across experimental phases and model versions.

Because the two phases differed in model versions, number of repeated runs, and execution protocol, cross-phase comparisons should be interpreted descriptively rather than as causal estimates of model improvement.

---

## Experimental Framework

The study evaluates model behavior under two primary evidence conditions.

### Conflict Condition (E1)

E1 uses structured evidence prompts containing conflicting or partially incompatible recommendations.

The purpose of E1 is to examine how generative models organize and reproduce decisions when multiple evidence sources support different plausible recommendations.

### Standardized Condition (E2)

E2 uses standardized items without structured evidentiary contradiction and serves as a comparison condition.

The E2 condition provides a reference for examining decision stability when the structured conflict present in E1 is absent.

---

## Decision Structure

Model outputs are represented using three decision dimensions:

- **Policy_Decision (Level 1):** high-level decision framing
- **Operational_Interval (Level 2):** actionable implementation recommendation
- **Evidence_Priority (Level 3):** evidence category emphasized in the generated decision

Repeated model runs are used to characterize variability within each decision dimension.

The framework does not assume that variability will be concentrated at any specific level.

Instead, stability is evaluated separately across decision levels and models.

---

## E1 Conflict Scenario

The released E1 materials include structured evidence concerning repositioning frequency for pressure injury prevention in hospitalized adults.

The evidence packs contain sources with partially conflicting operational implications, including:

- clinical guidelines supporting individualized or risk-based repositioning;
- randomized trials evaluating alternative repositioning intervals;
- observational or quality-improvement evidence supporting fixed schedules;
- additional evidence reflecting heterogeneity in patient populations, clinical settings, and intervention strategies.

The evidence content and structured response categories are held constant within directly compared experimental conditions.

---

## Output Structure

Model responses are requested in structured JSON format.

The primary decision variables are:

- `Policy_Decision`
- `Operational_Interval`
- `Evidence_Priority`
- `Confidence`

Depending on the experimental phase and released file, records may also contain metadata such as:

- `Pack_ID` or `Question_ID`
- `pack_id`
- `task`
- `model`
- `condition`
- `output_type`
- `run_id`

These metadata are used to identify the model, experimental condition, item, and repeated run associated with each output.

---

## Revised 20-Run Execution

For the revised experimental phase, each repeated run was conducted in a new model session.

Items were submitted using standardized batch prompts.

Models were instructed to evaluate each item independently and not to use information, reasoning, or conclusions from one item when answering another item within the same batch.

The structured output schema was held constant across directly compared conditions.

The revised experiments used:

- 20 repeated runs per E1 evidence pack
- 20 repeated runs per E2 item
- 20 repeated runs per E1 intervention evidence pack

---

## Evidence-Attribution Intervention

An additional evidence-attribution condition was evaluated under E1 during the revised experimental phase.

In this condition, models were instructed to explicitly evaluate and prioritize the supplied evidence before selecting the final policy and operational recommendation.

The intervention required the model to consider:

1. evidence type and strength;
2. clinical context and patient characteristics;
3. which evidence category most directly supported the operational recommendation;
4. whether a single evidence category dominated or whether the evidence should be classified as mixed.

The underlying clinical question, evidence packs, response categories, and structured output format remained matched to the E1 baseline condition.

The intervention was designed to test whether explicit evidence structuring changes the stability and distribution of generated decisions.

---

## Measures

The dataset supports analysis of:

1. Cross-model differences
2. Intra-model variability across repeated runs
3. Decision-level stability profiles
4. Decision-level entropy
5. Verbalized confidence
6. Changes in variability following structured evidence attribution
7. Descriptive comparison across experimental phases and model versions

---

## Decision-Level Entropy

Variability in categorical model outputs is quantified using Shannon entropy.

Entropy is calculated separately for each decision level based on the empirical distribution of categorical outputs across repeated runs.

Higher entropy indicates greater dispersion of outputs within the corresponding coding structure, whereas lower entropy indicates greater stability.

Because the number and type of admissible categories differ across decision levels, absolute entropy values should be interpreted within the predefined coding structure of each level.

Cross-level comparisons are therefore used to characterize the distribution of variability across decision dimensions rather than to assume identical theoretical entropy ceilings.

For the revised analyses, entropy was calculated within each item across repeated runs and then summarized across items.

---

## Verbalized Confidence

The `Confidence` field represents a model-generated confidence score on a 0–100 scale.

In this study, this measure is referred to as **verbalized confidence**.

Verbalized confidence is a generated output variable and should not be interpreted as:

- a calibrated probability of correctness,
- a direct estimate of epistemic uncertainty,
- a token-probability-based uncertainty measure, or
- a direct observation of the model's internal confidence state.

Differences in verbalized confidence across experimental conditions are therefore interpreted as changes in expressed confidence at the output level.

Standardized effect sizes calculated from these values describe differences in generated confidence scores between conditions and should not be interpreted as calibrated changes in epistemic uncertainty.

---

## Interpretation of the Intervention

The evidence-attribution intervention is intended to test whether explicitly structuring evidence prioritization changes the distribution and stability of model-generated decisions.

Intervention effects are evaluated separately across:

- `Policy_Decision`
- `Operational_Interval`
- `Evidence_Priority`

Changes in entropy are interpreted as changes in output variability within the corresponding decision dimension.

The intervention should not be assumed to affect all decision levels or models in the same direction.

Changes observed under the intervention should not be interpreted as evidence that:

- the model has become clinically more accurate,
- the model has acquired calibrated uncertainty,
- the intervention improves real-world patient safety, or
- human users will necessarily rely on the model more appropriately.

These questions require separate clinical, calibration, or human-subject evaluation.

---

## Cross-Phase Comparison

The initial 7-run experiments and revised 20-run experiments provide a descriptive comparison of decision stability across different model versions and experimental phases.

The initial phase used:

- ChatGPT 5.1 Thinking
- Gemini 3 Pro
- 7 repeated runs per item

The revised phase used:

- GPT-6 Astra Medium
- Gemini 3.1 Pro
- 20 repeated runs per item

Absolute variability differed between the two experimental phases in several decision dimensions.

However, the phases also differed in:

- model versions,
- number of repeated runs,
- and execution protocol.

Cross-phase differences should therefore be interpreted descriptively.

They should not be interpreted as causal estimates of model improvement or as evidence that differences are attributable solely to model generation.

---

## Reproducibility Notes

- Experimental prompts and response schemas are documented to support transparency of the study design.
- Experimental conditions hold prompt structure and evidence content constant within each direct comparison.
- Repeated runs are used to estimate output variability under otherwise matched conditions.
- Model version, prompting condition, run identifier, and coded decision outputs are retained where available.
- Baseline and evidence-attribution intervention conditions use the same underlying E1 evidence materials.
- The structured output schema is held constant across directly compared conditions.
- A new model session was initiated for each repeated run in the revised experiments.
- Revised experiments were conducted using standardized batch prompts.
- Items within each batch were explicitly instructed to be evaluated independently.
- The repository documents model-output behavior and does not contain patient-level data or identifiable personal information.

Because generative AI systems may change over time, exact replication with later model versions may not reproduce historical outputs identically.

The repository is therefore intended to support transparency of the experimental conditions, prompts, output structure, and observed model behavior at the time of evaluation.

---

## Scope and Limitations

This dataset is intended to support analysis of decision stability in generative AI-assisted decision systems.

It should not be interpreted as:

- a benchmark of overall model quality,
- a direct measure of calibrated epistemic uncertainty,
- evidence of human automation bias or user behavior,
- a clinical effectiveness evaluation,
- a clinical safety evaluation, or
- evidence that one operational recommendation is clinically superior to another.

The study evaluates patterns in model-generated outputs under controlled evidence conditions.

Human responses to model instability, including trust, reliance, automation bias, and behavioral decision-making, were not directly evaluated.

The study evaluates a limited set of model versions, and stability characteristics may differ across future models, architectures, system configurations, or prompting environments.

---

## Data Availability

This repository provides structured prompt materials and representative model outputs from both experimental phases.

Materials from the initial 7-run experiments are retained for descriptive comparison with the revised experiments.

Materials from the revised 20-run experiments include:

- E1 baseline prompts and representative outputs
- E1 evidence-attribution intervention prompts and representative outputs
- E2 standardized prompts and representative outputs

Complete repeated-run datasets used for the primary revised analyses are provided as supplementary study materials.

The repository is intended to make the experimental structure, prompt design, output coding, and representative model behavior transparent and inspectable.

Additional materials may be obtained from the corresponding authors upon reasonable request.

---

## Citation

If you use this dataset or experimental framework, please cite the associated manuscript:

Zhou F, Sheng J, Yang H, He Y, Tang C.  
**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study.**  
Under review.

---

## Contact

For questions regarding the dataset, experimental materials, or additional study information, please contact the corresponding authors.
