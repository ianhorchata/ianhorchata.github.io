---
title: Ongoing Senior Design Project
date: 2026-10-01
year: Fall 2026
summary: Simulation and early prototyping of a robotic delivery service for ME Senior Design class Lafayette College.
tags:
  - ROS 2
  - LiDAR
  - Robotics
  - WeBots
repo: https://github.com/ianhorchata/SeniorDesign_4a/tree/main
image: /assets/images/senior-design-rviz.png
image_alt: Screenshot of RViz with navigation trajectory shown.
---

ME Senior Design under Professor Shi. This semster is a proof-of-concept prototype.
## Hardware

The hardware should be capable of traversing stairs to deliver food to different floors, and travel around the many stairs across campus.

## Software

The robot must be able to sense it's environment and create a trajectory towards the goal which avoids obstacles. This is done by dynamically generating a 3D map via OctoMap, and then running A* to generate the trajectory to a given point.