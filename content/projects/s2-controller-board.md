---
title: "Central Control Board for Teleoperated Mobile Robot"
description: "Custom PCB controller for our university's competitive robotics team"
date: "2024-06-15"
timeframe: "May 2024 - Jun 2024"
draft: false
tags:
  - pcb-design
  - robotics
  - embedded-systems
  - esp32
  - circuit-design
  - kuas
params:
  project_url: "https://github.com/ShayonKhaled/S2-Controller-Board"
---

## Overview

I designed the S2 Controller Board, a custom PCB that consolidates control logic, sensor communication, and power distribution for our university's Competitive Robotics team. It replaced a fragile, disorganized perfboard setup with a single professional-grade unit capable of scaling with future subsystems.

## Problem

Our existing control system was unreliable and difficult to debug. Multiple interconnected breadboards with fragile wire connections broke frequently and couldn't accommodate new sensors. We needed a unified, production-quality solution that could handle competitive robotics demands.

## What I built

- Unified PCB replacing multiple breadboards and perfboards
- ESP32 microcontroller with native Wi-Fi and Bluetooth
- Onboard MPU-6050 accelerometer for positional feedback
- CAN bus communication for motor and auxiliary controller coordination
- Four I2C and four SPI ports for flexible sensor connectivity
- OLED display for real-time system diagnostics
- Status LEDs and buzzer for visual and audio feedback
- Exposed ESP32 pins for future modular expansion

## Tech stack

- Microcontroller: ESP32 with Wi-Fi and Bluetooth
- PCB design: EasyEDA
- Communication: CAN bus, I2C, SPI, UART
- Sensors: MPU-6050 accelerometer
- Power: Barrel jack and USB input with 5V regulation
- Diagnostics: OLED display, status LEDs, buzzer
- Layout: Professional PCB design with proper power distribution

## Results

Successfully replaced an unreliable setup with a modular PCB that improved system reliability significantly and reduced debugging time. The board now operates flawlessly in the S2 chassis and scales easily for future subsystems.

## Link

GitHub repository: [https://github.com/ShayonKhaled/S2-Controller-Board](https://github.com/ShayonKhaled/S2-Controller-Board)
