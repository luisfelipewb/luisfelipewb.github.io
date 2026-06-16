---
layout: page
title: Kingfisher
description: Research ASV platform
img: assets/img/kingfisher.png
importance: 1
category: robots
related_publications: false
---

I spent a big part of my PhD working on this robot: a surface vessel that already has served well previous researchers in the DREAM Lab. The application was deceptively simple: get it to autonomously find and collect floating trash on the water. The reality was a lot of work integrating perception, reinforcement learning-based control, hardware, and lots of field tests.

<div class="row mt-3 justify-content-center">
    <div class="col-sm-12 col-lg-10 mt-3 mt-md-0">
        {% include video.liquid path="https://www.youtube.com/embed/QBxn9bTrWjM" class="w-100 rounded z-depth-1" height="440" %}
    </div>
</div>

The clip above shows the final result: an RL policy, trained entirely in simulation, controlling the real robot to capture floating waste. The policy was deployed zero-shot from Isaac Sim. No fine-tuning on real data.

Getting there meant working on pretty much every layer of the stack, with frequent field tests to evaluate progress and prioritize improvement efforts.

---

## The robot

[Clearpath Kingfisher](https://www.clearpathrobotics.com/wp-content/uploads/2013/08/Kingfisher_USV_Brochure_2015.pdf), ~35 kg, twin thrusters, research platform. We tested it at Lac Symphonie in Metz, which became an office extension for most of my PhD.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/platform-asv.png" title="Kingfisher overview" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/test_location.jpg" title="Field test site" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: the Kingfisher in its working configuration. Right: Lac Symphonie in Metz, where most of the field tests happened.
</div>

---

## Perception

Detecting floating waste sounds straightforward until you put a camera on a moving boat. Reflections, glare, ripples, changing weather. The same plastic bottle can look completely different under different illumination conditions and off-the-shelf perception models struggled.

To get around this, I worked on a polarimetric camera setup that exploits the polarization properties of water reflections to separate real bottles from the background reflections. That work became the **PoTATO** dataset [ECCV 2024 Workshop](https://link.springer.com/chapter/10.1007/978-3-031-91569-7_13) and later a fusion study published at [VCIP 2025](https://ieeexplore.ieee.org/document/11396891).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/perception_challenges.png" title="Perception challenges" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/rgb-pol.jpg" title="RGB vs Polarimetric" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Perception challenges due to surface reflection (left) and RGB vs Polarimetric image comparison.
</div>

The dataset is publicly available: see the [PoTATO github](https://github.com/luisfelipewb/PoTATO) repository for more details.

---

## Reinforcement learning-based control

The control policy was trained entirely in [Isaac Lab](https://developer.nvidia.com/isaac/sim), then deployed zero-shot on the real robot. Getting that to work consistently despite complex dynamics and external disturbances was the core contribution of my PhD.

<div class="row mt-3 justify-content-center">
    <div class="col-sm-12 col-lg-10 mt-3 mt-md-0">
        {% include video.liquid path="https://www.youtube.com/embed/-arrILHbwBM" class="w-100 rounded z-depth-1" height="440" %}
    </div>
</div>

The work led to two papers worth pointing at:

- [IROS 2024](https://ieeexplore.ieee.org/document/10802067): Explains the methodology and sim-to-real experiments.
- [W-FR 2025](https://arxiv.org/abs/2505.10033): Field tests for robustness evaluation and MPC comparison.

---

## Integration

Combining the perception and control learned models was the last part of my PhD. Here the challenge was putting it all together in a way that it worked reliably.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/integration1.jpg" title="Predefined area for testing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/integration2.jpg" title="Aerial view" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Predefined area for testing (left) aerial view and camera view (right).
</div>

The final results are briefly shown in the following video

<div class="row mt-3 justify-content-center">
    <div class="col-sm-12 col-lg-10 mt-3 mt-md-0">
        {% include video.liquid path="https://www.youtube.com/embed/qOIKrZn-bK8" class="w-100 rounded z-depth-1" height="440" %}
    </div>
</div>

A detailed explanation of the methodology and field tests is available in a [T-FR publication](https://ieeexplore.ieee.org/document/11505922).

---

## Hardware

A research robot rarely arrives ready for the work you want to do. Making all the modifications needed was time consuming and didn't lead directly to publications, but it was quite rewarding. Some of the interesting things I learned during the project:

- **Reverse-engineering the proprietary MCU.** I spent a fair amount of time failing to get the control policy to work until I decided to plug an oscilloscope in the motor controller output to figure out PPM signals sent by the proprietary control board as a response to the ROS-level input commands. Reverse engineering and modeling the rate-limit implemented in the proprietary controller was a key factor to improve simulation fidelity and get things right.
- **Integrating RTK GPS** Sounds straight-forward, but there is an interestingly high number of things that can go wrong.
- **Designing 3D-printed mounts** for new sensors, attachment points, camera mount, antenna supports, etc..
- **Network configuration** for reliable telemetry between the robot, the base station, and a laptop running training/evaluation.
- **Sensor calibration** for usable perception data.
- **Lots of cabling, waterproofing, and small electrical fixes** that aren't glamorous but are the difference between a working test day and going home with a wet, dead robot.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/hardware-integration.jpg" title="Hardware Integration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Image compiling some of the hardware integration tasks, from 3D printed parts, sensor calibration, firmware reverse engineering and component organization in tight spaces.
</div>

Field robotics is quite humbling. Your battery will always die sooner than your estimate and of course many other things can (and will) go wrong.

<div class="row justify-content-center">
    <div class="col-sm-10 col-md-8 col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/field-challenges.jpg" title="Field Issues" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A small selection of field-related issues: Broken propellers, failed 3D prints, getting the propeller tangled in fishing line, occasional fried cable, and network failures.
</div>

Over time, the field tests became way smoother and easier to execute. Towards the end I could even fly the drone to record the experiments (fist video). It is true the Kingfisher was already quite autonomous at this point...

---

## What's next...

PhD is done. The Kingfisher has served me well but it isn't retired. I am now preparing it for new research adventures on energy-efficient sail navigation.

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/sail1.jpeg" title="Sail configuration" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/sail2.jpeg" title="3D-printed souvenir" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/kingfisher/sail3.jpeg" title="3D-printed souvenir" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Sequence of images showing the latest modifications in the Kingfisher. Reduced payload, simplified components, and sail installation.
</div>

All these field deployments taught me lessons that simulation alone never could, about test protocols, controller behavior under real disturbances, sensor limitations, and calibration. Many failure modes only showed up once everything was running together on the real robot, and it took repeated iterations to trace the root causes and fix them properly. If there's one takeaway, it's that progress in autonomous systems depends as much on careful integration as on algorithmic novelty.
