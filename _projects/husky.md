---
layout: page
title: Husky
description: Rugged ground robot for research
img: assets/img/husky.jpeg
importance: 2
category: robots
related_publications: false
---

The [Clearpath Husky](https://clearpathrobotics.com/husky-unmanned-ground-vehicle-robot/) is a veteran platform in the [DREAM Lab](https://dream.georgiatech-metz.fr/), with multiple research projects already behind it. Rugged, skid-steered, and built for outdoors, it has been used across a wide range of field experiments over the years.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-intro-outside.jpeg" title="Husky outdoors" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-intro-mud.jpeg" title="Husky in muddy conditions" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The Husky in its natural habitat: outdoor field tests, sometimes a bit muddy.
</div>

---

## Hardware maintenance

I started working with the Husky mostly on the support side, keeping it healthy as a research platform. For example, the drivetrain was replaced in early 2026 after years of accumulated field use.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-maintain.jpeg" title="Drivetrain maintenance" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Drivetrain replacement.
</div>

---

## Field test support

A lot of my involvement has been around field tests: helping others prepare experiments, debugging issues during deployments, and processing the recorded data. On the easier days, I sometimes have a chance to fly a drone and capture aerial footage of the experiments.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-drone-footage.jpeg" title="Drone footage" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-pas-du-loup.jpeg" title="Field test at Pas du Loup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: aerial footage captured during a field experiment. Right: processing field test data.
</div>

---

## Sensor integration

Over time, the Husky has evolved with different exteroceptive sensors for better perception. Adding cameras and lidars, designing the necessary mounts, and running extrinsic calibration so the new data lines up with the rest of the stack has been a recurring task.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-sensor-integration.jpg" title="Sensor integration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Custom sensor integration for field experiments.
</div>

---

## NINSAR: perception for precision agriculture

The project I am directly involved in is [NINSAR](https://eng-pepr-agroeconum.custom.hub.inrae.fr/funded-projects/agricultural-equipment/targeted-projects/ninsar) (New ItiNerarieS for Agroecology using cooperative Robots), a French national project exploring how fleets of cooperative robots can support agroecological practices. My contribution focuses on the perception side: building a pipeline that lets a ground robot reliably understand the structure of a crop field for precision agriculture tasks.

In the first round of experiments, I evaluated a ZED 2i stereo camera combined with [OctoMap](https://octomap.github.io/) for 3D occupancy mapping of the surrounding environment.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-octomap.jpeg" title="OctoMap reconstruction" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    3D occupancy map generated from ZED 2i stereo data.
</div>

The broader goal is to develop a perception pipeline that scales: training on synthetic data generated in photorealistic simulation (Isaac Sim), and then validating it on real field recordings collected with the Husky. This is still an ongoing effort, but the images below show some of the preliminary results.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-simulation.jpg" title="Husky in Isaac Sim" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/husky/husky-ninsar.jpg" title="NINSAR field tests" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: photorealistic simulation in Isaac Sim. Right: real field tests for the NINSAR project.
</div>
