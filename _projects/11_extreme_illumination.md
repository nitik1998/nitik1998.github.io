---
layout: page
title: Extreme-Illumination Image Restoration
description: A lightweight U-Net for low-light and multi-exposure RGB enhancement, benchmarked against Zero-DCE++ on PSNR, SSIM, and LPIPS. JHU Computer Vision course project (Fall 2025).
img: /assets/img/projects/extreme.jpg
importance: 2
category: Computer Vision & Perception
github: https://github.com/nitik1998/extreme-illumination-image-restoration
report: /assets/pdf/reports/cv_illumination_report.pdf
---

A benchmark of deep models for **low-light and multi-exposure RGB enhancement**, built as a Johns Hopkins
**Computer Vision** course project (Fall 2025, with Man Namgung, Patrick Li, and Sahen Juneja). The lightweight,
SID-inspired **U-Net** clearly outperforms the curve-estimation baseline.

{% include figure.liquid loading="eager" path="assets/img/projects/extreme.jpg" class="img-fluid rounded z-depth-1" %}
<div class="caption">Low-light restoration — degraded inputs recovered by the U-Net toward the reference exposure.</div>

## Results

| Model | PSNR ↑ | SSIM ↑ | LPIPS ↓ |
|---|---|---|---|
| Zero-DCE++ | 11.49 | 0.668 | 0.219 |
| **U-Net** | **18.44** | **0.782** | **0.209** |

The U-Net achieves a **+6.95 dB PSNR** improvement over Zero-DCE++.

{% include figure.liquid loading="lazy" path="assets/img/projects/extreme_multi.jpg" class="img-fluid rounded z-depth-1" %}
<div class="caption">Multi-exposure correction across over- and under-exposed scenes.</div>

## Highlights

- Clean, modular training/eval/inference pipeline with mixed-precision and efficient data loading.
- Consistent benchmarking across **PSNR, SSIM, and LPIPS** (perceptual) metrics.
- SID-inspired architecture tuned for restoration under illumination extremes.

## Stack

PyTorch · U-Net · Zero-DCE++ · mixed-precision training · PSNR/SSIM/LPIPS
