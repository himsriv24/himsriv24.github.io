---
title: 'Why Three-Phase Seizure Segmentation Matters in SEEG'
date: 2026-03-24
permalink: /posts/2026/03/three-phase-seizure-segmentation/
tags:
  - epilepsy
  - SEEG
  - signal-processing
---

The central clinical question in drug-resistant focal epilepsy is not only *where* a seizure begins, but also *how* it evolves over time. In stereotactic EEG (SEEG), the transition from seizure onset to propagation and then to termination carries information that can help separate the true seizure onset zone from regions that are recruited later.

In our recent work, I focused on **three-phase seizure segmentation**: identifying ictal onset, intra-ictal transition, and seizure termination directly from SEEG recordings. Rather than treating seizures as a single undifferentiated event, this framing emphasizes their temporal structure and makes the analysis more useful for presurgical interpretation.

## Why segmentation matters

Clinical review of intracranial EEG is still heavily dependent on expert visual inspection. That process is valuable, but it is also time-intensive and can vary across readers. A phase-based computational framework can support that review by providing consistent temporal boundaries that are interpretable and easy to audit.

Precise phase segmentation also helps with downstream analysis. Once onset, transition, and termination are localized in time, it becomes easier to study propagation dynamics across channels, compare seizure organization across patients, and relate electrophysiology to surgical hypotheses.

## Why we used changepoint detection

A seizure is a dynamic signal, so changepoint detection is a natural fit. In this project, I used envelope-based multivariate features together with the **Pruned Exact Linear Time (PELT)** algorithm to detect boundaries between seizure phases. The goal was not only good performance, but also a method that remains physiologically interpretable.

The feature set combines signal energy and spectral structure, including RMS envelope, relative bandpower, line length, and spectral entropy. That combination gives the model access to amplitude shifts, rhythmic structure, and changes in signal complexity without turning the pipeline into a black box.

## What I find promising about this direction

What I find most promising is that the framework supports both **temporal precision** and **clinical interpretability**. If an algorithm proposes a boundary, it should be possible to inspect the relevant channels, understand the feature behavior, and decide whether the output is clinically meaningful.

That balance matters in epilepsy research. Methods that are accurate but opaque are harder to trust in high-stakes settings. Methods that are interpretable but too weak to be useful do not help enough. I am interested in approaches that move both of those constraints in the right direction.

## Looking ahead

This line of work connects naturally to broader questions about seizure propagation, seizure onset zone localization, and representation learning from intracranial EEG. The published paper is one step in that direction, and I expect future work to build on it with richer multichannel modeling and tighter integration with clinical decision support.

If you are interested in the paper itself, it is now online via [Springer](https://doi.org/10.1007/s10439-026-04097-7) and is also listed on my [publications page](/publications/).
