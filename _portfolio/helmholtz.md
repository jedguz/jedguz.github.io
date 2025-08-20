---
title: "AI-Driven RNA Drug Discovery — TUM Data Innovation Lab × Helmholtz"
collection: portfolio
date: 2025-04-30
display-date: "April 2025"
permalink: /portfolio/rna-drug-discovery
excerpt: "Sequence-based prediction of RNA–small-molecule binding affinity using RNA-FM and GNN encoders; LoRA fine-tuning and pocket-aware pretraining.<br/><img src='/images/rna_sm.png'>"
---

**Resources:**  
- [📑 Report](/files/helmholtz_report.pdf)

**Summary.** In collaboration with the **TUM Data Innovation Lab (MDSI)** and **Helmholtz Munich (Computational RNA Biology Lab)**, we built and evaluated deep learning models that predict **RNA–small-molecule binding affinity** directly from **RNA sequence** and **SMILES**—bypassing the need for solved RNA 3D structures. We curated and cleaned R-SIM data, designed **interpolation** and **extrapolation** splits, and compared sequence-only deep models against the RSAPred baseline.

### Highlights
- **Encoders:** RNA-FM (frozen / **LoRA** fine-tuned) and a 1D-CNN for RNA; **GIN / Graph Diffusion / MolCLR** for molecules.  
- **Combination layers:** **Concatenation** vs **cross-attention**; pocket-aware **pretraining** from PDB-derived RNA–ligand interactions.  
- **Data work:** Deduplication, family assignment fixes, and robust split design to test **generalization** (no RNA overlap in extrapolation).  

### Key results
- **Interpolation (easier)**: Best MAE ≈ **0.75** with **RNA-FM (frozen) + GIN**; deep models outperform **RSAPred**.  
- **Extrapolation (hard)**: Best MAE ≈ **1.34** with **RNA-FM (LoRA) + Graph Diffusion**; still challenging but **better than RSAPred** and mean-predictor baselines.  
- **Classification**: Fixed-threshold AUROC ≈ 0.5; **ranking accuracy ~60%** with RNA-FM+MolCLR—better than chance but leaves headroom.  
- **Pocket pretraining**: Helpful for sparsity intuition; **no clear downstream gain** at current scale.

### Method at a glance
1. **Encode** RNA (RNA-FM / 1D-CNN) and molecules (GIN / Graph Diffusion / MolCLR).  
2. **Fuse** via concatenation or cross-attention; optional pocket-aware pretraining for attention.  
3. **Head**: MLP regressor on pKd; LoRA for parameter-efficient RNA-FM adaptation.  
