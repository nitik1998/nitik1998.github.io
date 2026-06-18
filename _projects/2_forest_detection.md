---
layout: page
title: Forest Occlusion Detection
description: Human detection under sparse forest occlusion using RGB-thermal fusion and aerial imaging.
img: /assets/img/projects/forest_multimodal.jpg
importance: 1
category: Computer Vision & Perception
related_publications: true
paper: https://europepmc.org/article/PPR/PPR667482
report: /assets/pdf/reports/forest_occlusion_thesis.pdf
slides: /assets/pdf/reports/forest_occlusion_slides.pdf
featured: true
tldr: "RGB-thermal fusion with Airborne Optical Sectioning to detect people through forest canopy — ~70% occlusion removal and +32% detection accuracy."
---

**Master's Thesis** at IIT Kanpur under the advisement of **Dr. Mangal Kothari**, published as {% cite jain2026occlusion %}.

## Problem

Detecting humans in forested areas with sparse occlusion presents significant challenges for autonomous aerial vehicles. Traditional computer vision methods fail when objects are partially obscured by canopy and vegetation.

## Methodology

### Sensor Fusion
- Developed a **sensor fusion model** integrating RGB and thermal image modalities
- Created integral image representations to improve visibility of concealed targets

### Airborne Optical Sectioning (AOS)
- Implemented **AOS techniques** on fused images in a synthetic-aperture imaging framework
- Improved focus on target depth while reducing occluding clutter

### Deep Learning Enhancement
- Employed **transfer learning** to fine-tune YOLOv5 for forest environments
- Trained on aerial imagery with sparse-occlusion patterns

{% include figure.liquid loading="lazy" path="assets/img/projects/forest_aos.jpg" class="img-fluid rounded z-depth-1" %}
<div class="caption">RGB and thermal modalities fused into Airborne Optical Sectioning integral images — concealed targets emerge as the synthetic aperture removes occluding canopy.</div>

## Outcomes

| Metric | Improvement |
|--------|-------------|
| Occlusion Removal | ~70% improvement in simulation |
| Detection Accuracy | 32% gain over baseline YOLO |

## Applications

- Search and rescue operations in forested terrain
- Wildlife monitoring and conservation
- Border surveillance in vegetated areas
- Agricultural monitoring through canopy

## Technologies

- Python, PyTorch
- YOLOv5
- ROS for UAV integration
- Synthetic aperture imaging algorithms
