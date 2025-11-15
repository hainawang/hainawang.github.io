---
title: " 📊 Autodebias GCN: Dual-Model Correction for Exposure Bias in Implicit Feedback"
excerpt: "Undergraduate thesis proposing a dual-LightGCN model to decompose implicit feedback into Preference and Exposure matrices, substantially reducing estimation variance and improving performance on benchmark datasets (Yahoo!R3, Coat).<br/><img src='/images/srtp_gif.gif'>"
paperurl: '../files/zjuthesis.pdf'
collection: portfolio
---




## Project Summary

* **Goal:**To address Exposure Bias in recommender systems—the issue where implicit user feedback is a joint product of Preference ($R$) and Exposure ($O$), leading to biased preference estimates.

* **Core Innovation:** Designed and implemented a novel dual-Graph Convolutional Network (GCN) model, based on LightGCN, that jointly trains separate models for the Preference Matrix ($R$) and the Exposure Matrix ($O$) using Expectation-Maximization (EM) principles.

* **Key Contributions:** Theoretically demonstrated that the proposed method significantly reduces the variance of the preference estimation compared to state-of-the-art methods like Item Propensity Weighted (IPW) models.

Validated model uniqueness by leveraging the hypothesized difference in properties (e.g., Eigenvalue distribution) between $R$ and $O$ via customized regularization terms.

Authors: Haina Wang (Undergraduate Thesis)

Institution: Zhejiang University

---

## **Problem & Model Motivation**

Modern recommender systems rely on implicit feedback (clicks, views), which suffer from **exposure bias** because we cannot distinguish if a non-click means 'dislike but exposed' or 'like but unexposed'. Existing debiasing methods, such as Weighted Matrix Factorization (WMF) and Propensity-Based models (IPW), often lead to biased estimates or suffer from high variance.

Our approach explicitly models the observation \(Y_{ui}\) as the product of two latent variables: \(Y_{ui} = R_{ui} \cdot O_{ui}\).

---

## **Technical Approach: Dual-LightGCN Architecture**

### **1. Dual-Model Training**

We utilize two parallel LightGCN models—a powerful and simplified GCN architecture—to learn the embeddings for \(R\) and \(O\).

* **Preference Model (\(R\)):** Trained to predict the user's true interest \(\xi_{ui}=P(r_{ui}=1)\).
* **Exposure Model (\(O\)):** Trained to predict the probability of exposure \(\theta_{ui}=P(o_{ui}=1)\).

The combined output, \(P(Y_{ui}=1) = \text{sigmoid}(R) \cdot \text{sigmoid}(O)\), is used for the overall loss calculation against the training data. The Preference Model output is used for final testing.

### **2. Variance Reduction (Theoretical Proof)**

A crucial theoretical contribution of this work is proving that our method effectively bounds the variance of the preference estimation loss \(L_{\text{prefer}}\).

* **IPW Issue:** The IPW estimator contains the inverse of the propensity score \(1 / P(O_{ui}=1)\), which can be very small, leading to unbounded variance in extreme cases.
* **Our Solution:** We proved that the variance of our proposed loss function is upper-bounded, demonstrating a theoretical advantage in estimation stability.

### **3. Hypothesis-Driven Regularization**

To prevent the two parallel models (\(R\) and \(O\)) from becoming redundant, we enforced structural differences based on hypotheses about user behavior:

* **Hypothesis:** The Exposure Matrix (\(O\)) has a more decentralized and polarized structure compared to the Preference Matrix (\(R\)), which exhibits stronger long-tail effects (fewer popular items dominate preference).
* **Customization:** We introduced **Eigenvalue Regularization** into the loss function, specifically leveraging the difference between the top \(k\) eigenvalues and the subsequent eigenvalues to guide the \(R\) and \(O\) models toward their hypothesized structural properties.

---

## **Experimental Results & Discussion**

* **Performance:** Comprehensive experiments on unbiased benchmark datasets (Yahoo!R3 and Coat) showed that the dual-model approach significantly outperformed single-model baselines (MF, ExpoMF) and IPW variants in terms of Recall@K and NDCG@K.

* **Ablation Studies:** We performed extensive ablation tests on LightGCN layer count and eigenvalue coefficients, confirming that introducing the Exposure Model consistently boosts the performance of the Preference Model.

* **Reflection:** While the Exposure Model itself proved challenging to train to its full theoretical potential, its inclusion served as a powerful regularizer, effectively separating the Preference signal from the Exposure noise. The analysis also revealed complex relationships between LightGCN layer counts and performance on different datasets (e.g., over-smoothing sensitivity), guiding future research directions.

---

> **Citation:** Haina Wang. "Autodebias GCN: Dual-Model Correction for Exposure Bias in Implicit Feedback." *Undergraduate Thesis, Zhejiang University (2024)*.