---
layout: page
title: Onboard 3D Detection and Tracking
description: Lightweight stereo-vision pipeline for real-time detection and tracking on edge hardware.
img: /assets/img/projects/onboard.jpg
importance: 3
category: Computer Vision & Perception
slides: /assets/pdf/reports/onboard_3d_slides.pdf
featured: true
tldr: "A lightweight stereo-camera YOLO pipeline for real-time onboard object detection and 3D tracking on resource-constrained edge hardware."
---

## Problem

Design a lightweight computer-vision stack for onboard object detection and tracking with stereo cameras under constrained compute.

## What I Built

- Implemented a real-time YOLO-based detection and tracking pipeline.
- Computed 2D bounding boxes and centroids using depth maps from Intel RealSense.
- Tuned the pipeline for low latency and stable tracking in live settings.

{% include figure.liquid loading="lazy" path="assets/img/projects/onboard_track.jpg" class="img-fluid rounded z-depth-1" %}
<div class="caption">Real-time YOLO detection with depth-derived centroids for onboard tracking.</div>

## Outcomes

- Achieved strong real-time performance on commodity NVIDIA GPU hardware.
- Maintained stable tracking at interactive frame rates in field-like tests.

## Technologies

- Python, C++
- YOLO-based detection
- Intel RealSense depth sensing
- OpenCV
