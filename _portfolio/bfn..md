---
title: "Understanding Bayesian Flow Networks"
collection: portfolio
date: 2025-08-01
permalink: /portfolio/bayesian-flow-networks
excerpt: "Explainer of Bayesian Flow Networks (BFNs).<br/><img src='/images/bfn_img.png'>"
mathjax: true
---

**Type:** Seminar explainer of *Bayesian Flow Networks* (Bayes et al.) [Original paper (arXiv)](https://arxiv.org/pdf/2308.07037)

**Summary.** BFNs are generative models that update **distribution parameters** (not noisy data) via Bayesian rules. With an accuracy schedule \( \beta(t)=\int_{0}^{t}\alpha(t')\,dt' \), the explainer derives discrete- and continuous-time losses and a practical sampler.  
_This page summarizes my TUM seminar write-up; all diagrams are original._ :contentReference[oaicite:0]{index=0}

**Key points**
- Sender \(p_S(y\mid x;\alpha_t)\) and receiver \(p_R(y\mid \hat{x}_t;\alpha_t)\); train by minimizing \(\mathrm{KL}(p_S\Vert p_R)\).
- Bayesian updates \( \theta_t = h(\theta_{t-1}, y_t, \alpha_t) \) induce an update law \(p_U\) with **additive accuracies**.
- The **flow** \(p_F(\theta\mid x;t)\) enables one-step training; sampling alternates \(\hat{x}_t=\Psi(\theta_{t-1}, t-1)\), draw \(y\sim p_R\), update \(\theta_t\).
- Where BFNs fit: parameter-space guidance for discrete & continuous data; contrasts with diffusion / AR / VAEs.

**Resources:** 
- [🖼️ Slides](/files/BFN_slides.pdf)
- [📑 Report](/files/BFN_report.pdf)
