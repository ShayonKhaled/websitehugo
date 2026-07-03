---
title: How's June going so far
description: Life updates, mostly
date: 2026-06-21
url: /hows-june26-going/
draft: false
categories:
  - Blogs
tags: []
---


The thought of writing a blog doesn't naturally cross my mind on a daily basis. I'm only writing this one because I was going through my GitHub repositories, found the one for my website, and realized it has been a while since the last time I wrote something.

My June has been interesting. I have been extremely busy with university coursework and some projects, but in my spare time, I have been exploring AI agents. I know I'm a bit late to the party, but I've always been reluctant to jump onto hype trains due to FOMO. Now feels like a good time to start looking into it.

I have been hearing about OpenClaw for a long time, but I didn't want to try it due to security vulnerabilities. It also seems very capable, but I don't have that much going on in my day-to-day life to need something so complicated. Additionally, it is pretty expensive to run, and I can't afford it.

Instead, I decided to start with Hermes, developed by Nous Research. Their selling point is that Hermes has a functional memory and a built-in learning loop. It gets better as you use it, learns from its mistakes, learns more about you, and uses that information to improve itself.

You can self-host it, so I installed Hermes on my Proxmox server inside a Debian VM. For the API, I chose to use DeepSeek, specifically the V4 Flash and V4 Pro models, mainly because it is extremely cheap and capable enough for my day-to-day work.

If I were to use APIs from Anthropic or other US-based companies, I'd probably be paying at least a few dozen dollars a month depending on usage, which is hard to justify unless I'm sure I can put it to good use. On the other hand, I can load two dollars onto DeepSeek and it works for days. That's a better deal for me. 

### My Custom Agents

I set up Hermes with DeepSeek and created two agents:

- **Nexus:** My general-purpose agent for organizing my day-to-day life.
    
- **Sophia:** My academic agent that tracks assignment deadlines and manages files.
    

I connected Google's NotebookLM to Sophia and uploaded all my course materials to it. Whenever I need to search for a piece of information across a lot of lectures, I can just message Sophia on Discord, and she finds the file or tracks down the information, which has been incredibly helpful.

When you open YouTube, content creators do a lot of flashy things with AI, but I don't really have use cases for those fancy configurations. My most used function in the last three weeks has been asking it to remind me to submit my assignments on time. It acts as a smart reminder bot and tracks homework files. Sometimes I ask when the exams for a course are, and Sophia queries NotebookLM and returns the response. There is no chance of it hallucinating unless NotebookLM hallucinates first. It's a boring application, but it works for me and has been useful.

### AI for Coding: Claude Code to Reasonix

After exploring how cheap DeepSeek is, I started using AI agents to code. Previously, I was a basic user: either pasting a snippet into a chat interface to ask what was wrong, or using Copilot inside Visual Studio Code to check certain parts of the code.

Then I tried the Claude Code CLI, which was nice for a few days. It's supposed to be used with the Anthropic API, but I bypassed it and routed the requests to the DeepSeek API instead. It was significantly cheaper, but still getting a bit expensive, and I wanted to lower the cost further.

That's when I found Reasonix, an agent framework specifically optimized for DeepSeek. DeepSeek offers a very low price for cache hits, and Reasonix optimizes queries to hit as much of the cache as possible. Even with short chat conversations, I hit at least 90-95% cache hits, and for long agent loops, it sometimes goes as high as 99%. It costs me maybe 20 to 30 cents for a whole day of coding, which is great.

### Building a Hardware Companion Device

I've also been building a desktop companion device for Hermes. The problem is that Hermes messages me over Discord, but I turn off phone notifications for everything except Teams (since university updates and critical reminders come through there). Because I don't check Discord for hours at a time, I miss Hermes' notifications.

To fix this, I am making a desktop notifier with a screen and a light that flashes whenever a message needs my attention. I'm building it using a Raspberry Pi Zero, running an MQTT broker. When Hermes has a notification, it sends it over MQTT to an OLED screen, a WS2812 LED light, and a Time-of-Flight (ToF) sensor.

The light will keep flashing until I acknowledge the notification by waving my hand over the ToF sensor to dismiss it so it shuts up. Eventually, I'll 3D-print an enclosure for it.

### Why the Raspberry Pi Zero?

A generic microcontroller like an ESP32 or Raspberry Pi Pico would be perfectly capable of running this, but I chose the Raspberry Pi Zero because I wanted to try using Reasonix to write the code.

With a standard microcontroller, it has to be physically connected to a computer to upload code manually over USB. I could connect it to my laptop, create a VM, pass through the USB port, and install an agent framework there, but debugging and reading data from microcontrollers is still not as native to an AI agent as a standard Linux environment is. 

Because the Raspberry Pi Zero runs Linux, I can connect it to my Tailscale VPN network. This allows my coding AI agent to communicate with the Pi over SSH, run commands, deploy programs, and check the output automatically by itself. I can run really tight, fast AI agentic feedback loops without having to do much manually. It's slightly overkill, but I borrowed an old Raspberry Pi Zero W from the university for the project, so it wasn't expensive. 

I'll probably write more about it some other day.