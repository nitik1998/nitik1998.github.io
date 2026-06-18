---
layout: page
title: PAVE — Probing Affordance in VLA Encoders
description: Do vision-language-action models keep the affordance signal of their foundation encoders? A study of class-asymmetric degradation, its mechanism, and a lightweight recovery.
img: /assets/img/projects/pave.png
importance: 1
category: Robot Learning
github: https://github.com/nitik1998/PAVE
chart:
  chartjs: true
slides: /assets/pdf/reports/pave_slides.pdf
featured: true
tldr: "Do vision-language-action models keep the affordance signal of their foundation encoders? They lose it class-asymmetrically — and a 297K-parameter adapter recovers 82% of it."
---

**PAVE** asks a simple question with real consequences for robot manipulation: when a foundation vision
encoder (DINOv2, SigLIP-So400m) is fine-tuned end-to-end into a **vision-language-action (VLA)** policy
(π₀, π₀.₅, OpenVLA), does its per-class **affordance** signal survive — and if not, can we get it back?

*JHU EN.601.495/695 — Introduction to Robot Learning (Spring 2026).*
[Slides]({{ '/assets/pdf/reports/pave_slides.pdf' | relative_url }}) ·

## Key findings

1. A 60-second linear probe on **DINOv2-large @ 560²** scores **0.776 mIoU** on UMD Part Affordance —
   **+10.6 pp** over the published Zhang *et al.* (CVPR 2026) dense decoder (0.670), with no decoder,
   no fine-tuning, and no augmentation.
2. End-to-end VLA fine-tuning **silently degrades** the affordance signal in the SigLIP tower — but the loss is
   **class-asymmetric**: π₀ loses 27 pp on `cut` and 17 pp on `support`, while `contain` is preserved (−1 pp).
3. The pattern **generalizes across two VLA families** (PaliGemma-backboned π₀/π₀.₅, Prismatic-Llama OpenVLA)
   — it is recipe-independent.
4. Per-class feature **drift predicts** the per-class IoU drop (Spearman ρ = 0.90; Pearson r = 0.95 on OpenVLA).
   Mechanism predicts behavior.
5. A **297K-parameter MLP adapter** on frozen π₀ features recovers `cut` IoU from 0.181 → 0.405 —
   closing **82%** of the gap. *The signal was rotated, not deleted.*

{% include figure.liquid loading="eager" path="assets/img/projects/pave_spectrum.png" class="img-fluid rounded z-depth-1" %}

## Results at a glance

The `cut` affordance signal collapses under end-to-end VLA fine-tuning — and a 297K-parameter adapter
recovers most of it (interactive; hover for values):

```chartjs
{
  "type": "bar",
  "data": {
    "labels": ["Standalone SigLIP", "π₀ (post-VLA)", "π₀ + 297K Adapter"],
    "datasets": [{
      "label": "cut affordance IoU (↑)",
      "data": [0.451, 0.181, 0.405],
      "backgroundColor": ["rgba(45,120,173,0.75)", "rgba(255,83,83,0.75)", "rgba(58,204,58,0.75)"],
      "borderColor": ["rgba(45,120,173,1)", "rgba(255,83,83,1)", "rgba(58,204,58,1)"],
      "borderWidth": 1
    }]
  },
  "options": {
    "scales": { "y": { "beginAtZero": true, "max": 0.5, "title": { "display": true, "text": "IoU" } } },
    "plugins": { "legend": { "display": true } }
  }
}
```

Per-class IoU drop after fine-tuning: **`cut` −27 pp**, **`support` −17 pp**, **`contain` −1 pp** — the loss is
sharply class-asymmetric, and per-class feature drift predicts it (Spearman ρ = 0.90).

{% include figure.liquid loading="lazy" path="assets/img/projects/pave_umd_qual.png" class="img-fluid rounded z-depth-1" %}

## Why it matters

Manipulation pipelines increasingly sit on top of VLA policies. If fine-tuning quietly destroys *where you can
cut / grasp / contain*, downstream affordance reasoning inherits a blind spot no one measured. PAVE shows the
degradation is real, characterizes **which classes** break and **why**, and demonstrates a cheap fix.

## Approach

- **Probing:** frozen patch features → a 60-second `sklearn` logistic-regression probe on UMD Part Affordance
  (no decoder, no fine-tuning), comparing standalone encoders vs. their post-VLA counterparts.
- **Mechanism:** per-class final-layer feature drift (CKA / centroid shift) between standalone and post-VLA
  encoders, correlated against the measured per-class IoU drop.
- **Recovery:** a tiny MLP adapter trained on frozen π₀ features to re-rotate the lost subspace back.

{% include figure.liquid loading="lazy" path="assets/img/projects/pave_recovery.png" class="img-fluid rounded z-depth-1" %}

{% include figure.liquid loading="lazy" path="assets/img/projects/pave_cross_domain.png" class="img-fluid rounded z-depth-1" %}
<div class="caption">The class-asymmetric pattern reproduces across two VLA families (π₀/π₀.₅ and OpenVLA) — it is recipe-independent.</div>

## Key finding

The 27 pp deficit is largely a **multi-class-probing artifact**: on the binary part-discrimination formulation
that real grasp pipelines (Aff-Grasp, GIFT, Kokic *et al.*) actually use, all VLAs are essentially
indistinguishable from the foundation encoder. The honest story is nuanced — and that nuance is the contribution.

## Stack

DINOv2 · SigLIP-So400m · π₀ / π₀.₅ (PaliGemma) · OpenVLA (Prismatic-Llama) · PyTorch · UMD Part Affordance · scikit-learn
