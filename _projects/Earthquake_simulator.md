---
layout: post
title: Earthquake simulator
description: A P-wave earthquake simulator
---


## Intro
Earthquake is always capable of causing catastrophic events, especially in developing countries due to poor structured houses and infrastructures. Many researchers developed systems to minimize the probable harm caused by the earthquake, and early warning systems are one. These systems implement artificial intelligence and pattern recognition techniques to predict the propagation of earthquake waves and send proper notifications through GSM or other similar networks.


|![schematic](https://bijanmehr.github.io/assets/earthquack_simulator/schematic.png)|
|:-:|
|[Esposito, M., Palma, L., Belli, A., Sabbatini, L., & Pierleoni, P. (2022). Recent Advances in Internet of Things Solutions for Early Warning Systems: A Review. Sensors, 22(6), 2124.](https://doi.org/10.3390/s22062124)
|


In Advanced Robotics and Intelligent Systems Lab, a similar system was under development for earthquake early warning. They take advantage of the popularity of smartphones and their embedded sensors to collect anonymous data to predict if an earthquake is happening and in which direction it's going to propagate.
We like this idea and decided to contribute a little to this project by developing a p-wave earthquake simulator to act as a testbed for their experiments. Testing an active damping system in such conditions also looks interesting for us, and it's an excellent case to practice what we mainly learned in theory in our control courses.



## System design
The process of system designing starts with choosing a proper linear motion generator mechanism. We need to convert motor rotation to a controlled linear motion. Fortunately, this old problem comes with an old solution, the crank rocker mechanism as old as steam locomotives themselves.
We decided to use simple and cost-effective linear bearings with stainless steel shafts as a linear guide for the test platform to build a prototype. Two connecting rods with a fish-eye bearing and a small disk create the needed linear motion.

We provide a Matlab interface and an Arduino PID speed controller to control the system, so the users can quickly achieve their desirable motion profile.

|![cad_model](https://bijanmehr.github.io/assets/earthquack_simulator/solid.png)|![prototype](https://bijanmehr.github.io/assets/earthquack_simulator/prototype.png)|
|:-:|:-:|
|CAD model|Prototype|

## Test and data collection
The speed controller system takes motor PWM as feed-forward and the optical encoder data as feedback. We also design a data acquisition system that records vibration data for each time frame. The DAQ system sensor module is a Piezo Vibration Sensor with high voltage sensitivity and up to 40hz operational frequency that far exceeded our requirements. We manage to collect multiple sets of data for different accelerations values and motion profiles. By applying Matlab's system identification tools at our disposal, we come to a crude model of our system and its active damper model accordingly.

|![sytem_function](https://bijanmehr.github.io/assets/earthquack_simulator/tf.png)|
|:-:|
|active damping model|

## Discussion
This project started with the idea of making a testbed for our fellow researcher to do experiments on her early warning system cost-effectively in our lab. It was an incredible opportunity to polish our knowledge about control systems and the challenges of implementing them on a real-time physical system.
Unfortunately, due to budget problems, we abandoned our further developments and never succeeded in prototyping our active damping system, but in the end, the journey is the reward.

