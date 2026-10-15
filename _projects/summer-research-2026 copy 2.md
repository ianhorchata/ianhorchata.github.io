---
title: Test1
date: 2026-08-01
year: Summer 2026
summary: A mobile robot that finds small objects with stereo cameras and picks them up with a custom arm. Summer research at Lafayette College.
tags:
  - ROS 2
  - Computer vision
  - Robotics
repo: https://github.com/ianhorchata/SummerResearch2026
image: https://i.ytimg.com/vi/UcSSc0AryHc/hqdefault.jpg
image_alt: Still from a demo of the Create3 grabbing an object with a custom arm
videos:
  - title: Successful grab
    url: https://www.youtube.com/watch?v=UcSSc0AryHc
    id: UcSSc0AryHc
  - title: Successful sweep
    url: https://www.youtube.com/watch?v=dUKRa-kdFyE
    id: dUKRa-kdFyE
---

Summer research at Lafayette College, supervised by Professor Yu. The robot is built to notice small objects, drive up to them, and pick them up.

## Hardware

The base is an iRobot Create3. An NVIDIA Jetson Orin Nano rides on it and runs the software. A custom 3D-printed arm uses four LX-224 serial bus servos, which report their own position so the arm can run closed loop. The arm has a separate battery, because the servos can draw more than the Create3 can spare once the Jetson is powered. Two IMX219 cameras sit where their views overlap in front of the robot, and a printed basket catches what the arm picks up.

## Software

The Jetson runs ROS 2. The Create3 publishes its own topics over a USB-C Ethernet link, and the two computers share a ROS domain. Vision does not run on every frame. A service takes the latest image from each camera, segments objects, and keeps the ones that match across both views. Matching uses the epipolar constraint, then a cost matrix, so nearby objects are not paired with the wrong partner. Matched objects are triangulated into a pose on the ground.

To pick something up, the robot waits until it has stopped, because vibration blurs the cameras. It looks for the same object across a few frames, drives to a standoff, checks the pose again, solves a planar grab, and drops the object in the basket. A coverage mode undocks, travels a rectangle in a back-and-forth path, and scans at each stop.

URDF models exported from CAD are used in RViz, and a Gazebo setup is layered on iRobot's Create3 simulator. That simulation is still in progress. The repository has the ROS graph, launch files, and notes on getting the laptop, the Jetson, and the Create3 onto one graph with Fast DDS.
