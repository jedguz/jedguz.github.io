---
title: "Self-Supervised Learning for Robot Grasping"
collection: portfolio
date: 2025-08-01
display-date: "August 2025"
permalink: /portfolio/robot-grasping
excerpt: "Investigating JEPA pretraining on point clouds to improve grasp success in low-label regimes.<br/><img src='/images/grasping_pipeline.png'>"
---

**Resources:**  
- [🖼️ Poster](/files/grasping_poster.pdf)  
- [📑 Report](/files/grasping_report.pdf)

**Summary.** On the **DLR–Hand II** platform, we fine-tune a **Point–JEPA** backbone on spatially sequenced point clouds and predict grasp joint angles with a **multi-hypothesis head**. JEPA pretraining consistently improves **top-logit RMSE** in low-label regimes and boosts **coverage@15°**, with parity at 100% labels. :contentReference[oaicite:0]{index=0}

### Highlights
- **Backbone:** Point–JEPA for 3D point clouds; attention-pooled object embedding.  
- **Head:** K=5 multi-hypothesis joints + logits; **winner-takes-all** (min-over-K) training; **top-logit** selection at inference.  
- **Label efficiency:** Largest gains at **25% labels**; consistent improvements at **1–10%**; **parity** at full supervision.  
- **Evaluation:** Object-level splits; fixed val/test fixtures across label budgets.

### Results (validation)
- **Top-logit RMSE (↓)** — *Scratch → JEPA (relative gain)*  
  - **1%:** 0.363 → **0.335** *(+7.7%)*  
  - **10%:** 0.335 → **0.303** *(+9.6%)*  
  - **25%:** 0.332 → **0.246** *(+25.9%)*  
  - **100%:** 0.235 → **0.234** *(≈ parity)*
- **Selector fidelity:** Smaller **selection gap** with JEPA at 1–10% (e.g., **0.142 vs 0.165** at 1%; **0.157 vs 0.176** at 10%).  
- **Coverage@15° (↑):** Higher with JEPA in low-label settings (e.g., **0.955 vs 0.938** at 10%; **0.866 vs 0.861** at 1%). :contentReference[oaicite:1]{index=1}

### Method at a Glance
1. **Tokenize** meshes → point-cloud patches; positional encodings.  
2. **Pretrain** JEPA (context vs. target encoders; EMA target).  
3. **Pool** contextualized patch features → global object embedding.  
4. **Predict** K joint-angle hypotheses + logits given object embedding + wrist pose.  
5. **Train** with WTA / min-over-K + cross-entropy on the winning hypothesis; **infer** with top-logit.

**Status:** *Aiming for workshop submission (in progress).* 
