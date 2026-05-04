---
title: "Three-Phase Seizure Segmentation in SEEG"
excerpt: "Semi-supervised changepoint detection for automated delineation of seizure onset, intra-ictal transition, and termination in stereoelectroencephalography recordings.<br/><img src='/images/projects/seizure_segmentation.png' style='max-width:400px;'>"
collection: portfolio
---

## Overview

Accurate segmentation of seizure phases in intracranial EEG is essential for characterizing seizure dynamics and supporting presurgical evaluation in drug-resistant focal epilepsy. This project develops a semi-supervised framework that automatically delineates three distinct seizure phases — **ictal onset**, **intra-ictal transition**, and **seizure termination** — directly from stereoelectroencephalography (SEEG) recordings.

## Motivation

In patients with drug-resistant focal epilepsy, surgical resection of the seizure onset zone (SOZ) remains the primary therapeutic option when medications fail. Surgical success depends critically on accurate SOZ localization, which requires comprehensive characterization of seizure dynamics. Clinical interpretation of intracranial EEG relies on expert visual inspection — a process that is time-intensive and subject to significant inter-rater variability (Cohen's κ = 0.35–0.69).

Understanding how seizures progress through **initiation → propagation → termination** is essential for distinguishing the true SOZ from areas of secondary spread.

## Methodology

Seven envelope-based features are extracted from optimized sliding windows: RMS envelope, relative bandpower in θ/α/β/γ bands, line length, and spectral entropy. The **Pruned Exact Linear Time (PELT)** algorithm with an RBF kernel detects temporal changepoints. Three phase-specific models are trained with independently optimized feature weights and PELT penalty parameters, validated via nested leave-one-subject-out cross-validation with Optuna hyperparameter optimization.

## Results

Evaluated on 179 SOZ bipolar channels across 32 seizures from 10 Engel Class I patients:

| Phase | MAE (s) | Accuracy (±5 s) |
|---|---|---|
| Seizure Onset | 4.19 ± 2.69 | 71.6% |
| Intra-ictal Transition | 6.93 ± 5.75 | 60.0% |
| Seizure Termination | 3.82 ± 4.24 | 75.0% |

Performance was stable across seizure durations (60–240 s), confirming length-invariant behavior.

## Publication

*Three-Phase Seizure Segmentation in Stereotactic EEG Using Envelope-Based Multivariate Changepoint Analysis.* **Annals of Biomedical Engineering**, April 2026. [DOI: 10.1007/s10439-026-04097-7](https://doi.org/10.1007/s10439-026-04097-7)
