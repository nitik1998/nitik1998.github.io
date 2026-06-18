---
layout: page
title: Daksh II - Autonomous Ground Vehicle
description: Outdoor autonomous ground vehicle for lane following and obstacle avoidance; multiple IGVC accolades.
img: /assets/img/projects/daksh_maze.jpg
importance: 1
category: Autonomous Systems & SLAM
github: https://github.com/IGVC-IITK
paper: https://ieeexplore.ieee.org/document/9784787/
report: /assets/pdf/reports/daksh_design_report.pdf
video: https://www.youtube.com/watch?v=emXtgtBRtSA
award: "IGVC 2019 — 2nd Worldwide (Lescoe Cup); 4 international awards"
featured: true
tldr: "An end-to-end ROS autonomy stack (perception, SLAM, planning) for outdoor navigation — placed 2nd worldwide at IGVC 2019."
---

**Daksh II** is an autonomous ground vehicle developed at IIT Kanpur under Team VISiON for the Intelligent Ground Vehicle Competition (IGVC).

{% include figure.liquid loading="eager" path="assets/img/projects/daksh_maze.jpg" class="img-fluid rounded z-depth-1" %}
<div class="caption">Daksh II autonomously navigating a maze with live lane segmentation and path planning — <a href="https://www.youtube.com/watch?v=emXtgtBRtSA" target="_blank" rel="noopener">watch the run ▶</a>.</div>

## Problem

Build a reliable AGV capable of outdoor navigation on grassy terrain while following lane boundaries and avoiding static and dynamic obstacles.

## What I Built

### Perception
- Implemented a low-latency **Fast-SCNN-based semantic segmentation** network
- Added depth-wise separable convolutions and inverted residual blocks for efficient lane understanding

### SLAM & Mapping
- Built a **global mapper** ROS publisher with LiDAR-camera fusion
- Generated occupancy maps for real-time navigation

### Path Planning
- Used **costmap_2d** with **RRT** for smooth path generation
- Tuned planning for low-latency execution on the vehicle computer

## Outcomes

At **IGVC 2019**, Team VISiON achieved multiple top finishes, including **Lescoe Cup (2nd worldwide)** and podium finishes in autonomous navigation tracks.

## Technologies Used

- ROS (Robot Operating System)
- Python, C++
- LiDAR (Velodyne)
- Intel RealSense Camera
- Deep Learning for segmentation

## Team

Led a **3-tier team of 21 students** as Team Leader of Team VISiON (2019-2021), orchestrating funding drives that successfully procured $35,000 for development.
