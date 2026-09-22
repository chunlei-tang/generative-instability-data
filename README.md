# Data for: Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems

This repository contains evidence prompts, model-generated outputs, and supporting materials associated with the manuscript:

**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study**

The repository is intended to support transparency and reproducibility of the experimental framework used to examine decision stability under conflicting and non-conflicting evidence conditions.

## Contents

- `data/evidence_packs/`  
  Representative evidence bundles used as model inputs, including clinical guidelines, randomized controlled trials, observational studies, and other evidence sources selected to preserve directional tension across recommendations.

- `data/outputs_sample.json`  
  Representative model-generated outputs across repeated runs, including policy-level decisions, operational recommendations, evidence-priority judgments, and verbalized confidence.

Additional prompt templates, repeated-run outputs, and analysis materials will be added as part of the revised study materials.

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

## Evidence-Attribution Intervention

An additional evidence-attribution condition is evaluated under E1. In this condition, models are instructed to explicitly prioritize and attribute the available evidence before producing an operational recommendation.

This intervention is designed to test whether additional structure in evidence interpretation reduces variability at the operational decision level.

The intervention uses the same underlying evidence materials as the corresponding E1 baseline condition.

## Measures

The dataset supports analysis of:

1. Cross-model differences
2. Intra-model variability across repeated runs
3. Policy–operational dissociation
4. Decision-level entropy
5. Verbalized confidence
6. Changes in operational variability following structured evidence attribution

Verbalized confidence should be interpreted as a model-generated output measure rather than as a calibrated estimate of epistemic uncertainty.

## Reproducibility Notes

- All outputs were generated using publicly accessible large language models.
- Experimental conditions were designed to hold prompt structure and evidence content constant within each comparison.
- Repeated runs are used to estimate output variability under otherwise matched conditions.
- Model version, prompting condition, run identifier, and coded decision outputs should be retained in the released data whenever available.
- The repository documents model-output behavior and does not contain patient-level data or identifiable personal information.

## Scope and Limitations

This dataset is intended to support analysis of decision stability in generative AI-assisted decision systems.

It should not be interpreted as:

- a benchmark of overall model quality,
- a direct measure of calibrated epistemic uncertainty,
- evidence of human automation bias or user behavior, or
- a clinical effectiveness or safety evaluation.

Human responses to model instability were not evaluated in this study.

## Citation

If you use this dataset, please cite the associated manuscript:

Zhou F, Sheng J, Yang H, He Y, Tang C.  
**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study.**  
Under review.

## Contact

For questions regarding the dataset or additional study materials, please contact the corresponding authors.
