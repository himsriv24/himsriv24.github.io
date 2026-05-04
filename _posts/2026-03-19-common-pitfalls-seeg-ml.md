---
title: 'Common Pitfalls in SEEG Machine Learning'
date: 2026-03-19
permalink: /posts/2026/03/common-pitfalls-seeg-ml/
tags:
  - EEG
  - SEEG
  - machine-learning
  - deep-learning
---

Machine learning in EEG and SEEG can look deceptively straightforward: preprocess the signals, extract features or train a network, and report accuracy. In practice, many pipelines fail because the modeling choices are cleaner than the data assumptions underneath them.

Here are a few pitfalls I think are especially important.

## 1. Leakage across patients or seizures

The most common failure mode is still data leakage. If windows from the same seizure or patient appear in both training and test sets, performance can become artificially optimistic very quickly.

In epilepsy applications, patient-level separation is usually the right default. A model that performs well only because it has already seen a very similar seizure from the same person is not telling us much about generalization.

## 2. Treating labels as more precise than they really are

Many neuroscience labels are approximate, noisy, or based on human interpretation. Seizure onset time, propagation boundaries, emotional state labels, and cognitive annotations often carry uncertainty that standard pipelines ignore.

That does not mean the labels are unusable. It means the model evaluation should reflect their limitations. If the ground truth is inherently uncertain by a few seconds, then a metric that pretends otherwise can be misleading.

## 3. Ignoring temporal structure

EEG and SEEG are not just collections of independent samples. The order of events matters. Transitions matter. Context matters.

Pipelines that flatten everything into disconnected windows can miss the very structure that makes the problem interesting. Even when window-based analysis is necessary, it helps to think carefully about what temporal information is being discarded.

## 4. Optimizing for performance without interpretability

High accuracy is attractive, but in biomedical settings it is rarely enough on its own. Clinicians and collaborators usually want to know *why* a system made a prediction, which channels were informative, and whether the output aligns with known physiology.

This is one reason I often prefer methods that preserve some connection between features, signal dynamics, and decision boundaries. A model that is slightly less accurate but substantially easier to interpret can be more valuable in practice.

## 5. Underestimating preprocessing choices

Referencing scheme, filtering, artifact handling, channel selection, and segmentation strategy can change results substantially. These steps are sometimes treated as routine housekeeping, but they are often part of the scientific question itself.

A pipeline is only as defensible as its preprocessing assumptions. If those assumptions are weak or poorly documented, the downstream machine-learning results are harder to trust.

## Final thought

The hardest part of EEG and SEEG machine learning is usually not the model architecture. It is making sure the data split, label definition, temporal framing, and evaluation criteria actually match the problem you claim to solve.

That is where most of the real rigor lives.
