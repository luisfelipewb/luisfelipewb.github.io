---
layout: page
title: TurtleBot 3
description: Personal mobile robot platform
img: assets/img/turtlebot3.jpeg
importance: 4
category: robots
related_publications: false
---

The TurtleBot 3 is a compact, differential-drive mobile robot built around a Raspberry Pi and the OpenCR control board. I bought one back in 2018 when I first started getting into robotics, and it's been my go-to personal platform for tinkering ever since.

A bit like adult LEGO, it gives you something to explore at every level: mechanical assembly, firmware on the OpenCR, and the full software stack running on top of ROS. The time-lapse below shows the initial assembly.

<div class="row mt-3 justify-content-center">
    <div class="col-sm-12 col-lg-10 mt-3 mt-md-0">
        {% include video.liquid path="https://www.youtube.com/embed/cRYp7vrn46c" class="w-100 rounded z-depth-1" height="440" %}
    </div>
</div>

---

## Tinkering and customization

Beyond running the classical navigation algorithms available in ROS (mapping, localization, path planning, all the usual suspects), the TurtleBot 3 is easy to extend. Over the years I added an ultrasonic range sensor and a Raspberry Pi camera to play with additional sensing modalities.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot3/tb3-customization.jpg" title="Customization" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot3/tb3-new-sensors.jpg" title="New sensors" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: customized chassis. Right: added ultrasonic sensor and Raspberry Pi camera.
</div>

---

## Testing the SparkFun OTOS

The latest addition has been the [SparkFun OTOS](https://www.sparkfun.com/sparkfun-optical-tracking-odometry-sensor-paa5160e1-qwiic.html) (Optical Tracking Odometry Sensor), which combines a laser-based optical flow sensor with an IMU and runs sensor fusion onboard to output a pose estimate directly. It's a neat little board, and a low-effort way to add an extra odometry source to a small robot.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot3/tb3-design.jpg" title="OTOS mount design" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot3/tb3-real.jpg" title="OTOS mounted on the robot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: 3D-printed OTOS mount. Right: sensor installed on the robot.
</div>

With this extra sensor on board, the TurtleBot 3 becomes a handy testbed for comparing different odometry sources (wheel encoders, IMU integration, optical tracking) and evaluating sensor fusion strategies. A useful little platform for quickly trying out sensors and algorithms before committing to deploying them on a larger, more expensive robot.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/turtlebot3/tb3-state-estimation.jpeg" title="State estimation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    State estimation comparison across different odometry sources.
</div>
