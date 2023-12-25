---
layout: post
title:  "Night Collision Avoidance System by detection of Forward Vehicles in drive lane and Head-up Display notification"
date:   2018-6-31
excerpt: "Undergraduate Thesis (Korean version)."
project: true
tag:
- ADAS 
- Autonomous Vehicle 
- Computer Vision
- Image processing
- Machine Learning
comments: false
---
<div align="center">
<img src="../assets/img/UndergradThesis/UG_Thesis.png" width="300" height="200" alt="ADAS system with Head-up display." style="display: block; margin: 0 auto;">
</div>

## Summary
We efficiently detected the taillights of front vehicles in nighttime environments by converting the RGB color space to HSV and YCbCr. The detection of taillights was used to generate a candidate pool for vehicles. Haar-like features and the AdaBoost algorithm were then employed, validating the vehicles using 2000 positive and 5000 negative images. A Region of Interest (ROI) was specified to reduce processing speed in real-time video processing.

To calculate the distance between vehicles detected based on taillights, we estimated the vehicle width based on each taillight and computed the inter-vehicle distance. To effectively communicate the risk of a collision to the driver, a Head-up Display (HUD) was created, indicating danger levels using three levels of sound (Forward Collision Warning - FCW).

To further reduce the error rate in vehicle detection, we added tracking using Mean-Shift Tracking or Kalman Filter to track future video frames of vehicles. Additionally, for improved performance in forward vehicle detection, we plan to explore the use of a more accurate classifier continuously. Our future research will focus on exploring effective methods to enhance performance continuously.

