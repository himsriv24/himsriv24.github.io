---
layout: page
title: Deep Contrastive Learning for Seizure Onset Zone Localization
description: A self-supervised CNN-Transformer framework for automated ictal onset zone classification from SEEG spectrograms, with multi-center validation.
img: assets/img/projects/deep_learning_soz.png
importance: 4
category: Cleveland Clinic
---

## Overview

Accurate seizure onset zone (SOZ) localization is central to successful epilepsy surgery, yet current methods rely on time-intensive expert visual analysis of intracranial EEG. No validated automated tool currently exists for this task.

This project develops a **self-supervised deep learning framework** that learns representations of ictal onset patterns from SEEG spectrograms without requiring labeled data during training. A hybrid CNN-Transformer encoder is pretrained using contrastive learning on time-frequency representations derived from the superlet transform, capturing both local spectral features and long-range temporal dependencies. Downstream classification is evaluated under leave-one-subject-out cross-validation and validated on an independent external cohort.

Beyond classification performance, the project explores what the model learns about ictal onset phenotypes and examines whether learned representations can offer insight into cases with poor surgical outcomes.

*Manuscript in preparation.*