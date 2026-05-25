---
title: "gesture-Based macro controller"
description: "things i learned while building my own macro controller."
date: "2023-05-19"
url: "/gesture-based-macro-controller/"
draft: false
categories:
  - Projects
tags:
  - gesture
  - macro-controller
  - esp32
  - circuitpython
  - micropython

---


![](https://shayonkhaled.com/wp-content/uploads/2023/11/IMG_4934-2-Large-e1700042342141.jpeg)


## April, 2023: I Got Onto the Hype Train

When I started working on it, building your own Macro Keypad was pretty trendy and a lot of YouTubers were doing it. While I found them to be cool, one thing I was slightly annoyed of how everyone was limiting themselves to basing the design around switches and knobs only.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/Screenshot-2023-11-15-at-16.58.48.png?resize=1024%2C666&ssl=1)

I mean, I get it, we’re building macro keyboards, and keys and knob are what make keyboards…keyboard. But what’s wrong with other forms of input, especially the ones that are hands-free?

I really wanted to build a gesture-based macro controller because a lot of times I’m listening to music while working on something on my desk or eating. It would be far easier for me to do a quick gesture to play/pause the music than fumbling around with the keyboard/mouse.

So I got to work.

A friend of mine recommended the Lolin (A.K.A Wemos) S2 Mini board which was based on ESP32-S2, dirt cheap, and most importantly – had USB-C. So I ordered two of that and a PAJ7620-based gesture sensor. They were here within a few days.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_3573-4-Large.jpeg?resize=768%2C1024&ssl=1)

I started off with sketching the rough design on a piece of paper, then modeled it on Fusion360.

![](https://i1.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4183-2-Large-2-768x1024.jpeg?ssl=1)

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4187-2-Large-768x1024.jpeg?ssl=1)

The concept was that it would be standing on the desk and I would point my finger towards it (from a distance) making a gesture to control stuff. I took some measurements from the comfortable height of my finger when my palm is resting on the desk and based the design around that.

Ergonomics apart, I also wanted it to be simple and minimalistic, which was the reason behind sticking to basic geometrical shapes for the design.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4194-2-Large-768x1024.jpeg?ssl=1)

![](https://i1.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4197-2-Large-768x1024.jpeg?ssl=1)

After printing, it didn’t turn out to be as ergonomic as I hoped it to be though, nor was it pretty. It looked rather clumsy, and pointing finger towards the sensor while resting my palm on the desk didn’t feel natural. It felt forced.

I went back to the drawing board again.

* * *

## May, 2023: KISS, Keep It Simple, Stupid!

After designing the draft, I got busy with other projects and stopped working on it. Although whenever I had nothing else on my mind, I would think about how to make the design more ergonomic and look for inspirations while browsing similar projects.

Somewhere around the middle of May, I realized something.

I was getting nowhere with thinking. It was a simple project, and the only way to get the perfect balance of ergonomics and aesthetic is to keep iterating until I find it.

So the project resumed again. I made the design even more simple with just a rectangle with overly-rounded corners.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4896-Large.jpeg?resize=768%2C1024&ssl=1)

This time, I decided to add some WS2812 LED’s to it as well, and have a semi-transparent layer in the enclosure for the LEDs to shine through. Lastly, a chamber to hold some small neodymium magnets which would allow the macro controller to be attached magnetically to my keyboard, which had a metal base.

It looked like this in rendering –

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4925-Large.jpeg?resize=768%2C1024&ssl=1)

And came out pretty good when I printed it.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4916-1-1.gif?resize=320%2C240&ssl=1)

I changed to red for the base and yellow for the top in the final print.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4934-2-Large.jpeg?resize=768%2C1024&ssl=1)

The white part was the semi-transparent layer for LEDs.

Since this was a prototype I wanted to use for a few months before building a more permanent version, the sensor and the ESP32 was directly wired to each other and then hotglued at their respective places.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4941-Large.jpeg?resize=768%2C1024&ssl=1)

As for the LEDs, I used this WS2812-compatible strip –

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_4939-Large.jpeg?resize=768%2C1024&ssl=1)

With everything wired up, it was time to write the code.

### MicroPython vs. CircuitPython

Initially, the ESP32 came with Arduino bootloader flashed so I tested the sensor using Arduino. However, I’d been curious with MicroPython for awhile and wanted to try it – which wasn’t a pleasant experience.

I’m gonna be frank, MicroPython is very promising and the syntax is as simple as it gets. If I were to glue a couple of modules and an ESP32 and put something together really quickly, a high level language like Python makers that much easier. But when I tried to get Asynchronized input/output work with the drivers for WS2812 and PAJ7620, there were a lot of issues and the lack of documentation/community support compared to Arduino put me off.

We definitely are well-overdue for a high-level language in embedded instead of C being the dominant language for even the simplest stuff. It’s just that MicroPython’s libraries and drivers are still a work-in-progress which my experience a bit frustrating.

I decided to switch to CircuitPython instead. That felt slightly simpler and better documented than MicroPython. #HailAdafruit

The code was straightforward, CircuitPython already came with pre-written drivers for WS2812 and PAJ7620. I used the USB\_HID class to make the ESP32 S2 Mini pretend to be a keyboard. And lastly, to cycle the colors on the RGB LEDs while reading from the sensor concurrently, I used the AsyncIO library of Python.

In two days, I was done with my second prototype.

### Final result

To play the previous track, swipe left. To play the next track, swipe right. To toggle play/pause, move your hand towards the front. To mute, put your palm down on the controller (doesn’t have to be all the way down).

I was moving my hand rather aggressively in the video 😂  but a gentle swipe usually worked.

I took another video in the dark to show the LED lighting better. It also doubles as a desk light too lol. _The gesture sensor is disabled here to allow me to pick up the macro controller without changing the music._

Here are some more photos from various angles.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_5022-2-Large.jpeg?resize=576%2C1024&ssl=1)Chilling on the desk![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_5021-Large-1.jpeg?resize=576%2C1024&ssl=1)Magnetically attached to my keyboard. I love this feature.![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_5028-Large-1.jpeg?resize=576%2C1024&ssl=1)The USB-C port. Looks quite professional, I’m proud of myself.

## The End: Ship Fast Or Never

This was a fun side project. Although on the inside it looks like a time bomb, I believe it looks pretty well-made from the outside. Right now, my plan is to use it myself regularly for a few months to find all the places where it has room for improvement.

And then, I’m going to make a revised version with the ESP-32 S2 module and PAJ7620 directly soldered on a PCB instead of using them in their dev board and module forms.

One last thing. A few days after finishing the project, I made myself a small poster to keep on the desk.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/11/IMG_5619-Large.jpeg?resize=768%2C1024&ssl=1)

Sounds cryptic, doesn’t it?

What it means to me is that if I want to ship something (in the sense of finishing a product), it’s gonna be either churning out iterations after iterations as fast as possible or taking it slow, getting too busy solving imaginary problems and ended up shipping never.

Just a phrase I’ve come up with.

Is this true? Debatable.

Does it work for me? Yes. There’s no debate about that.

Let’s just leave it at that.

In

* * *

* * *