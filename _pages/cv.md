---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* Ph.D. in Hardware Accelerator for Neuromorphic Computing, KTH Royal Institute of Technology, 2024–present
* M.S. in Embedded Systems, KTH Royal Institute of Technology, 2021–2023
* S.T. in Engineering Physics, Universitas Gadjah Mada, 2013–2017

Work experience
======
* Doctoral Researcher, Kungliga Tekniska högskolan (KTH), Apr 2024 – present
  * Developing FPGA-based accelerators for neuromorphic computing across the IoT–Edge–Cloud continuum.
* Software Engineer, Atlas Copco, Aug 2023 – Mar 2024
  * Upgraded SD card testing, built automatic testing board, and explored DC motor temperature estimation for MicroTorque tools.
* R&D Engineer, Atlas Copco, Aug 2022 – Dec 2022
  * Analyzed ultrasound tightening systems, designed amplifier circuits, supported PCB manufacture, and developed Processor-In-Loop software.
* Summer Worker (R&D Engineer), Atlas Copco, Jun 2022 – Aug 2022
  * Created electronics platform and universal Processor-In-Loop testing board using STM32 microcontrollers.
* Electronics Engineer, The Agency for the Assessment and Application of Technology (BPPT) Indonesia, Jan 2018 – Aug 2021
  * Designed embedded devices and communication systems for tsunami warning, AIS, and visible light communication projects.
* Teaching & Laboratory Assistant, Universitas Gadjah Mada, Sep 2014 – Dec 2016
  * Supported courses in AI, sensor technology, and electronics laboratories.

Skills
======
* C programming
* RTL design
* Embedded Linux
* FPGA development (VHDL, HLS)
* Microcontroller programming (STM32)
* Analog electronics

Languages
======
* English (Full Professional)
* Bahasa Indonesia (Native)
* Swedish (Limited Working)

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
