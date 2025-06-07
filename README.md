# TJUAV Computer Vision

This repository contains the computer vision pipeline developed by the [TJUAV](https://tjuav.org) team for participation in the [Student Unmanned Aerial Systems (SUAS) Competition](https://suas-competition.org/). Our system is built to support autonomous object detection from aerial imagery using deep learning, deployed on an NVIDIA Jetson platform onboard the aircraft.

## Overview

During flight missions, our UAV captures video footage over a designated field or drop zone. The primary objective is to detect specific objects placed within this area, as required by SUAS rules, and relay that information to a ground control station for mission evaluation.

We use YOLO (You Only Look Once) object detection models to perform this task in real-time. The models are trained on synthetic aerial data and optimized for execution on edge hardware in dynamic field conditions.

## Methodology

1. **Image Collection**  
   High-resolution aerial images of the competition drop zone are captured from past flights or simulation environments.

2. **Synthetic Data Generation**  
   Images representing mission-relevant objects (e.g., vehicles, markers, shapes) are manually annotated with bounding boxes. These labeled objects are then randomly composited onto background aerial images to generate realistic synthetic datasets.

3. **Model Training**  
   YOLO models are trained on this synthetic dataset using PyTorch-based frameworks. The models learn to detect object classes under various lighting, orientation, and scale conditions.

4. **Onboard Deployment**  
   Trained YOLO models are exported and deployed to an NVIDIA Jetson device. This edge device runs the real-time detection pipeline, continuously processing video frames from an onboard camera during flight.

5. **Map Integration**  
   Detected object coordinates are logged and optionally fed into a larger map-stitching pipeline for visualization and scoring.
