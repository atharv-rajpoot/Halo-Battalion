# Holo Battalion – Multi-Robot Warehouse Automation System
[![ROS2](https://img.shields.io/badge/ROS2-Humble-22314E?style=for-the-badge&logo=ros&logoColor=white)](https://docs.ros.org/en/humble/)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Gazebo](https://img.shields.io/badge/Gazebo-Simulation-orange?style=for-the-badge)](https://gazebosim.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer_Vision-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org/)
[![ESP32](https://img.shields.io/badge/ESP32-Embedded_Systems-E7352C?style=for-the-badge&logo=espressif&logoColor=white)](https://www.espressif.com/)
[![MQTT](https://img.shields.io/badge/MQTT-Communication-660066?style=for-the-badge)](https://mqtt.org/)
[![C](https://img.shields.io/badge/Embedded_C-00599C?style=for-the-badge&logo=c&logoColor=white)](https://en.cppreference.com/w/c)
[![eYRC](https://img.shields.io/badge/eYRC-2025--26-800000?style=for-the-badge)](https://www.e-yantra.org/)
Developed as part of the **e-Yantra Robotics Competition (eYRC) 2025–26**, IIT Bombay.

## Overview

Holo Battalion is a ROS2-based multi-robot warehouse automation system developed to automate crate sorting and transportation inside a simulated warehouse environment.

The system consists of three holonomic mobile robots—**Glacio**, **Crystal**, and **Frostbite**—that collaboratively transport temperature-sensitive crates to their designated storage locations.

The project combines **robot perception, autonomous navigation, embedded systems, and robot control** to perform coordinated pick-and-place operations.

---

# Demo

▶️ Gazebo Simulation

https://www.youtube.com/watch?v=ffOcRU38SAU

▶️ Real Robot Demonstration

https://www.youtube.com/watch?v=DBNaWMGV1Pk

---

# Project Architecture

```
                 Overhead Camera
                        │
                        ▼
                 OpenCV Processing
                        │
           ArUco Detection + Homography
                        │
                        ▼
         Robot & Crate Pose Estimation
                        │
       ROS2 Topics (/bot_pose, /crate_pose)
                        │
                        ▼
               Task Allocation Logic
                        │
                        ▼
            PID Controller + Navigation
                        │
                        ▼
          Inverse Kinematics Calculation
                        │
                        ▼
              ROS2 MQTT Communication
                        │
                        ▼
                     ESP32
                        │
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
    MG995 Motors     MG90 Servo      Solenoid
                        │
                        ▼
                  Pick and Place
```

---

# System Workflow

1. An overhead camera captures the complete warehouse.

2. OpenCV detects ArUco markers placed on robots and crates.

3. Homography converts image coordinates into real-world coordinates.

4. Robot and crate poses are published using ROS2 topics.

5. A task allocation node assigns the nearest crate to each robot.

6. PID controllers generate smooth motion commands.

7. Inverse kinematics converts robot velocity into wheel velocities.

8. Commands are transmitted through MQTT to the ESP32.

9. ESP32 controls motors, servo motors, and solenoid to perform pick-and-place operations.

---

# Key Features

- Multi-robot warehouse automation
- ROS2-based communication
- Holonomic robot control
- Autonomous waypoint navigation
- PID-based motion control
- ArUco marker localization
- Homography-based coordinate transformation
- OpenCV-based color detection
- MQTT communication with ESP32
- Pick-and-place mechanism

---

# Technologies Used

## Robotics

- ROS2 Humble
- Gazebo
- URDF

## Programming

- Python
- Embedded C

## Computer Vision

- OpenCV
- ArUco Marker Detection
- Homography

## Embedded Systems

- ESP32
- MQTT
- PWM Control

## Hardware

- MG995 DC Motors
- MG90 Servo
- IR Sensor
- Solenoid
- Buck Converter

---

# Hardware Components

- ESP32
- 12V Li-Po Battery
- Buck Converter
- MG995 Motors
- MG90 Servo
- MOSFET Driver
- IR Sensor
- Solenoid

---

## Repository Structure

```text
Holo-Battalion/
│
├── hb_ws/
│   └── src/
│       └── eyrc-25-26-holo-battalion/
│
├── hb_ws2/
│   └── src/
│       └── eyrc-25-26-holo-battalion/
│
├── hardware_testing/
│   └── eyrc-25-26-holo-battalion/
│
├── esp32/
│
├── .gitignore
└── README.md
```

---

## Repository Organization

This repository follows the development workflow used during the **e-Yantra Robotics Competition (eYRC) 2025–26**.

The project was developed incrementally across multiple competition tasks, with each task maintained in a dedicated Git branch.

### Branches

| Branch | Description |
|---------|-------------|
| **main** | Initial boilerplate repository provided for project development. |
| **task1** | Initial ROS2 workspace (`hb_ws`) and Task 1 implementation. |
| **task2a** | Task 2A implementation in simulation. |
| **task4a** | Task 4A implementation in simulation. |
| **task4b** | Task 4B implementation in simulation. |
| **task5a** | Task 5A implementation in simulation. |
| **task5b** | Task 5B implementation in simulation. |
| **task6a** | Final simulation implementation. |
| **real_world_task** | Real-world implementation using `hb_ws2`, hardware integration, and ESP32 firmware. |

---

## Workspace Organization

### hb_ws

Contains the ROS2 simulation workspace developed during the competition tasks.

### hb_ws2

Contains the ROS2 workspace used for real-world robot deployment and hardware testing.

### hardware_testing

Contains hardware-specific development and testing files.

### esp32

Contains firmware for ESP32-based robot control.

This firmware is used only in the real-world implementation and was developed during the later stages of the competition (Task 4 onwards).

---

# Results

- Successfully completed autonomous crate sorting in simulation.

- Demonstrated coordinated operation of three holonomic robots.

- Successfully integrated perception, navigation, control, and embedded hardware.

- Achieved Level 2 in the e-Yantra Robotics Competition.

- Recognized as the Top Girls Team.

---

# Technical Challenges

- Accurate robot localization using overhead camera

- Homography calibration

- PID tuning for stable navigation

- Multi-robot coordination

- Hardware and ROS2 communication through MQTT

---

# Future Improvements

- Dynamic obstacle avoidance

- Advanced path planning

- SLAM integration

- Real-time warehouse deployment

- Autonomous charging station

---

# Team

Team eYRC#3975

- Atharv Rajpoot
- Vignesh Gajula

---

Developed for the e-Yantra Robotics Competition (eYRC) 2025–26, IIT Bombay.
