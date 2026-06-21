---
layout: page
title: TurtleBot 2
description: Open source learning platform
img: assets/img/turtlebot2.jpeg
importance: 5
category: robots
related_publications: false
---

The TurtleBot 2 is a differential-drive mobile robot built on a Kobuki base, designed as an open platform for learning and experimenting with ROS. I spent a lot of time with it over the years, first as a student, then later as a teaching assistant for the [CS 7630 - Autonomous Robots](https://europe.gatech.edu/sites/default/files/2024-09/CS%207630%20course_syllabus.pdf) class.

---

## As a student

The class covered multiple layers of autonomy, from low-level control up to full mission-level behavior. The final project had the robot autonomously exploring the building floor while building a Wi-Fi signal strength map as it went, basically combining SLAM-based exploration with a secondary mapping task running on top.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-explore.jpg" title="Autonomous Exploration" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-wifi-mapping.jpg" title="Wifi mapping" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: autonomous exploration. Right: resulting Wi-Fi signal strength map.
</div>

I also used the TurtleBot 2 as a preliminary test platform for RL-based control, before moving on to outdoor tests with the [Kingfisher](https://luisfelipewb.github.io/projects/kingfisher/). The setup used an AprilTag as a perception-based target for the policy to track. It's a much friendlier place to debug a control policy: indoors, low stakes, and no risk of losing the robot in a lake.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-rl.jpg" title="Reinforcement Learning for the TurtleBot2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-rl-target.jpg" title="Target based on AprilTags" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: RL training setup. Right: AprilTag tracking target.
</div>

As a fun side project, in collaboration with other students, we also got a small fleet of TurtleBots to follow each other in a daisy-chain, each one tracking the robot ahead of it using a unique tag attached to its back. Simple to set up, but it made for a fun demo.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-rl-follow.jpg" title="Follow application" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    TurtleBots following each other in a daisy-chain.
</div>
---

## As a teaching assistant

Later on, as TA for the same class (Spring 2024 and 2025), I helped keep the lab's TurtleBot fleet running and supported students through their assignments. That meant a mix of hardware upkeep, software maintenance, and a fair amount of debugging help during office hours.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-fleet.jpg" title="TurtleBot fleet" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Maintaining TurtleBot 2 fleet.
</div>

During that time, I worked on upgrading the sensor suite on the lab's TurtleBots. In addition to the Kinect, we added an RPLidar for improved laser-based SLAM. That meant designing a 3D-printed mount for the new sensor, calibrating its extrinsics, and running integration tests to make sure everything played nicely together.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-laser-mount.jpg" title="3D-designed Laser Mount for the RPLidar" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    3D-printed RPLidar mount.
</div>

The improvement in map quality was remarkable. The lidar's wider field of view and longer range compared to the Kinect's depth sensor made a real difference, and it was enough to reliably run SLAM (via Nav2) across the entire second floor of the building — something that was a lot less consistent with the narrow field of view of the Kinect.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot2/tb2-slam.jpg" title="Lidar-based SLAM" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Lidar-based SLAM map of the Georgia Tech-Europe's second floor.
</div>

---
