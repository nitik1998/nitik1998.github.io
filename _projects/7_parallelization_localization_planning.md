---
layout: page
title: Parallelization of Localization and Planning Algorithms
description: GPU acceleration study for SLAM-style localization/planning pipelines.
img: /assets/img/projects/gpu_slam.jpg
importance: 3
category: Autonomous Systems & SLAM
report: /assets/pdf/reports/parallelization_report.pdf
---

## Problem

Improve computational efficiency of localization and planning pipelines by parallelizing key components on GPU.

## What I Built

- Implemented Particle Filter SLAM on 2D LiDAR data from a ground robot.
- Profiled computation bottlenecks and parallelized **~87% of pipeline stages** on **CUDA**.
- Compared speed and scaling behavior against CPU implementations.

## Outcomes

- GPU acceleration scaled **linearly** with particle count, versus the CPU's **exponential** blow-up.
- Substantial runtime gains that widen as the particle filter grows.

{% include figure.liquid loading="lazy" path="assets/img/projects/gpu_slam_perf.jpg" class="img-fluid rounded z-depth-1" %}
<div class="caption">Operating frequency vs. particle count — GPU (CUDA) holds up where the CPU degrades.</div>

## Technologies

- C++
- CUDA
- Particle Filter SLAM
- 2D LiDAR processing
