---
title: "ProxiCharge"
description: "Proximity-Based Charger Safety System that automatically powers off unattended chargers."
date: "2024-08-01"
timeframe: "Nov 2023 - Jul 2024"
draft: false
tags:
  - electronics
  - safety
  - sensing
  - hardware
params:
  project_url: "https://github.com/ShayonKhaled/ProxiCharge"
---

## Overview

ProxiCharge is an automated charger safety system that prevents unattended charging of lithium batteries by monitoring room occupancy and shutting off chargers when no motion is detected.

## How it works

- Initial setup: press the power switch on the motion detector to enable chargers.
- Motion is monitored by three PIR sensors. While motion is detected the system keeps chargers enabled and shows a green status.
- If the room is vacant a countdown begins (configurable; default ~5 minutes). Visual and audio alerts escalate before shutdown.
- If vacancy persists past the timeout, the motion detector sends an ESPNOW "OFF" command to the remote power-supply controller which cuts power to the chargers.
- Returning within the timeout resets the countdown; otherwise the user must re-enable the system.

## Features

- Motion detection (3x PIR sensors)
- Remote control of charger power via ESPNOW
- Visual (RGB LED ring) and audio (buzzer) alerts during countdown
- OTA firmware updates for the motion detector

## Technical Details

### Components
- Motion detector: 3 × PIR sensors, ESP32-S2 (Lolin S2 Mini), RGB LED ring, buzzer, power switch.
- Remote power controller: ESP32-S2 controlling a relay and a 24 V SMPS to switch charger power.

### Design
- Enclosure and mounts modeled in Autodesk Fusion 360 and 3D-printed for the PIR sensor assembly.

### Programming
- Firmware written for the Arduino/PlatformIO environment targeting ESP32-S2. Uses `esp_now` for low-latency local wireless commands and simple heartbeat/timeout messaging.

## Final results

The prototype demonstrates reliable occupancy-based shutdown of battery chargers and includes photos, CAD renders and circuit diagrams in the repository.

Gallery (selected):

- ![Motion Sensor](/img/proxicharge/e21efacf-cc81-4956-8fcd-aa7f318b4264.jpg)
- ![Enclosure render](/img/proxicharge/5014bdc3-5336-44a1-b25b-96b3493d1a9b.png)
- ![Battery Charger Power Supply](/img/proxicharge/ba82bff6-7d33-478f-9fa2-8477b36bb225.jpg)

Demo video: [/img/proxicharge/e3da7332-e028-45b5-88b8-72c04bd070bb.mp4](/img/proxicharge/e3da7332-e028-45b5-88b8-72c04bd070bb.mp4)

## Technical specifications

- Microcontroller: ESP32-S2 (Lolin S2 Mini)
- Design: Autodesk Fusion 360 (CAD)
- Programming: Arduino framework using PlatformIO in VS Code

## Links

- Repository: [https://github.com/ShayonKhaled/ProxiCharge](https://github.com/ShayonKhaled/ProxiCharge)

If you'd like, I can also copy key images into this site's `static/img` folder and embed local copies for faster loading.
