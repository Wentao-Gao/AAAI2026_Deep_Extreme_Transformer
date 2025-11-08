# 🌧️ Deep Extreme Transformer (DET)

**Tackling Zero-Inflated Time Series for Precipitation Prediction**  
_AAAI 2026 • Adelaide University • RMIT • Shanghai University of International Business and Economics_

<p align="center">
  <a href="https://aaai.org/Conferences/AAAI-26/"><img src="https://img.shields.io/badge/AAAI-2026-blue.svg?style=for-the-badge"></a>
  <img src="https://img.shields.io/badge/Python-3.10+-green.svg?style=for-the-badge">
  <img src="https://img.shields.io/badge/PyTorch-2.x-red.svg?style=for-the-badge">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge">
</p>

---

## 📘 Overview

**Deep Extreme Transformer (DET)** is a principled architecture that bridges **statistical distribution modeling** and **deep sequence learning** to handle **zero-inflated** and **nonstationary** time series data.  
We apply it to rainfall prediction — one of the most challenging domains due to its **extreme sparsity** and **temporal shifts**.

> DET unifies discrete zeros and continuous intensities through Tweedie distribution modeling, while enhancing the Transformer’s attention via fixed shared weights and a Gaussian perturbation strategy for stable optimization.

---

## 🧠 Motivation

Rainfall data are **zero-inflated (70–85% zeros)** and **nonstationary**, making both classical statistical models and standard Transformers ineffective.  
DET directly addresses this dual challenge with a **theoretically grounded** framework that combines:

- Statistical rigor (Tweedie mixture model for zeros & positives)  
- Deep temporal modeling (Transformer backbone)  
- Stability and robustness under extreme data sparsity  

---

## 🚀 Key Innovations

| 🧩 Component | 🌟 Purpose |
|--------------|------------|
| 🎯 **Weighted Attention** | Differentiates zero vs. non-zero samples to restore information concentration. |
| 🔢 **Tweedie Distribution Head** | Unified probabilistic modeling for zeros and continuous values. |
| 🌫️ **Gaussian Perturbation** | Smooths optimization and preserves non-negativity. |
| ⚖️ **Weighted Tweedie Loss** | Aligns training objective with rare-event importance. |
| 🌀 **Nonstationary Attention Integration** | Adapts to evolving rainfall regimes and long-term shifts. |

<p align="center">
  <img src="docs/det_diagram.png" width="820" alt="Deep Extreme Transformer Framework">
</p>

---

## 🧩 Architecture Summary

**DET Workflow:**
1. Gaussian perturbation smooths zero samples for stable gradients.  
2. Weighted Attention assigns higher weights to non-zero rainfall events.  
3. Tweedie Distribution Layer predicts `(μ, ϕ, ρ)` parameters for zero-continuous data.  
4. Weighted Tweedie Loss optimizes the model coherently with attention weights.  
5. Nonstationary Attention (τ, Δ) integrates temporal adaptivity.

---

## 📊 Experimental Setup

- **Dataset:** NCEP–NCAR Reanalysis 1 (1948–2014), South Australia  
- **Zero ratio:** ~80% dry days  
- **Split:** 70/15/15 (train/val/test)  
- **Horizon:** 24, 48, 96, 192, 336, 720 steps  
- **Baselines:** TimesNet, iTransformer, Nonstationary Transformer, TSMixer, ZIP, Hurdle, etc.

---

## 📈 Results

| Horizon | MSE ↓ | MAE ↓ |
|----------|--------|--------|
| 24 | **0.5120** | **0.2120** |
| 48 | **0.5180** | **0.2140** |
| 96 | **0.5320** | **0.2210** |
| 192 | **0.5450** | **0.2280** |
| 336 | **0.5580** | **0.2350** |
| 720 | **0.5800** | **0.2450** |

> DET achieves **21–28% lower MSE** than leading baselines and maintains superior accuracy even for 720-step forecasts.


---

## 🔬 Theoretical Highlights

- **Attention Uniformity Theorem:** proves Transformers’ attention degenerates under high zero ratios.  
- **Weighted Attention Entropy Bound:** ensures information concentration on rare but important events.  
- **Tweedie Optimality Theorem:** shows Tweedie uniquely models both zeros and positive continuous values under entropy constraints.  
- **PAC-Bayes Bound:** guarantees improved generalization with zero–nonzero balancing weights.


🌟 Highlights

📈 First Transformer with provable performance bounds on zero-inflated sequences.

🔢 Integrates Tweedie statistical modeling with deep sequence learning.

🌏 Achieves state-of-the-art results on South Australian rainfall forecasting.

💡 Applicable beyond climate science — to finance, healthcare, and other sparse-event time series.

<p align="center"> <b>💧 Bridging Statistics and Deep Learning for Sparse Temporal Prediction</b><br> <a href="https://aaai.org">AAAI 2026</a> • Adelaide University • RMIT • Shanghai University of International Business and Economics </p> ```

