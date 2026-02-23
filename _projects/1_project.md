---
layout: page
title: Three-Phase Seizure Segmentation in SEEG
description: Semi-supervised changepoint detection for automated delineation of seizure onset, intra-ictal transition, and termination in stereoelectroencephalography recordings.
img: assets/img/projects/seizure_segmentation.png
importance: 1
category: Cleveland Clinic
related_publications: true
---

## Overview

Accurate segmentation of seizure phases in intracranial EEG is essential for characterizing seizure dynamics and supporting presurgical evaluation in drug-resistant focal epilepsy. This project develops a semi-supervised framework that automatically delineates three distinct seizure phases—**ictal onset**, **intra-ictal transition**, and **seizure termination**—directly from stereoelectroencephalography (SEEG) recordings.

---

## Motivation

In patients with drug-resistant focal epilepsy, surgical resection of the seizure onset zone (SOZ) remains the primary therapeutic option when medications fail. Surgical success depends critically on accurate SOZ localization, which requires comprehensive characterization of seizure dynamics. Clinical interpretation of intracranial EEG has traditionally relied on expert visual inspection—a process that is time-intensive and subject to significant inter-rater variability (Cohen's κ = 0.35–0.69).

Understanding how seizures progress through **initiation → propagation → termination** is essential for distinguishing the true SOZ from areas of secondary spread. Precise timing of these phases enables mapping of spatiotemporal seizure propagation and ultimately supports improved surgical planning.

---

## Methodology

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/seizure_segmentation_pipeline.jpg" title="Three-phase segmentation pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Schematic of the proposed three-phase seizure segmentation framework combining multivariate envelope features with PELT changepoint detection.
</div>

### Signal Representation

Seven complementary envelope-based features are extracted from optimized sliding windows:

- **RMS envelope** — captures overall signal energy dynamics
- **Relative bandpower** in θ (4–8 Hz), α (8–13 Hz), β (13–30 Hz), and γ (30–80 Hz) bands
- **Line length** — proxy for signal complexity and high-frequency activity
- **Spectral entropy** — quantifies irregularity of the power spectrum

### Changepoint Detection

The **Pruned Exact Linear Time (PELT)** algorithm with a radial basis function kernel provides exact global optimization of temporal changepoint locations. Three phase-specific models are trained (Onset, Transition, Termination), each with independently optimized feature weights and PELT penalty parameters.

### Optimization & Validation

Nested **leave-one-subject-out cross-validation** with Optuna hyperparameter optimization ensures unbiased patient-level performance estimates. A key design choice is **random temporal padding** (5–30 s of real pre/post-ictal data) to enforce length invariance and prevent the algorithm from exploiting fixed seizure positions.

---

## Results

Performance was evaluated on **179 SOZ bipolar channels** across **32 seizures** from **10 patients**, all of whom achieved seizure freedom (Engel Class I) following resective surgery.

| Phase | MAE (s) | Accuracy (±5s) |
|---|---|---|
| Seizure Onset | 4.19 ± 2.69 | 71.6% |
| Intra-ictal Transition | 6.93 ± 5.75 | 60.0% |
| Seizure Termination | 3.82 ± 4.24 | 75.0% |

Temporal precision for onset and termination is comparable to published inter-rater reliability among clinicians. Performance was **stable across seizure durations** (60–240 s), confirming length-invariant behavior.

**Phase-specific feature importance** analysis revealed distinct contributions across seizure phases: β/α/γ power dominates onset detection; RMS amplitude and β power drive termination; RMS and line length are most informative for transition detection.

---

## Clinical Significance

By coupling physiologically meaningful features with exact changepoint detection, this framework yields **interpretable and auditable temporal boundaries** without the opacity of deep learning approaches. Beyond onset localization, changepoint-based segmentation enables objective mapping of seizure propagation on a per-channel basis—directly supporting surgical planning for drug-resistant epilepsy.

---

## Related Publications

{% cite kumar2025changepoint %}