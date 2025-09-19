---
title: "Privacy Amplification by Structured Subsampling for Deep Differentially Private Time Series Forecasting"
collection: publications
category: manuscripts
permalink: /publication/2009-10-01-paper-title-number-1
excerpt: "ICML 2025 Spotlight. Structured subsampling for DP time-series; tight event- and user-level guarantees; empirical validation."
date: 2025-07-01
venue: "International Conference on Machine Learning (ICML) — Spotlight"
paperurl: "https://arxiv.org/abs/2502.02410"
#publisherurl: "https://icml.cc/virtual/2025/poster/44722"
#openreview: "https://openreview.net/forum?id=bkauyuzBN4"
citation: "Guzelkabaagac, J., Schuchardt, J., et al. (2025). Privacy Amplification by Structured Subsampling for Deep Differentially Private Time Series Forecasting. ICML 2025 (Spotlight)."
---
We analyze why standard DP-SGD amplification assumptions break for forecasting—where batches come from (i) sampling series, (ii) contiguous subsequences, (iii) context/forecast splits—and provide tight event- and user-level guarantees via **structured subsampling**. We also prove amplification from sequence-model augmentation and validate empirically.

**Contribution:** I worked on appendix-level optimization/proof pieces:
- Derived a componentwise upper bound \(H_\alpha(P,Q)\le\sum_{i,j} w_i v_j\,H_\alpha(p_i,q_j)\) under lattice-path constraints on the means.
- Recast the bound as a shallow network with the closed-form “Gaussian hockey-stick” activation \(g_\varepsilon(d)=\Phi(d/2-\varepsilon/d)-e^{\varepsilon}\Phi(-d/2-\varepsilon/d)\).
- Built a certified SOCP relaxation via a single-tangent affine envelope on \(d\in[0,R_{ij}]\).

 Main writing and experiments were led by the first authors.

**WIP (tightening the relaxation).**
- Add **shared distance coupling** via a PSD/Gram-matrix formulation to prevent joint saturation while staying convex.
- Note: **multi-segment (SOS-2) envelopes alone** still push to the rightmost knot; they don’t fix the degeneracy.
