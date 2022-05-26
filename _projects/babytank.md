---
layout: post
title: The modular mobile robot
description: The modular mobile robot - the ASD rehabilitation approach
---

|![schematic](https://bijanmehr.github.io/assets/babytank/schematic.png)|
|:-:|
|schematic|

## Intro
During my M.S. program, I got familiar with ASD (autism spectrum disorder) and the complications it can cause for children's development. Trouble in social interactions, motor function problems, repetitive movements, and intensive focus on details are some of ASD's symptoms. Many ASD-related tools have been developed in the Advanced Robotics and Intelligent Systems lab at the University of Tehran, where I attended as a researcher. Many M.S. and Ph.D. students develop apps, AI systems, and robots to help children in the process of ASD screening and ASD rehabilitation.

The idea of the mobile robot and what quirky things we can do with it has always fascinated my team, and we like making toys like devices for children with autism, so we choose hand-eye coordination training as the goal of our little project. The system consists of a small robot that can imitate the given path and a minimalistic GUI for human-robot interaction. The robot is battery-operated and lightweight, and of course, cost-effective.

## System design
Designing such a system always has different challenges; selecting proper hardware, suitable materials, cost, and child-friendly design make the decision-making process problematic. By embracing open-source hardware and software, we significantly decrease the cost and design time; also, this decision makes future developments more straightforward.

|![initial idea](https://bijanmehr.github.io/assets/babytank/initial_idea.png)|
|:-:|
|initial prototype|

### Mechanical design
The body structure and the mechanical part of the system are based on an open-source differential drive robot that could easily be 3D printed with PLA filaments that are inexpensive, durable, and safe for children. Still, to make the chassis more enduring, we make a few changes in the power transmission system, adding a small bronze coupling between each motor shaft and driving wheel and reinforcing the track's holders.

The Arduino ecosystem was selected for the circuits and electronics part of projects, particularly its user-friendly interface, to reduce development time. The Arduino UNO and its motor driver shield handle the motor control part, and NodeMCU ESP8266, connected with the serial interface to Arduino UNO responsible for the wifi connection and between human-robot interaction GUI and the robot.

|![improvent](https://bijanmehr.github.io/assets/babytank/improving_smars.png)|
|:-:|
|changes to improve the model|

### Software 
The software part of the system is divided into three sections, Matlab interface, ESP8266 firmware, and Arduino motor controller.
The Matlab interface provides a simple GUI for drawing a path and a simulation to show the approximate course the robot will travel. It also decomposes the drawn path to multiple checkpoints and sends them over wifi to ESP8266.
The ESP8266 receives checkpoints and saves them on an array. In the meantime, after receiving multiple checkpoints, the navigation module generates a path based on given checkpoints and sends it as the motor command to Arduino.
The Arduino motor controller is based on a PI controller that implements a closed-loop velocity control based on PWM data on feed-forward and encoder data on feedback to minimize draft from the desired path.

## Discussion
We managed to prototype three versions in this project and were inspired by many great designs, such as the donkey cars and Epuck robots. We built and failed many times as expected. Though our few tests on typically developed children show their interest in our system, we stopped further developments due to financial issues.

|![improvent](https://bijanmehr.github.io/assets/babytank/smars.png)|
|:-:|
|Modular robot prototype|


