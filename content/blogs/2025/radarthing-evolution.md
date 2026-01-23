---
title: "RadarThing: From Simple Radar to Full Flight Platform"
description: "How a bandwidth-efficient radar evolved into a complete flight tracking platform with logging, stats, ATC commands, and community features."
date: "2026-01-23"
url: "/radarthing-evolution/"
draft: false
categories:
  - Development
  - Flight Simulation
tags:
  - GeoFS
  - RadarThing
  - Web Development
---

Back in November, I wrote about [GeoFS-Radar](/flightradar24-for-geofs/) and how it solved the bandwidth and accuracy issues with the official GeoFS map. What started as a simple radar replacement has since evolved into something much more comprehensive. The project has been renamed to RadarThing and has grown into a full flight tracking platform.

## Flight Logging

The most significant addition is automatic flight logging. Every flight you take is now recorded and saved to your account. The system tracks your route coordinates throughout the flight, which means you can view a complete replay of your flight path after landing.

The logging system is smart about WiFi disconnections too. If you briefly lose connection mid-flight, the system uses a grace period before finalizing your flight. If you reconnect within three minutes, your flight continues as a single session rather than being split into two separate flights. This was crucial because nothing is more frustrating than seeing two flights logged when you only flew once.

## User Statistics

With flight logging came the ability to track statistics. Your dashboard now shows:

- Total flights completed
- Total flight time
- Total distance flown in nautical miles
- Number of unique airports visited
- Top aircraft you fly
- Most frequent routes
- Most visited airports

All of this is calculated from your actual flight data. The distance calculation uses the Haversine formula on your recorded coordinates, so it reflects your actual path rather than just the great circle distance between airports.

## Remote Autopilot Control

RadarThing now supports sending commands to your own aircraft remotely. This is useful when you are away from your desktop but want to adjust your autopilot settings. From the radar interface on your phone or another device, you can:

- Set speed
- Set altitude
- Set heading
- Set vertical speed
- Assign squawk codes
- Change Waypoints
- Disable NAV mode

Your userscript polls for commands every few seconds and executes them automatically. This means you can step away from your computer during cruise and still make adjustments if needed.

## Aircraft Images

The community can now contribute aircraft livery images. When viewing an aircraft on the radar, you see the actual livery if someone has uploaded an image for that airline and aircraft type combination. There is an approval system in place to ensure quality, and contributors get credited by their Discord username.

## The Technical Stack

The architecture has matured as well. The frontend runs on Next.js with the T3 stack. Real-time updates flow through a dedicated Server-Sent Events server that handles position broadcasts to all connected radar viewers. Convex handles the database for flight logs, user data, and aircraft images. Clerk manages authentication.

Each flight session tracks not just coordinates but also maximum altitude reached, maximum speed achieved, squawk code, and calculates duration automatically. This data populates both the individual flight view and the aggregate statistics.

## What Changed Since November

Looking back at the original post, the core radar functionality remains the same. The smart polling, accurate altitude display, and Foo filtering all work as before. But the platform around it has expanded significantly:

**November 2025:**
- Basic aircraft position on map
- Real-time data only
- Anonymous viewing
- Desktop control only
- No aircraft images

**Now:**
- Full flight details with flight plan visualization
- Flight history with route replay
- User accounts with stats and dashboards
- Remote autopilot control from any device
- Community-contributed liveries

## What Is Next

The roadmap includes more detailed flight analytics, possibly landing rate detection, and better route planning tools for controllers. The foundation is solid now, so adding features is more about polish than infrastructure.

If you are doing ATC for GeoFS or just want to track your flights, check out [RadarThing](https://radarthing.com). The userscript takes seconds to install, and you immediately get access to flight logging and the improved radar experience.
