---
layout: page
title: Jaco 2
description: Kinova Jaco 2 robotic arm
img: assets/img/jaco2.jpeg
importance: 6
category: robots
related_publications: false
---

This was the robot I spent the least hands-on time with (~6 months), but it was part of an interesting project: [GANResilRob](https://www.entreprises.gouv.fr/espace-presse/la-france-et-lallemagne-renforcent-leur-cooperation-dans-le-domaine-de-lia). My role was to design the integration layer connecting the perception and control modules being developed by other partners — basically the glue that lets everything talk to each other.

---

## Getting hands-on with the real arm

Early on, I had the chance to set up the physical robot for tests and get familiar with the stack, mostly built around MoveIt. It was a nice opportunity to see how motion planning, collision checking, and trajectory execution come together in practice for a 7-DoF manipulator.

<div class="row" mt-3 justify-content-center>
    <div class="col-sm col-lg-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/jaco/jaco.jpeg" title="Sail configuration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Kinova Jaco 2 arm.
</div>

---

## Moving to simulation

For most of the project, I worked with a Franka Emika Panda arm in Isaac Sim. The photorealistic rendering was a big draw, especially for any perception components that needed to be trained or tested on visually realistic data.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/jaco/panda-sim.jpg" title="Sail configuration" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/robots/jaco/panda-perc.jpg" title="3D-printed souvenir" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Ilustrating the MoveIt plugin in RViz to control the Panda arm and its simulation with synthetic perception dada in Isaac Sim.
</div>

Working with the Panda was also a good opportunity to dig into some of the standard motion planners (e.g. OMPL-based planners available through MoveIt), compare Cartesian-space versus joint-space control, and get a feel for the challenges of planning in a 7-DoF arm. The extra degree of freedom compared to a more common 6-DoF arm means there's a whole null-space of joint configurations that all reach the same end-effector pose, great for avoiding obstacles and joint limits, but it adds real complexity to the search space.

---

## Some fun

As a bonus, I got the arm to serve me water. With a healthy dose of supervision and zero autonomy involved, but still a fun way to wrap up the project on a lighter note.

<div class="row mt-3 justify-content-center">
    <div class="col-sm-12 col-lg-10 mt-3 mt-md-0">
        {% include video.liquid path="https://www.youtube.com/embed/_cb439TtcmE" class="w-100 rounded z-depth-1" height="440" %}
    </div>
</div>
