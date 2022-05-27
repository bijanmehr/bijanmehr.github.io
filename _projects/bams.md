---
layout: post
title: BAMS - Interactive Social Robot Platform 
description: Interactive Social Robot Platform for ASD rehabilitation
---


## Intro

In one of our previous projects, we developed a mobile robot for hand-eye coordination training to help children with autism retrain their fine motor skills. During our tests and after consulting with experts, we found out that interactive social robots have a considerable advantage in interacting with children with ASD (autism spectrum disorder). There are many prominent social robot platforms in the market, but the main problem with utilizing them in ASD rehabilitation is their cost. So we decided to develop a simple ROS (robotic operating system) integrated social robot platform for studying the social behaviors of children with ASD and ASD-related rehabilitation.

## System design

Designing a complex system like social robots is a tedious task that requires multiple generations of prototyping. So we decided to proceed with this complicated task with an agile development mindset. Design and build different parts of the project modular, test each individually, and then integrate all modules.

|![BAMS1](https://bijanmehr.github.io/assets/bams/bams1.png)|
|:-:|
|BAMS 1.0 facial expression module|

The system design procedure was divided into three subsystems for better task management. The movement module handles robot motion, path planning, collision avoidance, and obstacle detection. The interaction module is responsible for facial expression, audio feedback, and hand gestures. Lastly, the cognitive module required for the intelligent behavior of the robot, face recognition, voice localization, and emotion recognition.

The importance of implementing the software part of the system based on the ROS (Robotic Operating System) ecosystem was self-explanatory from the beginning, so every module was designed and developed based on this manifest to help future integrations. The interaction module was the first step in this long journey because it could be the most cost-intensive and customizable part of the system. Other than that, the ASD experts should confirm its effectiveness in a child robot interaction scenario. So we chose to prototype a simple facial expression module and took some feedback from experts. We have called it BAMS (honestly, I don't remember why! :)) After some consideration, we figured out that our initial facial expression unit was far from acceptable, so we had to switch to an LCD-based system.

|![BAMS2](https://bijanmehr.github.io/assets/bams/bams2.png)|
|:-:|
|BAMS 2.0|

In the second prototype, BAMS 2.0, we prototyped and integrated a few parts for more complicated tests. A cheap character LCD in the middle of an IR sensor array on a small servo motor that could rotate 180 degrees and two microphones for each robot's side. Facial expressions were presented as multiple bitmapped emojis, and the IR sensor array tracked hand movement around the robot. Also, a basic sound localization system was provided for reaction to the voice commands. All the above functionalities were handled by an Arduino Mega 2560 that was selected to reduce cost and developing time.

|![BAMS3_motor](https://bijanmehr.github.io/assets/bams/bams3_motor.png)|
|:-:|
|BAMS 3.0 movement module|

Our previous systems did not have any cognitive module, and their interactions were almost hardcoded on them, but the results and experts' opinions were promising. Based on what we learned from past experiences, BAMS 3.0 was born that had every three required modules.
The interaction module is based on an Android tablet that presents the robot's face. A fisheye lens camera was provided for a wide-angle view. The robot's brain is an Nvidia jetson nano that controls all Dynamixel motors with a USB adapter. The robot is equipped with a local wifi router for ease of communication. The movement module is based on a triangular Omni wheel vectoring mechanism for the base motion; also, the robot's hands have one degree of freedom each. Other than that, the head of the robot has 2 degrees of movement provided by a pan-tilt mechanism.

|![BAMS3_skematic](https://bijanmehr.github.io/assets/bams/bams3_schematic.png)|
|:-:|
|BAMS 3.0|

## Discussion
The BAMS series was a unique experience for my team due to its long and progressive timeline requiring multiple developments and redesign stages. The BAMS 3 is now operational in Advanced Robotics and Intelligent Systems Lab at the University of Tehran, and it's going to be tested in rehabilitation scenarios for children with ASD.
Though the project's overall cost gradually increased over time, it's still reasonably more affordable than available commercial robots.
We hope to open-source all CAD files and source codes soon after publishing our paper.

|![BAMS3](https://bijanmehr.github.io/assets/bams/bams3.png)|
|:-:|
|BAMS 3.0 interactions|