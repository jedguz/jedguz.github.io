---
title: "Understanding Bayesian Flow Networks — Explainer & Analysis"
collection: portfolio
date: 2025-08-01
permalink: /portfolio/bayesian-flow-networks
excerpt: "A math-first walkthrough of Bayesian Flow Networks (BFNs): sender/receiver view, accuracy schedules, discrete vs. continuous-time losses, and sampling.<br/><img src='/images/bfn_img.png'>"
---

**Type:** Explainer & critical analysis (no new code or experiments)

**Summary.** This report demystifies **Bayesian Flow Networks (BFNs)** — generative models that operate on **distribution parameters** rather than noisy data. Using a sender–receiver formulation with **Bayesian parameter updates** and an **accuracy schedule** \( \beta(t)=\int_0^t \alpha(t')\,dt' \), the explainer derives both **discrete-time** and **continuous-time** training objectives, clarifies sampling, and situates BFNs among autoregressive, diffusion, VAE, and flow-based approaches. :contentReference[oaicite:0]{index=0}

### Key ideas covered
- **Sender distribution** \(p_S(y\mid x;\alpha_t)\): factorized noise model whose precision grows with \(\alpha_t\).  
- **Bayesian parameter updates:** \( \theta_t = h(\theta_{t-1}, y_t, \alpha_t) \); introduces the **additive accuracies** property so that sequential updates sum in accuracy.  
- **Output & receiver:** network \( \Psi(\theta_{t-1}, t-1) \to \hat x_t \) defines \(p_O\), inducing a **receiver** \(p_R(y\mid \hat x_t;\alpha_t)=\mathbb{E}_{p_O} p_S(y\mid x';\alpha_t)\).  
- **Continuous-data example:** Gaussian sender \( \mathcal{N}(y\mid x,\alpha_t^{-1}I) \) with closed-form mean updates \( \mu_t \) and **update distribution** \(p_U(\mu_t\mid\mu_{t-1},x;\alpha_t)\).  
- **Bayesian flow distribution** \(p_F(\theta\mid x;t)=p_U(\theta\mid\theta_0,x;\beta(t))\): simplifies training via direct sampling at time \(t\).  
- **Losses:**  
  - Discrete: \(L_n(x)=\sum_{i=1}^n \mathrm{KL}\big(p_S(\cdot\mid x;\alpha_i)\ \Vert\ p_R(\cdot\mid \hat x_{i-1};\alpha_i)\big)\).  
  - Continuous: \(L_\infty(x)\) via the \(n\!\to\!\infty\) limit, avoiding fixed step counts and easing gradients.  
- **Sampling:** discrete-time loop that alternates prediction \( \hat x_t=\Psi(\mu,t) \), synthetic observation from \(p_R\), and Bayesian update of \(\mu,\rho\).

### What this explainer adds
- **Clear, unified notation** for sender/receiver, updates, and schedules across discrete & continuous time.  
- **Step-by-step derivations** of \(p_U\) and \(p_F\) and how they yield practical training estimators.  
- **Bridging intuition:** why operating in **parameter space** enables continuous, differentiable guidance even for discrete data.  
- **Where BFNs fit:** contrasts with diffusion on discrete domains and why BFNs can excel on text-like tasks.

**Resources:**  
- [🖼️ Slides](/files/BFN_slides.pdf)  
- [📑 Report](/files/BFN_report.pdf)  

