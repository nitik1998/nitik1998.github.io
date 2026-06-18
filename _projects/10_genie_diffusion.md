---
layout: page
title: GENIE — Learning Latent Structure with Diffusion Models
description: GSoC 2026 / ML4SCI evaluation — learning compact latent representations, classifying jets via graph structure, and generating physics-realistic jets with a latent diffusion model.
img: /assets/img/projects/genie.png
importance: 1
category: Generative Models & NLP
github: https://github.com/nitik1998/GENIE_DiffusionLearning
report: /assets/pdf/reports/genie_report.pdf
award: "Google Summer of Code 2026 · ML4SCI"
---

A three-task generative-modeling pipeline on **139,306 quark/gluon calorimeter jet images** (125×125×3),
built for the **ML4SCI GENIE** Google Summer of Code 2026 evaluation. Each task builds on the previous:
learn a compact latent space, classify with graph structure, then generate new jets via latent diffusion.

[Technical report]({{ '/assets/pdf/reports/genie_report.pdf' | relative_url }}) ·

## Results

| Task | Model | Metric | Score |
|---|---|---|---|
| **1 — Reconstruction** | Convolutional VAE | PSNR / SSIM | **37.93 dB** / **0.967** |
| **2 — Classification** | GraphSAGE on k-NN graphs | ROC-AUC / Acc | **0.774** / **70.6%** |
| **3 — Generation** | Latent DDPM | PSNR / SSIM | **30.32 dB** / **0.931** |

{% include figure.liquid loading="eager" path="assets/img/projects/genie_recon.png" class="img-fluid rounded z-depth-1" %}

## Approach

- **Task 1 — Representation:** a convolutional VAE compresses each jet image to a low-dimensional latent that
  preserves detector structure (high PSNR/SSIM reconstruction).
- **Task 2 — Structure:** treat jets as k-NN graphs over active calorimeter cells and classify quark vs. gluon
  with **GraphSAGE**, exploiting topology rather than raw pixels.
- **Task 3 — Generation:** a **latent DDPM** samples new, physics-realistic jets in the VAE latent space —
  cheaper and more stable than pixel-space diffusion.

## Stack

PyTorch · Convolutional VAE · DDPM (latent diffusion) · GraphSAGE / PyG · quark–gluon jet dataset
