---
layout: page
title: (2023) Thesis Project in Atlas Copco
description: I created an implementation of bolt detection and visual-inertial localization algorithm for tightening tool on SoC FPGA
img: assets/img/thesismasterproj.jpg
importance: 1
category: work
related_publications: true
---

During my master's studies, I completed my thesis project at Atlas Copco in Spring 2023 as part of the Master's Programme in Embedded Systems at KTH Royal Institute of Technology.

The thesis, titled [Implementation of Bolt Detection and Visual-Inertial Localization Algorithm for Tightening Tool on SoC FPGA](https://www.diva-portal.org/smash/record.jsf?pid=diva2%3A1811287), focused on edge computing for industrial bolt-tightening systems. The goal was to detect bolts and localize a tightening tool using visual-inertial data, with the complete computation pipeline running on a System-on-Chip FPGA.

I implemented bolt detection using a YOLOv3-Tiny-3L model accelerated by a Deep-learning Processor Unit (DPU) on the FPGA. In parallel, I worked with an Error-State Extended Kalman Filter (ESEKF) to fuse visual and inertial measurements for tool localization, with the algorithm accelerated through an RTL implementation in the FPGA fabric.

The final system demonstrated that bolt detection and visual-inertial localization could be executed directly on SoC FPGA hardware for a tightening-tool application. The evaluated pipeline achieved a position RMSE of 39.69 mm, a mean orientation error of 4.8 degrees, and an end-to-end processing time of 113.1 ms from bolt detection to localization.

This work was completed in cooperation with Atlas Copco and supervised by Dimitrios Stathis and Sofia Olsson, with Ahmed Hemani as examiner.

Keywords: bolt detection, visual-inertial localization, SoC FPGA, machine learning, YOLO, ESEKF, RTL, HLS, tightening tool.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/thesismasterproj.jpg" title="SoC FPGA" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The devices
</div>