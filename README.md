# Data for: Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems

This repository contains evidence prompts, model-generated outputs, and supporting materials associated with the manuscript:

**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study**

The repository is intended to support transparency and reproducibility of the experimental framework used to examine decision stability under conflicting and non-conflicting evidence conditions.

## Contents

- `data/evidence_packs/`  
  Experimental prompt materials used as model inputs. The currently released materials include a structured conflicting-evidence scenario concerning repositioning frequency for pressure injury prevention in hospitalized adults.

- `data/outputs_sample.json`  
  Representative model-generated outputs across repeated runs, including policy-level decisions, operational recommendations, evidence-priority judgments, and confidence scores.

Additional repeated-run outputs, prompt templates, intervention materials, and analysis files may be added as part of the revised study materials.

## Experimental Framework

The study evaluates model behavior under two primary evidence conditions:

1. **Conflict condition (E1)**  
   Structured evidence prompts containing conflicting or partially incompatible recommendations.

2. **Non-conflict condition (E2)**  
   Standardized single-answer items without evidentiary contradiction, used as a baseline condition.

Model outputs are analyzed using a three-level decision structure:

- **Policy_Decision (Level 1):** high-level decision framing
- **Operational_Interval (Level 2):** actionable implementation recommendation
- **Evidence_Priority (Level 3):** explicit or implicit prioritization of evidence

Repeated model runs are used to characterize variability in categorical outputs and to estimate Shannon entropy at each decision level.

## E1 Conflict Scenario

The currently released E1 material focuses on repositioning frequency for pressure injury prevention in hospitalized adults.

The evidence set contains three sources with partially conflicting operational implications:

- an international clinical guideline favoring individualized repositioning based on patient risk, tissue tolerance, and clinical condition;
- a randomized clinical trial reporting that a 4-hour repositioning interval, under specified support-surface conditions, did not increase pressure injury incidence relative to a 2-hour regimen; and
- an observational/quality-improvement study reporting a substantial reduction in pressure injury incidence following implementation of a fixed 2-hour repositioning schedule.

The same evidence content and output categories are used across repeated runs within the corresponding experimental condition.

## Output Structure

Model responses are requested in structured JSON format using the following fields:

- `Policy_Decision`
- `Operational_Interval`
- `Evidence_Priority`
- `Confidence`

A representative output record contains metadata such as:

- `pack_id`
- `task`
- `model`
- `condition`
- `output_type`
- `run_id`

together with the four structured decision variables listed above.

## Evidence-Attribution Intervention

An additional evidence-attribution condition is evaluated under E1.

In this condition, models are instructed to explicitly evaluate and prioritize the supplied evidence before selecting the operational recommendation. The underlying clinical question, evidence set, response categories, and structured output format remain unchanged relative to the E1 baseline condition.

The intervention is designed to test whether additional structure in evidence interpretation reduces variability at the operational decision level.

Baseline and intervention prompt materials are provided separately so that the difference between experimental conditions can be inspected directly.

## Measures

The dataset supports analysis of:

1. Cross-model differences
2. Intra-model variability across repeated runs
3. Policy–operational dissociation
4. Decision-level entropy
5. Verbalized confidence
6. Changes in operational variability following structured evidence attribution

### Decision-Level Entropy

Variability in categorical model outputs is quantified using Shannon entropy.

Entropy is calculated separately for each decision level based on the empirical distribution of categorical outputs across repeated runs.

Higher entropy indicates greater dispersion of outputs within the corresponding coding structure, whereas lower entropy indicates greater stability.

Because the number of admissible categories may differ across decision levels, absolute entropy values should be interpreted within the predefined coding structure of each level. Cross-level comparisons are used to characterize where variability is concentrated within the decision hierarchy rather than to assume identical theoretical entropy ceilings across levels.

### Verbalized Confidence

The `Confidence` field represents a model-generated confidence score on a 0–100 scale.

In this study, this measure is referred to as **verbalized confidence**.

Verbalized confidence is a generated output variable and should not be interpreted as:

- a calibrated probability of correctness,
- a direct estimate of epistemic uncertainty,
- a token-probability-based uncertainty measure, or
- a direct observation of the model's internal confidence state.

Differences in verbalized confidence across experimental conditions are therefore interpreted as changes in expressed confidence at the output level.

Any standardized effect sizes calculated from these values describe differences in generated confidence scores between conditions and should not be interpreted as calibrated changes in epistemic uncertainty.

## Reproducibility Notes

- All outputs were generated using publicly accessible large language models.
- Experimental conditions were designed to hold prompt structure and evidence content constant within each direct comparison.
- Repeated runs are used to estimate output variability under otherwise matched conditions.
- Model version, prompting condition, run identifier, and coded decision outputs should be retained in the released data whenever available.
- Baseline and evidence-attribution intervention conditions use the same underlying evidence materials.
- The structured output schema is held constant across directly compared conditions.
- The repository documents model-output behavior and does not contain patient-level data or identifiable personal information.

## Interpretation of the Intervention

The evidence-attribution intervention is intended to test whether explicitly structuring evidence prioritization changes the distribution of model-generated operational recommendations.

A reduction in operational-level entropy is interpreted as reduced output variability under the intervention condition.

Such a reduction should not be interpreted as evidence that:

- the model has become clinically more accurate,
- the model has acquired calibrated uncertainty,
- the intervention improves real-world patient safety, or
- human users will necessarily rely on the model more appropriately.

These questions require separate clinical, calibration, or human-subject evaluation.

## Scope and Limitations

This dataset is intended to support analysis of decision stability in generative AI-assisted decision systems.

It should not be interpreted as:

- a benchmark of overall model quality,
- a direct measure of calibrated epistemic uncertainty,
- evidence of human automation bias or user behavior,
- a clinical effectiveness evaluation,
- a clinical safety evaluation, or
- evidence that one operational recommendation is clinically superior to another.

The study evaluates patterns in model-generated outputs.

Human responses to model instability, including trust, reliance, automation bias, and behavioral decision-making, were not directly evaluated.

## Data Availability

The repository currently provides representative prompt materials and sample model outputs.

Additional repeated-run datasets and analysis materials may be released as the revised study materials are finalized.

The repository is intended to make the experimental structure, output coding, and representative model behavior transparent and inspectable.

## Citation

If you use this dataset or experimental framework, please cite the associated manuscript:

Zhou F, Sheng J, Yang H, He Y, Tang C.  
**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study.**  
Under review.

## Contact

For questions regarding the dataset, experimental materials, or additional study information, please contact the corresponding authors.
