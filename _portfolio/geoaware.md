---
title: "GeoAware3D — Geometry-Aware 3D Semantic Features"
collection: portfolio
date: 2025-08-01
permalink: /portfolio/geoaware3d
excerpt: "Zero-shot, class-agnostic 3D feature decoration by fusing Stable Diffusion + DINO via multi-view projection/unprojection; fast correspondence on SHREC’19.<br/><img src='/images/geoaware3d_pipeline.png'>"
---

**Summary.** We propose **GeoAware3D**, a zero-shot, class-agnostic method to decorate meshes/point clouds with **geometry-aware semantic features**. We (i) render multi-view images, (ii) add texture via **ControlNet-guided** diffusion, (iii) fuse **Stable Diffusion + DINO** features, and (iv) **unproject** per-pixel descriptors back to 3D, aggregating with \(k\)-NN mean to obtain vertex/point-wise features. No training or extra data required.

### Highlights
- **No training / no extra data**; works on untextured shapes.
- **Projective analysis**: 3D → 2D renders → fused features → **unprojection** to 3D.
- **Two correspondence modes**: closest-vertex or direct point-to-point.
- **Geometry-aware fusion** improves robustness to pose and symmetries.

### Results (SHREC’19, humans)
- **Accuracy:** 23.42% vs. **DIFF3F** 26.41% and **SE-ORNet** 21.41%.  
- **Runtime:** **~1.02 min/mesh** (DIFF3F ~4.42 min/mesh).  
- **Ablations:**  
  - 2D-only corr.: 16.12%  
  - Standard SD+DINO: 17.81%  
  - Hyperfeatures: 18.54%  
  - GeoAware3D: 23.35% (32 views) → **23.42%** (64 views)

### Method at a Glance
1. **Render** \(k\) views (uniform azimuths, fixed elevation).  
2. **Texture** each view using ControlNet (prompted high-def photo realism).  
3. **Fuse** SD + DINO features (geometry-aware aggregation).  
4. **Unproject** per-pixel features to 3D with depth + intrinsics \(K\); build a point cloud of descriptors.  
5. **Aggregate** to vertices via \(k\)-NN mean; compute cosine-similarity correspondences (vertex- or point-level).

**Resources:**  
- [🖼️ Poster](/files/geoaware_poster.pdf)  
- [📑 Report](/files/geoaware_report.pdf)  
