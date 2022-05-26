---
layout: post
title: Intelligent Toy Car
description: An Intelligent Toy Car for Autism Screening
---

## Intro
Early screening, which can lead to early diagnosis and intervention of children with autism (ASD), can significantly improve the life quality of children with autism. The observational process of ASD diagnosis and the lack of experts make the technology-based ASD screening methods more necessary. Early ASD screening based on behaviors is one of the most reliable methods that could be done by analyzing children's playing patterns.

The home-based IoT devices such as the intelligent toy car were designed to perform screening in children's natural settings at a relatively low-cost thanks to dirt cheap IoT chips like ESP8266, ESP32, and MEMS sensors. These sensorized toys are valuable tools for ASD screening and were proven effective. They collect behavioral data from playing patterns and analyze them using signal processing techniques or machine learning approaches.

This project redesigned and improved the intelligent toy car functionality by adding shaft encoders to detect attention to detail and interest in rotating objects in children with ASD. Also, we improved our classification system by implementing two modalities to detect different ASD symptoms that enhanced our previous accuracy by more than 10%

|![car](https://bijanmehr.github.io/assets/intelligent_car/car_axis.png)|
|:-:|
|The intelligent toy car 2.0|

## System design
The intelligent toy car is designed to capture the signs of two major symptoms in children with ASD, obsessive attention to detail and repetitive behaviors. In our first design, a Wii remote, which includes an accelerometer, was placed in the car. Our new design has an inexpensive IoT board ESP8266 NodeMCU to read sensor data and send them wirelessly through Wi-Fi via UDP protocol to ensure maximum data collection rate. Also, the cheap MEMS accelerometer ADXL345 is placed inside the car, and two magnetic shaft encoders are installed on each car's axle. The whole system runs on a battery, and all electronic parts are embedded inside the car deliberately to avoid any distraction.

The intelligent toy car firmware is based on the Arduino ecosystem to make future R&D more effortless. Also, a ROS (Robotic Operating System) package is developed for interfacing with the system, making integrating the intelligent toy car in other systems more straightforward.

|![schematic](https://bijanmehr.github.io/assets/intelligent_car/car_diagram.png)|
|:-:|
|System diagram|

## Tests and results
The data collection process took place in an ASD center under the supervision of a psychiatrist and an ASD expert. The collected data consists of timestamps, X, Y, and Z-axis accelerations, and the number of rotations of each wheel shaft.
We applied two different strategies to the acquired dataset. First, based on frequency domain analysis, the data was divided into four chunks, NOT PLAYING, ONLY PLAYING WITH WHEELS, MOVING CAR ON THE GROUND, and MOVE THE CAR IN THE AIR, then used the ratio of each chunk for classification. The other method was based on an SVM classifier. We extracted multiple features based on our observations and the experts' opinions. Then by utilizing feature reduction methods like backward elimination, we chose the most compelling features for SVM with a linear kernel. The classifier showed promising results, and by combining both modalities, the system handled classification with the accuracy of 85%


|                      **Classifier**                     | **Accuracy** | **Sensitivity** | **Specificity** | **precision** |
|:-------------------------------------------------------:|:------------:|:---------------:|:---------------:|:-------------:|
|                    Baseline features                    |     71.11    |      67.14      |      73.00      |     80.00     |
|              Baseline and encoder features              |     78.61    |      75.00      |      68.00      |     87.50     |
|          Baseline and new acceleration feature          |     75.83    |      65.48      |      77.00      |     64.00     |
| Baseline, encoder features and new acceleration feature |   **85.56**  |      81.67      |      81.00      |     87.67     |


## Discussion
The intelligent toy car was the most time-intensive study for us. We developed IoT systems, built toy cars (it was way harder than you can imagine!), dealt with real-world data collection difficulties, analyzed noisy behavioral data, got in touch with families with ASD children, and talked to many ASD experts. The experience was unique for every member of our team and the most challenging task for me as a team leader.
This study is under review for publishing in a related journal, and we are looking forward to making this system open source after that
