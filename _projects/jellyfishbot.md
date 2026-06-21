---
layout: page
title: Jellyfishbot
description: Industrial ASV for waste collection
img: assets/img/jellyfishbot.png
importance: 3
category: robots
related_publications: false
---

The [Jellyfishbot](https://www.iadys.com/jellyfishbot/) is a commercial autonomous surface vessel built by [IADYS](https://www.iadys.com/), a French company specialized in robotic solutions for water depollution. Unlike a research platform, the Jellyfishbot is designed for real-world operations in ports, marinas, and industrial sites, collecting floating waste and hydrocarbons either teleoperated or in autonomous mode.

We use it in the context of the [R3AMA ANR project](https://dream.georgiatech-metz.fr/research/robust-rl/), which focuses on robust reinforcement learning for floating waste collection.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/jellyfishbot/jfb-water.jpeg" title="Jellyfishbot in operation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/jellyfishbot/jfb-remote.jpeg" title="Remote control" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: collecting floating waste. Right: remote control interface, with autonomous cleaning mode.
</div>

---

## A more capable platform

Compared to the [Kingfisher](https://luisfelipewb.github.io/projects/kingfisher/) I used during my PhD, the Jellyfishbot is a more mature, production-grade platform. Three thrusters for omnidirectional motion in tight spaces, longer battery life, and a sensor and software stack already designed around real cleaning operations. It's built to be deployed and used by non-roboticists, which is a very different design approach from a research ASV.

---

## Adding a research layer on top

The trade-off with a commercial platform is that the internals are proprietary, so we don't get direct access to the robot's embedded computer. To work around this, we added a separate waterproof enclosure on top of the Jellyfishbot, hosting our own compute (NVIDIA Jetson Orin Nano). This gives us a ROS-based interface for prototyping new perception and control algorithms, while leaving the manufacturer's stack untouched.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/jellyfishbot/jfb-custombox.jpeg" title="Custom enclosure" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/jellyfishbot/jfb-testing.jpeg" title="Field testing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Custom waterproof enclosure designed and integrated to host the research compute and sensors.
</div>

---

## What's next

The next step is to port the RL-based control pipeline previously developed for the Kingfisher onto the Jellyfishbot, and extend it with available sensing modalities, in particular underwater sonar (for bathymetry and submerged obstacle awareness) and lidar-based obstacle avoidance for navigating safely around docks, boats, and other structures.
