---
layout: page
title: Research
permalink: /research/
---

## Publications

[The Missing Indicator Method: From Low to High Dimensions](https://arxiv.org/pdf/2211.09259.pdf)

**Venue**: KDD 2023 Applied Data Science Track

<details>
<summary><b>Abstract</b></summary>
Missing data is common in applied data science, particularly for
tabular data sets found in healthcare, social sciences, and natural
sciences. Most supervised learning methods only work on complete data, thus requiring preprocessing such as missing value imputation to work on incomplete data sets. However, imputation alone does not encode useful information about the missing values themselves. For data sets with informative missing patterns, the Missing Indicator Method (MIM), which adds indicator variables to indicate
the missing pattern, can be used in conjunction with imputation to
improve model performance. While commonly used in data science,
MIM is surprisingly understudied from an empirical and especially
theoretical perspective. In this paper, we show empirically and theoretically that MIM improves performance for informative missing
values, and we prove that MIM does not hurt linear models asymptotically for uninformative missing values. Additionally, we find
that for high-dimensional data sets with many uninformative indicators, MIM can induce model overfitting and thus test performance.
To address this issue, we introduce Selective MIM (SMIM), a novel
MIM extension that adds missing indicators only for features that
have informative missing patterns. We show empirically that SMIM
performs at least as well as MIM in general, and improves MIM for
high-dimensional data. Lastly, to demonstrate the utility of MIM
on real-world data science tasks, we demonstrate the effectiveness
of MIM and SMIM on clinical tasks generated from the MIMIC-III
database of electronic health records.
</details>

[CDF Normalization for Controlling the Distribution
of Hidden Nodes](https://proceedings.mlr.press/v163/ness22a/ness22a.pdf)

**Venue**: I (Still) Can't Believe It's Not Better! Workshop at NeurIPS 2021

<details>
<summary><b>Abstract</b></summary>
Batch Normalizaiton (BN) is a normalization method for deep neural networks
that has been shown to accelerate training. While the effectiveness of BN is
undisputed, the explanation of its effectiveness is still being studied. The original
BN paper attributes the success of BN to reducing internal covariate shift, so we
take this a step further and explicitly enforce a Gaussian distribution on hidden
layer activations. This approach proves to be ineffective, demonstrating further that
reducing internal covariate shift is not important for successful layer normalization.
</details>

## Preprints

Interpretable Survival Analysis for Heart Failure Risk Prediction (Coming soon!)

[Cross-Frequency Time Series Meta-Forecasting](https://arxiv.org/pdf/2302.02077.pdf)

<details>
<summary><b>Abstract</b></summary>
Meta-forecasting is a newly emerging field which combines meta-learning and
time series forecasting. The goal of meta-forecasting is to train over a collection
of source time series and generalize to new time series one-at-a-time. Previous
approaches in meta-forecasting achieve competitive performance, but with the
restriction of training a separate model for each sampling frequency. In this work,
we investigate meta-forecasting over different sampling frequencies, and introduce
a new model, the Continuous Frequency Adapter (CFA), specifically designed
to learn frequency-invariant representations. We find that CFA greatly improves
performance when generalizing to unseen frequencies, providing a first step towards
forecasting over larger multi-frequency datasets.
</details>

