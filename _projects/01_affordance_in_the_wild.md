---
layout: page
title: Affordance in the Wild — Generative World-Models
description: Do text-to-image diffusion models carry affordance? Probing FLUX & Cosmos verb-conditioned cross-attention against ground-truth affordance heatmaps.
img: /assets/img/projects/vla_affordance.png
importance: 2
category: Robot Learning
github: https://github.com/aleksantari/VLA-affordance/tree/nj-features
featured: true
tldr: "Do text-to-image diffusion models carry affordance? FLUX cross-attention aligns with ground-truth affordance far above chance — and the cheaper model probes it better."
---

*Team project (with Aleks Antari), JHU Introduction to Robot Learning, Spring 2026.* This study asks whether
two opposite robot-visual paradigms — **VLA encoders** (image → action) and **generative world-models**
(language → image) — carry fine-grained **affordance** structure. I led **Axis 2: generative world-models**;
[**PAVE**]({{ '/projects/0_pave/' | relative_url }}) is the deep dive on Axis 1 (VLA encoders).

## Axis 2 — does a text-to-image diffusion model "know" affordance?

I extract **verb-conditioned cross-attention** maps from **FLUX.1** (schnell & dev) on **AGD20K**
(n = 1,675 egocentric samples, 36 affordance categories) and score them against ground-truth affordance
heatmaps with saliency metrics (KLD, SIM, NSS).

## Findings

**1 — Diffusion models carry incidental affordance.** FLUX cross-attention aligns with affordance ground
truth far above chance (**KLD 1.86**, 31% below the uniform null; **SIM 0.25**, +67%; **NSS +0.43**) —
despite never being trained on robot data or affordance labels.

**2 — The *cheap* model wins (counterintuitive).** FLUX-schnell (4 steps, no CFG) statistically beats
FLUX-dev (20 steps + classifier-free guidance, 5× the compute) on KLD and SIM (Mann-Whitney *p* < 10⁻⁴).
CFG sharpens the model onto what it *thinks* the scene should be, drifting from the real image — so the fast
config is a *better* measurement tool.

{% include figure.liquid loading="lazy" path="assets/img/projects/vla_schnell_dev.png" class="img-fluid rounded z-depth-1" %}

**3 — Manipulation verbs bind *weaker* than postural verbs** (NSS +0.349 vs +0.509, *p* = 3×10⁻⁹). Binding
strength is set by the *geometry* of the ground-truth region (sharp for `lie_on`/`talk_on`, diffuse for
`push`/`brush_with`), not by whether the verb names a manipulation primitive — refuting the intuitive prior.

{% include figure.liquid loading="lazy" path="assets/img/projects/vla_affordance.png" class="img-fluid rounded z-depth-1" %}

**4 — Pre-registered thresholds, honestly reported.** H2a thresholds were committed *before* data collection;
the strict version is refuted, the qualitative version (binding above null) confirmed. The gap to published
numbers is shown to be **methodology-bound, not model-bound** (schnell↔dev convergence rules out the model),
keeping the FLUX-vs-Cosmos cross-axis comparison valid under one identical pipeline.

## Stack

FLUX.1 (schnell/dev) · Cosmos-Predict2 · cross-attention extraction · AGD20K · KLD / SIM / NSS saliency metrics · PyTorch · T5 tokenization
