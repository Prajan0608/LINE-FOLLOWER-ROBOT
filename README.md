# Line Follower Robot using Arduino (PID Control)

## Minor Project – Embedded Systems & Robotics

**Student Name:** PRAJAN VS  
**College:** Kumaraguru College of Technology  
**Degree:** B.E  
**Project Type:** Mini Project  
**Project Title:** Line Follower Robot  
**Platform:** Arduino Mini Pro  
**Motor Driver:** TB6612FNG  

---

##  Project Overview

A **Line Follower Robot (LFR)** is an autonomous robotic system designed to follow a predefined path using infrared (IR) sensors.  
This project implements a **PID (Proportional–Integral–Derivative) control algorithm** to achieve accurate line tracking, smooth motion, and stable performance at higher speeds.

The robot continuously senses surface reflectivity, calculates positional error, and dynamically adjusts motor speeds to stay aligned with the track.

---

## Objectives

- Design and implement an autonomous line-following robot  
- Apply PID control for precise motion correction  
- Perform automatic sensor calibration for different surfaces  
- Reduce oscillations and improve tracking accuracy  
- Gain hands-on experience with Arduino and motor drivers  

---

## Hardware Components

| Component | Specification | Quantity |
|---------|--------------|----------|
| DC Gear Motor | N20, 600 RPM, 100:1 | 2 |
| Wheels | 4 cm diameter | 2 |
| Chassis | 3D Printed ABS | 1 |
| Battery | 7.6V Li-ion | 2 Cells |
| Motor Driver | TB6612FNG | 1 |
| Microcontroller | Arduino Mini Pro | 1 |
| IR Sensor Array | 5-Channel | 1 |
| Push Buttons | Calibration & Start | 2 |
| Jumper Wires | Connecting wires | As required |

---

## Circuit Connections

### IR Sensor Array
- Sensor outputs → Arduino **A1 – A5**
- VCC → **5V**
- GND → **GND**

### TB6612FNG Motor Driver
- **VCC** → 5V  
- **VM** → Motor supply (7–12V)  
- **GND** → Common ground with Arduino  
- **STBY** → 5V (Enable motor driver)

### Motor Control Pins
| Arduino Pins | Function |
|-------------|----------|
| AIN1, AIN2, PWMA | Left Motor |
| BIN1, BIN2, PWMB | Right Motor |

---

## Working Principle

### 1️ Sensor Calibration
- Activated using **Button 1 (Pin 11)**
- Robot rotates in place
- Stores:
  - Minimum values → white surface
  - Maximum values → black line
- Threshold values calculated automatically

### 2️ Line Detection
- IR sensor readings mapped to **0–1000**
- Converted into digital states using threshold
- Determines whether the robot is on the line

### 3️ Error Calculation
- Each sensor has an assigned weight
- Calculates lateral deviation from the line center

### 4️ PID Control
- **Proportional (P):** Corrects present error  
- **Integral (I):** Eliminates steady-state error  
- **Derivative (D):** Reduces oscillations  

### 5️ Differential Drive Control
- PWM values adjusted for left and right motors
- Maintains smooth and stable trajectory

---

##  PID Parameters

```cpp
float Kp = 0.12;
float Ki = 0.0;
float Kd = 0.1;
