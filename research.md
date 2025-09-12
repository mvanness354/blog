---
layout: page
title: Research
permalink: /research/
---

Link to <a href="https://scholar.google.com/citations?user=rgwrYqIAAAAJ&hl=en&oi=ao">Google Scholar</a>

During my PhD, I mainly focused on builting interpretable machine learning models for a variety of problems 
in healthcare. Towards the beginning of my PhD, I focused more on problems related to missing data,
which is common in my domains including healthcare. 
Later in my PhD, I switched to developing techniques to train additive models for survival analysis.
These models have the benefit of increased accuracy compared to linear models, but with
more structural interpretability than black-box neural networks.
In the last year of my PhD, I spent a lot of time developing <a href="https://dnamite.readthedocs.io/en/latest/">dnamite</a>,
a Python package for training Neural Additive Models for regression, classification, and survival analysis.
For a good overview of my PhD research, see my <a href="https://drive.google.com/file/d/1grB2yGueojADOtXQgo2EHfyV9enu57Qx/view?usp=sharing">PhD defense slides</a>.

## Publications

[Interpretable Prediction and Feature Selection for Survival Analysis](https://arxiv.org/pdf/2404.14689)

**Venue**: KDD 2025

<details>
<summary><b>Abstract</b></summary>

Survival analysis is widely used as a technique to
model time-to-event data when some data is censored,
particularly in healthcare for predicting future patient
risk. In such settings, survival models must be both accurate and interpretable so that users (such as doctors)
can trust the model and understand model predictions.
While most literature focuses on discrimination, interpretability is equally as important. A successful interpretable model should be able to describe how changing each feature impacts the outcome, and should only use a
small number of features. In this paper, we present DyS
(pronounced “dice”), a new survival analysis model that
achieves both strong discrimination and interpretability.
DyS is a feature-sparse Generalized Additive Model,
combining feature selection and interpretable prediction
into one model. While DyS works well for all survival
analysis problems, it is particularly useful for large (in n
and p) survival datasets such as those commonly found
in observational healthcare studies. Empirical studies
show that DyS competes with other state-of-the-art
machine learning models for survival analysis, while
being highly interpretable.

</details>

-----------------------------------------------------------------------------------

[DNAMite: Interpretable Calibrated Survival Analysis with Discretized Additive Models](https://arxiv.org/pdf/2411.05923?)

**Venue**: ML4H 2024

<details>
<summary><b>Abstract</b></summary>

Survival analysis is a classic problem in statistics
with important applications in healthcare. Most
machine learning models for survival analysis are
black-box models, limiting their use in healthcare settings where interpretability is paramount.
More recently, glass-box machine learning models have been introduced for survival analysis,
with both strong predictive performance and
interpretability. Still, several gaps remain, as
no prior glass-box survival model can produce
calibrated shape functions with enough flexibility to capture the complex patterns often found
in real data. To fill this gap, we introduce a
new glass-box machine learning model for survival analysis called DNAMite. DNAMite uses
feature discretization and kernel smoothing in
its embedding module, making it possible to
learn shape functions with a flexible balance of
smoothness and jaggedness. Further, DNAMite
produces calibrated shape functions that can
be directly interpreted as contributions to the
cumulative incidence function. Our experiments
show that DNAMite generates shape functions
closer to true shape functions on synthetic data,
while making predictions with comparable predictive performance and better calibration than
previous glass-box and black-box models.

</details>

-----------------------------------------------------------------------------------


[Interpretable Survival Analysis for Heart Failure Risk Prediction](https://arxiv.org/pdf/2310.15472)

**Venue**: ML4H 2023

<details>
<summary><b>Abstract</b></summary>

Survival analysis, or time-to-event analysis, is an important and widespread problem in healthcare research. Medical research has traditionally relied on Cox models for survival analysis, due to their simplicity and interpretability. Cox models assume a log-linear hazard function as well as proportional hazards over time, and can perform poorly when these assumptions fail. Newer survival models based on machine learning avoid these assumptions and offer improved accuracy, yet sometimes at the expense of model interpretability, which is vital for clinical use. We propose a novel survival analysis pipeline that is both interpretable and competitive with state-of-the-art survival models. Specifically, we use an improved version of survival stacking to transform a survival analysis problem to a classification problem, ControlBurn to perform feature selection, and Explainable Boosting Machines to generate interpretable predictions. To evaluate our pipeline, we predict risk of heart failure using a large-scale EHR database. Our pipeline achieves state-of-the-art performance and provides interesting and novel insights about risk factors for heart failure.

</details>

-----------------------------------------------------------------------------------

[In Defense of Zero Imputation for Tabular Deep Learning](https://openreview.net/pdf?id=H0gENXL7F2)

**Venue**: Table Representation Learning Workshop, NeurIPS 2024

<details>
<summary><b>Abstract</b></summary>

Missing values are a common problem in many supervised learning contexts. While a wealth of literature exists related to missing value imputation, less literature has focused on the impact of imputation on downstream supervised learning. Recently, impute-then-predict neural networks have been proposed as a powerful solution to this problem, allowing for joint optimization of imputations and predictions. In this paper, we illustrate a somewhat surprising result: multi-layer perceptrons (MLPs) paired with zero imputation perform as well as more powerful deep impute-then-predict models on real-world data. To support this finding, we analyze the results of various deep impute-then-predict models to better understand why they fail to outperform zero imputation. Our analysis sheds light onto the difficulties of imputation in real-world contexts, and highlights the utility of zero imputation for tabular deep learning.

</details>

-----------------------------------------------------------------------------------

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

-----------------------------------------------------------------------------------

[CDF Normalization for Controlling the Distribution of Hidden Nodes](https://proceedings.mlr.press/v163/ness22a/ness22a.pdf)

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

-----------------------------------------------------------------------------------

## Preprints

[dnamite: A Python Package for Neural Additive Models](https://arxiv.org/pdf/2503.07642)

<details>
<summary><b>Abstract</b></summary>
Additive models offer accurate and interpretable predictions for tabular data, a critical
tool for statistical modeling. Recent advances in Neural Additive Models (NAMs) allow
these models to handle complex machine learning tasks, including feature selection and
survival analysis, on large-scale data. This paper introduces dnamite, a Python package
that implements NAMs for these advanced applications. dnamite provides a scikit-learn
style interface to train regression, classification, and survival analysis NAMs, with built-
in support for feature selection. We describe the methodology underlying dnamite, its
design principles, and its implementation. Through an application to the MIMIC III clin-
ical dataset, we demonstrate the utility of dnamite in a real-world setting where feature
selection and survival analysis are both important. The package is publicly available via
pip and documented at dnamite.readthedocs.io.
</details>

-----------------------------------------------------------------------------------

[Interpretable Prediction and Feature Selection for Survival Analysis](https://arxiv.org/pdf/2404.14689)

<details>
<summary><b>Abstract</b></summary>
Survival analysis is widely used as a technique to model time-to-event data when some data is censored, particularly in healthcare for predicting future patient risk. In such settings, survival models must be both accurate and interpretable so that users (such as doctors) can trust the model and understand model predictions. While most literature focuses on discrimination, interpretability is equally as important. A successful interpretable model should be able to describe how changing each feature impacts the outcome, and should only use a small number of features. In this paper, we present DyS (pronounced “dice”), a new survival analysis model that achieves both strong discrimination and interpretability. DyS is a feature-sparse Generalized Additive Model, combining feature selection and interpretable prediction into one model. While DyS works well for all survival analysis problems, it is particularly useful for large (in n and p) survival datasets such as those commonly found in observational healthcare studies. Empirical studies show that DyS competes with other state-of-the-art machine learning models for survival analysis, while being highly interpretable.
</details>

-----------------------------------------------------------------------------------

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

