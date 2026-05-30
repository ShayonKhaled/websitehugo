---
title: "Gesture-based macro controller"
description: "Things i learned while building my own macro controller."
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


![](/img/posts/gesture-based-macro-controller/IMG_4934-2-Large-e1700042342141.jpeg)


## April, 2023: I got onto the hype train

When I started working on it, building your own Macro Keypad was pretty trendy and a lot of YouTubers were doing it. While I found them to be cool, one thing I was slightly annoyed of how everyone was limiting themselves to basing the design around switches and knobs only.

![](/img/posts/gesture-based-macro-controller/Screenshot-2023-11-15-at-16.58.48.png)

I mean, I get it, we’re building macro keyboards, and keys and knob are what make keyboards…keyboard. But what’s wrong with other forms of input, especially the ones that are hands-free?

I really wanted to build a gesture-based macro controller because a lot of times I’m listening to music while working on something on my desk or eating. It would be far easier for me to do a quick gesture to play/pause the music than fumbling around with the keyboard/mouse.

So I got to work.

A friend of mine recommended the Lolin (A.K.A Wemos) S2 Mini board which was based on ESP32-S2, dirt cheap, and most importantly – had USB-C. So I ordered two of that and a PAJ7620-based gesture sensor. They were here within a few days.

![](/img/posts/gesture-based-macro-controller/IMG_3573-4-Large.jpeg)

I started off with sketching the rough design on a piece of paper, then modeled it on Fusion360.

![](/img/posts/gesture-based-macro-controller/IMG_4183-2-Large-2.jpeg)

![](/img/posts/gesture-based-macro-controller/IMG_4187-2-Large.jpeg)

The concept was that it would be standing on the desk and I would point my finger towards it (from a distance) making a gesture to control stuff. I took some measurements from the comfortable height of my finger when my palm is resting on the desk and based the design around that.

Ergonomics apart, I also wanted it to be simple and minimalistic, which was the reason behind sticking to basic geometrical shapes for the design.

![](/img/posts/gesture-based-macro-controller/IMG_4194-2-Large.jpeg)

![](/img/posts/gesture-based-macro-controller/IMG_4197-2-Large.jpeg)

After printing, it didn’t turn out to be as ergonomic as I hoped it to be though, nor was it pretty. It looked rather clumsy, and pointing finger towards the sensor while resting my palm on the desk didn’t feel natural. It felt forced.

I went back to the drawing board again.

* * *

## May, 2023: KISS, keep it simple, stupid!

After designing the draft, I got busy with other projects and stopped working on it. Although whenever I had nothing else on my mind, I would think about how to make the design more ergonomic and look for inspirations while browsing similar projects.

Somewhere around the middle of May, I realized something.

I was getting nowhere with thinking. It was a simple project, and the only way to get the perfect balance of ergonomics and aesthetic is to keep iterating until I find it.

So the project resumed again. I made the design even more simple with just a rectangle with overly-rounded corners.

![](/img/posts/gesture-based-macro-controller/IMG_4896-Large.jpeg)

This time, I decided to add some WS2812 LED’s to it as well, and have a semi-transparent layer in the enclosure for the LEDs to shine through. Lastly, a chamber to hold some small neodymium magnets which would allow the macro controller to be attached magnetically to my keyboard, which had a metal base.

It looked like this in rendering –

![](/img/posts/gesture-based-macro-controller/IMG_4925-Large.jpeg)

And came out pretty good when I printed it.

![](/img/posts/gesture-based-macro-controller/IMG_4916-1-1.gif)

I changed to red for the base and yellow for the top in the final print.

![](/img/posts/gesture-based-macro-controller/IMG_4934-2-Large-e1700042342141.jpeg)

The white part was the semi-transparent layer for LEDs.

Since this was a prototype I wanted to use for a few months before building a more permanent version, the sensor and the ESP32 was directly wired to each other and then hotglued at their respective places.

![](/img/posts/gesture-based-macro-controller/IMG_4941-Large.jpeg)

As for the LEDs, I used this WS2812-compatible strip –

![](/img/posts/gesture-based-macro-controller/IMG_4939-Large.jpeg)

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

![](/img/posts/gesture-based-macro-controller/IMG_5022-2-Large.jpeg)*Chilling on the desk*![](/img/posts/gesture-based-macro-controller/IMG_5021-Large-1.jpeg)*Magnetically attached to my keyboard. I love this feature.*![](/img/posts/gesture-based-macro-controller/IMG_5028-Large-1.jpeg)*The USB-C port. Looks quite professional, I’m proud of myself.*

## The end: Ship fast or never

This was a fun side project. Although on the inside it looks like a time bomb, I believe it looks pretty well-made from the outside. Right now, my plan is to use it myself regularly for a few months to find all the places where it has room for improvement.

And then, I’m going to make a revised version with the ESP-32 S2 module and PAJ7620 directly soldered on a PCB instead of using them in their dev board and module forms.

One last thing. A few days after finishing the project, I made myself a small poster to keep on the desk.

![](/img/posts/gesture-based-macro-controller/IMG_5619-Large.jpeg)

Sounds cryptic, doesn’t it?

What it means to me is that if I want to ship something (in the sense of finishing a product), it’s gonna be either churning out iterations after iterations as fast as possible or taking it slow, getting too busy solving imaginary problems and ended up shipping never.

Just a phrase I’ve come up with.

Is this true? Debatable.

Does it work for me? Yes. There’s no debate about that.

Let’s just leave it at that.

