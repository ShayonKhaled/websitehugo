---
title: "Building, crashing, and learning about quadcopters"
description: "About that time I built and flew quadcopters for kicks."
date: "2023-07-25"
url: "/building-quadcopters/"
draft: false
categories: 
  - Hobbies
tags:
  - quadcopters
---

![](/img/posts/building-crashing-learning-quadcopters/building-and-crashing-featured-pic.jpg)


## 2012: Browsing random RC forums

Now, this might sound like an exaggeration, but I do like to think that this project did not start in 2023. The first time I wanted to build something like this, it was back in 2012.

As a kid, I used to spend most of my free time on the internet, scrolling through random forums. One of my favorite haunts was [www.rcgroups.com](http://www.rcgroups.com/). It was a forum dedicated to everything radio controlled – cars, planes, multicopters, and you name it.

I was obsessed with them, and at one point, I even tried building my own RC plane using hard drive motors. But, it was a bust since I had no clue where to find the right components in Bangladesh.

Fast forward to when I turned 20 – RC stores got easier to find in my country, and the components became more affordable. So, as a birthday gift, my parents got me the components for my first quadcopter build, which I completed during the pandemic.

* * *

## February, 2022: My first build & the maiden flight

![](/img/posts/building-crashing-learning-quadcopters/1.jpeg)*May – The S500 build*![](/img/posts/building-crashing-learning-quadcopters/2.jpeg)*KK 2.1 Flight Controller*![](/img/posts/building-crashing-learning-quadcopters/5.jpeg)*FlySky FS-I6X Radio Transmitter*![](/img/posts/building-crashing-learning-quadcopters/4.jpeg)*…with crappy joysticks*![](/img/posts/building-crashing-learning-quadcopters/3.jpeg)*A low voltage alarm*

To be honest, I thought building my first quadcopter would be a breeze. All I had to do was make a list of the necessary components, assemble them, and voila! I was good to go. So, I put together a list of compatible components and headed to the shop.

And that was the first time I discovered things always _never_ go as planned in this hobby.

The motors I wanted – 900 KV motors – weren’t available, and all they had were 1400KV motors that were woefully underpowered for my heavy frame with a lower thrust. Rather than waiting for the right motors, I made the foolish decision to go ahead with what they had in stock.

I mean, how bad could it affect the performance, right?

![](/img/posts/building-crashing-learning-quadcopters/Emax.jpeg)*The 1400KV Emax Motors I mistakenly purchased*

But yes, as I soon found out, the motors were definitely not the right fit for the huge frame.
{{< youtube BxpymZccCqY >}}
Despite the underpowered motors, my first quadcopter did manage to take off, and **that moment was simply magical**. I was thrilled beyond words to see my creation soar through the air, even if it wasn’t performing at its best.

The experience left me feeling incredibly excited and inspired – eager to make improvements.

Unfortunately, my excitement was short-lived, as disaster struck during my next outdoor flight. In a moment of carelessness, I cut off the throttle at a height of about 40 feet, causing my quadcopter to come crashing down and breaking one of its arms.

![](/img/posts/building-crashing-learning-quadcopters/ezgif-2-2777da8674.gif)*Screenshot taken from my Instagram story I posted that day. Very “ahahaha” of me indeed.*

It was a painful lesson learned – one that reminded me of the importance of caution and patience when working with delicate equipment like this. But, I wasn’t about to give up just yet.

Undeterred by the crash, I ordered a new arm and set out to get my quadcopter back in the air. However, things didn’t go quite as planned again (by that time I was starting to realize it was a part of the hobby).

The smoothness in the controls that I had experienced before was gone, and for some unknown reason, the quadcopter wasn’t taking off until 50% throttle and kept shooting up rapidly into the sky whenever I went past that. And, the moment I reduced the throttle, it would come crashing down.

At first, I thought it might just be my shaky fingers, but even a friend of mine who’s an experienced RC plane flyer gave the same feedback. It was a frustrating setback. After trying out resetting the firmware of the flight controller I was using (KK 2.1) several times, I gave up and concluded that the last crash may have damaged the accelerometer of the flight controller or something.

And that’s where the new flight controller came in – the mighty ArduPilot APM 2.8.

* * *

### April, 2022: New flight controller & LED controller

![](/img/posts/building-crashing-learning-quadcopters/278664193_1299376640551198_3511876816306273477_n.jpg)*Ardupilot APM 2.8*

I had a soft spot for it because it was based on Arduino Mega – a board from the same family I used in a lot of robotics projects of mine. The flight controller was discontinued in 2013 and the one I got my hands one was a Chinese knockoff – but it still worked just as good.

It would be better to go for the latest version (Pixhawk), but I didn’t have the budget for that so settled for APM 2.8.

Now, KK 2.1 was a beginner-friendly board so that didn’t require any software to set up – everything was to be done with the onboard buttons. But APM 2.8 was actually made for advanced multicopters with GPS and autopilot capabilities – so it came with its own “Mission Planner” software. The initial setup process was a bit tricky, but it flew like a charm when I was done.

{{< youtube xstSLi8oMlU >}}
*Well, it was still a bit flinchy, but the PID tuning was still a work-in-progress so yeah.* 

And now that it was flying properly, I could finally start working on the fun part – adding custom accessories to the quadcopter.

Obviously, the first thing I decided to do was adding some RGB LEDs.

![](/img/posts/building-crashing-learning-quadcopters/L1.jpeg)![](/img/posts/building-crashing-learning-quadcopters/L2.jpeg)![](/img/posts/building-crashing-learning-quadcopters/L3.jpeg)*I had also taken an interest in photography at that time – as you may already have noticed in the _artsy_ photos in this post.*

I also made an LED controller based on an Arduino Nano – to control the LEDs. It was a fun little project.

![](/img/posts/building-crashing-learning-quadcopters/Controller.jpeg)*Used some ULN2003 transistor arrays to control the power-hungry LEDs. The Arduino was connected to one of the spare channels of the radio receiver – so I could control the lights from my radio transmitter.*

**And the end result looked amazing! Check this out –**
{{< youtube lSsd6k9WY >}}
Fun fact, I also composed the background music of the video myself.

Now, why does the title say that this is the last video of the S500 frame?

Because, I decided to get rid of the S500 frame and use the components for a new build – something smaller and more agile – something I would end up calling “Dione”.

Although my learning pace eventually outgrew that first quadcopter, it will always hold a special place in my heart as the one that started it all. It taught me the basics and helped me discover my passion for this hobby.

* * *

### Technical details of the S500 build

- **Frame:** S500 (Glass fiber edition).
- **Flight controller:** KK 2.1.5 (Clone), ArduPilot APM 2.8 (Clone)
- **Motor:** Emax XA2212 1400KV
- **Propeller:** No-brand 8045
- **Electronic Speed Controller (ESC):** Emax BLHeli 40A Brushless ESC.
- **Battery**:

  - **Red Volcano 3S 35C 1500mah battery**: NOT RECOMMENDED. Died after two uses.
  - **TigerPower 3s 35C 3000mah:** Okayish for the price. Not reliable.
  - **Tattu 3s 35C 2200mah:** Decent quality, recommended.
- **Battery charger:** Imax B6 (Clone).
- **Radio system:** FlySky FS-I6X with FS-IA10B receiver.
- **Custom LED lighting:**
  - Arduino Nano and ULN2003 for driving the LEDs.
  - 5MM RGB LEDs.

* * *

## May 2022: New build (Dione) & a (failed) quadcopter revolution

One problem I faced with my S500 frame build was that I always felt a lack of thrust. Like, after take off, if I dropped altitude for some reason, I’d need almost all of the throttle to stop the descent.

And I thought the reason was that it was a heavy frame. _Well, unless that wasn’t it._

Turned out, when I went to the electronics shop for the first time, I originally asked for 1000KV motors but they didn’t have any. I also wanted F450 frame, which they didn’t have either (it’s a smaller frame than S500, the number denoting the width)

They offered 1400KV motors and S500 frame, and I thought, yeah, how big of a difference it can make, right?

Apparently S500 frame should ideally have 900KV or lower motors because they need more thrust to take off and fly okay. It’s a decent frame, I just didn’t have the right set of motors for it.

I had two choices. Either to buy four new motors with lower KV ($$$) or get a smaller frame ($).

Went for the latter. Because other than the thrust issues, S500 was also a HUGE quadcopter and it wasn’t really convenient to carry to places. So I ordered a (clone) DJI F330 frame which arrived in two days, spray painted the arms black and transferred all the electronics from the S500 to it.

Except for the LED controller and the LED lights. The first _cultural_ _shock_ that came from the _exchange programme_ was that I no longer had the space for random accessories in the quadcopter. It was a pretty tight build. Too bad…

![](/img/posts/building-crashing-learning-quadcopters/dione.jpeg)*Behold, the Dione!*

And I was pleasantly surprised when it started flying perfectly at the first attempt. No more power issues, the motors were perfect for it. Another plus point, _Dione_ also looked much cooler than its predecessor!

![](/img/posts/building-crashing-learning-quadcopters/ezgif-2-660e5d9b95.gif)

> ###### _On May 2, 2022, history witnessed the first-ever Quadcopter Revolution coming to a sudden standstill, under my (foot’s) firm control._

Of course, it wasn’t all that good. During my first outdoor flight with it, it suddenly _stopped_ listening to my radio.

Like, it literally wasn’t responding to my stick inputs. I tried disarming the motors, but it wouldn’t disarm; it just started going up slowly, hit a tree and crashed onto the ground. Despite me almost breaking my radio trying to turn it off, the propellers were still spinning (slowly). Which meant, I couldn’t reach in and unplug the battery without getting my fingers chopped.

Sometimes life gives you lemon and…you decide you need to abuse your quadcopter for the greater good.

I put my foot on the quadcopter and jammed the propellers with my shoe, and then quickly unplugged the battery. I knew that was gonna burn out the ESCs and possibly the motors but I couldn’t just let it have its intrusive thoughts on the pavement in peace while not listening to my radio, right?

![](/img/posts/building-crashing-learning-quadcopters/Untitled-design-60.jpg)

Fortunately only the propellers broke, everything else was fine.

Later I found out the APM Flight Controller had a return-to-home mode which triggered automatically if the radio signal was lost for longer than 2 seconds. The radio I was using (FlySky) was infamous for having its signal dropping sometimes. So my quadcopter tried to return to the takeoff position.

Commendable. Only problem, I never put a GPS on it.

So instead of landing immediately, it was going to climb some height and then try to locate the takeoff position (without a GPS? good luck), but the plan was cut short by the trees and then my trusty sneakers.

Anyway, I turned that option off and it started flying a-ok again. I even went for some indoor flights. It noticeably was far more agile than the S500.

![](/img/posts/building-crashing-learning-quadcopters/ezgif-1-ec64eb5083.gif)

For a while, the idea of getting a GPS module lingered in my mind, unsure of my next move. Then I came across an advertisement of an FPV quadcopter online and messaged the seller to ask if it was still available – out of curiosity.

“Yes, it is.” Three words that marked the beginning of my journey down the rabbit hole.

* * *

### Technical details of Dione

- **Frame:** DJI F330 (Clone and painted matte black)
- **Flight controller:** ArduPilot APM 2.8 (Clone)
- **Motor:** Emax XA2212 1400KV Brushless motors.
- **Electronic Speed Controller (ESC):** Emax BLHeli 40A Brushless ESC.
- **Battery**:

  - **TigerPower 3s 35C 3000mah:** Okayish for the price. Not reliable.
  - **Tattu 3s 35C 2200mah:** Decent quality, recommended.
- **Battery charger:** Imax B6 (Clone).
- **Radio system:** FlySky FS-I6X with FS-IA10B receiver.

* * *
## June 2022: Getting started with FPV & the 5 inch freestyle (re)build

When I was inquiring about the FPV quadcopter was up for sell (it’s not a huge scene in my country so that was the only listing then), I didn’t have any FPV-related equipment. I managed to buy the quadcopter for almost half the price he initially asked for, but it was certainly not in pristine condition.

And when I say not pristine…

![](/img/posts/building-crashing-learning-quadcopters/287705147_1485215511881556_8131091348215005664_n.jpg)

When it arrived, the first shock was the condition of the electronics. Those joints really make you wonder if he tried to solder the wires by lighting the board up on fire…

![](/img/posts/building-crashing-learning-quadcopters/289958922_358380469737109_2010048169075661551_n.jpg)

It was so bad that I didn’t even have the courage to rebuild the quad myself. It would require soldering the radio receiver, video transmitter, camera and other stuff onto the flight controller which is pretty straightforward if it’s new and you have the pinout diagram. But in this one, the texts were all smudged and he couldn’t even tell me the model number or anything.

So I reached out to one of the few FPV shops asking them if they could rebuild the quadcopter. They gave me a quote that was almost half of what I paid for it. They explained it was because the electronics were on their last breath, so they had to consider the risk.

Very fair. Except that I couldn’t afford that amount, as a broke student. Little did I know, that quote will turn out to be peanuts comparing to what I would be spending on this hobby in future..

Anyway, I found a local FPV pilot who agreed to rebuild it for a price that worked for me. But even he was horrified when he finally received the package and got to see the condition of the parts for the first time.

“It looked bad enough in the pictures, but this bad? Please know that I tried my best if this thing doesn’t fly even after assembling everything.”

I assured him that I was aware of the condition and wouldn’t blame him if it didn’t work out.

Fortunately, he managed to rebuild the quadcopter without breaking anything (probably wasn’t a fun experience lol) and sent me the picture of the assembled quad after a week.

![](/img/posts/building-crashing-learning-quadcopters/288206860_599325788425929_4286445936409956619_n.jpg)*Look at that workbench tho*

Well, not fully assembled. I still had to solder the radio receiver myself and set up the Flight Controller using configurator software.

Which went okay. It wasn’t too hard, and I got to get it flying after like a day or two of work. At that time I still had only 3S batteries (used in the previous builds) so it flew like a brick, but it flew.

Naive me was unaware of what the propellers of a 5 inch could do, so of course the first flight was inside

Great, the quadcopter’s flying. So what do I need now?

* * *

### Mid-May, 2022: My first pair of FPV goggles

A pair of FPV goggles, of course. But again, I couldn’t afford a new pair of goggles for one. The hobby was getting financed by what I had saved up from writing tech-related articles for clients and selling off the parts of the previous quadcopters I built.

Secondly, at that time literally no one in my country had any decent goggles in stock, everyone was pre-ordering and waiting months for it to arrive. Neither did I have the money nor the time/patience to wait.

Luckily, a guy posted some pictures of an Eachine VR-007 that was up for sell. While the goggles was as basic as it could get, I could finally get my feet wet with FPV without breaking the bank.

However, in hindsight, the goggles weren’t the highlight of the deal. It was the opportunity to get to know him. He was the first person to make me realize how the quadcopters I had been building were outdated, and how the latest generation multicopters were designed. I owe a great deal of my knowledge about these things to him.

![](/img/posts/building-crashing-learning-quadcopters/285719101_436027974611741_7429223885884562043_n.jpg)*Eachine VR-007*

I put some stickers on the goggles to give it some swag. And then came the second problem.

![](/img/posts/building-crashing-learning-quadcopters/290333535_2202135459954316_1568723253746058764_n.jpg)

The new video transmitter (RushFPV Racing) I installed, it wasn’t working with the FPV goggles for some reason. Then I installed the previous one (Eachine TS5828L), that didn’t work either. All I got was static.

I reached out to another shop owner, with whom I had a good relationship from purchasing various items, and asked him to inspect everything using his setup. He discovered that the camera I originally received with the quadcopter (from the person with TERRIBLE soldering skills) was a goner.

Bought another _used_ camera from him and finally go the FPV setup to work. All that troubleshooting took my about 3 months, most of which was saving up for replacement parts and waiting for shipping.

* * *

### July, 2022: First FPV flight & a proper radio

I already had more than 20 hours on simulator, but my first flight was very, very shaky. That being said, it was the most fun experience I had in a while. Felt like all those efforts were finally paying off.

In the next few weeks, I went through a bunch of upgrades.

The first one was…

![](/img/posts/building-crashing-learning-quadcopters/Screenshot-2023-11-06-at-3.36.13.png)

Previously, I had been using this. The go-to radio for RC planes and quadcopters. It wasn’t the top-of-the-line, but with a range of 1 KM, I thought it would be a safe choice.

But at that time I didn’t know that freestyle quadcopters are the least forgiving when it comes to radio link quality. Because when I’m flying a plane, if the connection drops for like a second or two, the plane would simply be gliding. However, since I was planning on doing freestyle tricks while flying FPV, even the slightest latency could result in crashes.

And FlySky had a bad reputation among the FPV community for this. So I splurged a bit and got a decent-ish radio, the RadioMaster TX-12.

![](/img/posts/building-crashing-learning-quadcopters/Screenshot-2023-11-06-at-3.45.17.png)

The stock radio options it came with weren’t good enough – I went with a FRSky receiver which was slightly better than FlySky but still had complaints about radio signal losses.

But since this has a module bay, I could buy a radio transmitter module separately (was eyeing ELRS, never got around doing that though) and use the radio with that. It also ran OpenTX which was highly configurable and I could even flash EdgeTX on it. Pretty cool stuff.

* * *

### August 2022: The iFlight XL5 frame & smaller LED controller

My quadcopter setup originally came with a frame known locally as “Johnny V2”, which was basically a cheap clone of the AstroX X5 Freestyle Johnny FPV V2 frame. The problem with clone frames was that the carbon fiber would always be of lower quality, and the manufacturers never gave two shits about tolerances.

![](/img/posts/building-crashing-learning-quadcopters/291937157_759069392202144_7614765736612485588_n.png)

Seriously. This is an antenna mount I 3D printed with TPU that was designed for the Astrox X5 frame. But since the measurements of the clone frame were so off, I had to fight tooth and nail to install it.

Shortly after I started flying, I upgraded the frame to iFlight Titan XL5.

![](/img/posts/building-crashing-learning-quadcopters/307222458_1135061057099790_7357121767479613265_n.jpg)

It’s the only decent 5 inch frame I ever used, but I must say that my experience was very pleasant with this. It already came with a bunch of 3D printed TPU accessories, the build quality felt awesome and the PID tuning was a breeze.

I’d also upgraded the camera from a Cadxx Turbo EOS V2 to a Cadxx Tarsier that came with 4K DVR recording. But there wasn’t enough space in the frame to make room for the DVR board, so I printed an extended adapter for the camera.

![](/img/posts/building-crashing-learning-quadcopters/296274714_1368914820264046_7886231121398206447_n.jpg)

Keeping the camera outside the frame obviously meant that in the event of a head-on impact, the camera would be the first thing to break. But since I got it for so cheap, I didn’t care much since I had a replacement to go right in – if needed.

My second upgrade (more of an aesthetic one) was some LEDs.

But the catch was that these LEDs were not being controlled by the Flight Controller. I had the first version of Diatone Mamba F405 which was three years old, and in the latest firmware its LED pin got remapped to controlling one of the motors. That’s how fast things get obsolete here.

![](/img/posts/building-crashing-learning-quadcopters/Screenshot-2023-11-06-at-4.06.10.png)

I had an Attiny85-based DigiSpark development board lying around which was small enough to be wrapped in heatshrink and fit inside the frame. So that’s what I did, I uploaded a small Arduino code on it to cycle the colors on the WS2812-based LED strips, and powered it via one of the 5V pins of the Flight Controller. It looked pretty cool in the sky, although I couldn’t see it due to having the first person view, lol.

Moving on…

* * *

### September 2022: Moved to Japan, no more pre-orders

![](/img/posts/building-crashing-learning-quadcopters/300675572_779742196652681_8875322563790602606_n.jpg)*The 5 inch freestyle quad with a toy I got from a Gatcha machine*

Yep, that’s when my journey with FPV started going 📈📈📈. I moved to Japan where AliExpress would deliver stuff within 7-10 days. What’s even better, since Japanese people usually take good care of their stuff – there were plenty of awesome deals in the used marketplace.

### October 2022: I almost got killed by my quad

Earlier, I mentioned several times how beaten up the flight controller and ESC of my 5 inch freestyle quad was. Since it continued to work, I never considered replacing the stack (because it would be expensive to anyway).

But I had to change my mind after it tried to kill me on a sunny weekend.

Well, I’m making it sound too dramatic. What actually happened was a malfunction in the Flight Controller.

After reaching the end of the third pack, I landed about 20 feet away from me as usual, disarmed the motors, took my goggles off and started walking towards the quadcopter. That’s when I realized something was wrong.

Motor 3 was spinning up randomly. It wasn’t supposed to, I had disarmed already. But it was not starting at full speed randomly and then stopping. Which put me in a tough spot because…the disarm button on my quadcopter was the only way to make sure the motors weren’t spinning. If the quadcopter isn’t listening to my radio, there was nothing else I could do. I tried arming and disarming, the flight controller wasn’t responding at all despite radio link being all right.

Unlike last time (when Dione (the F330 build) switched to Return to Home Mode automatically and I put my foot on the motor to stop it), going near to the quad when it’s spinning and unplugging the battery wasn’t an option.

The motor would easily rip my shoe into pieces with the sharp propeller and if the other motors started up too launching straight into me…I’d be pretty messed up.

So I did what I thought was the safest. I picked up a long tree branch I found around, and flipped the quad using it. Finally, motor 3 stopped spinning.

Because flipping the quad enabled the safety feature on Betaflight (the firmware) that prevented the quad from arming inverted. I wasn’t sure if it would work, but it did. I approached the quad cautiously and unplugged the battery quickly with a shaky hand.

Bam. Time to retire it.

![](/img/posts/building-crashing-learning-quadcopters/326494702_1618904505199014_2051019335832537204_n.jpg)

Afterwards, I found out the reason. My Flight Controller (Diatone Mamba F405 MK1) had been released three years ago, and two other versions (MK2 and F7-based MK3) came out in the meanwhile with different pin mappings. When I flashed a newer version of the firmware, I had unknowingly enabled the conflict with motor 3 and the LED pin. Now, why the problem started occurring after a delay and not immediately after flashing the firmware, I’m not too sure. But from my research, this what what seemed to be the case.

![](/img/posts/building-crashing-learning-quadcopters/333017082_2801257453341958_1466509743181003664_n.jpg)

Anyway, shortly after the incident, I sold the 5 inch setup off. A big problem with flying it was that due to the open-prop configuration and of course, the size, I needed to go outside the city every time I wanted to fly it. I had been considering moving to a smaller class for awhile anyway, and after the malfunction, I decided to move on.

Even though the 5 inch gave me a lot of trouble, it still was a blast to fly. Later when I moved to whoops, I found myself longing for the power and momentum I had felt with the 5 inch.

* * *

### Technical details of the 5 inch freestyle build and my current setup

- **Frame:** AstroX X5 Clone => iFlight Titan XL5
- **Flight controller:** Diatone Mamba F405 MK1
- **Electronic Speed Controller (ESC):** Racerstar Special Anniversary Edition 35A ESC.
- **Motor:** Emax RS2306 2400KV
- **Propeller:** DALProp Cyclone T5040
- **Camera:** Cadxx Turbo EOS V2 => Cadxx Tarsier V2
- **Video transmitter (VTX):** Eachine TS5828L => RushFPV Racing
- **Antenna:** Foxeer Lollipop 3 V3 on both VTX and goggles.
- **FPV Goggles:** Eachine VR-007
- **Battery**: Tattu R-Line 4S 1550mAh 100C Li-Po
- **Battery charger:** Imax B6 (Clone).
- **Radio system:** FlySky FS-I6X with FS-IA8X => RadioMaster TX-12 and FrSky R-XSR

* * *

## January 2023: New cinewhoop (Siren), new goggles

![](/img/posts/building-crashing-learning-quadcopters/Screenshot-2023-02-26-at-3.47.32-min.png)

After selling off the 5 inch, I took a break. But it wasn’t long before I won an almost new cinewhoop on Yahoo Auctions. Considering the condition and the retail price, it was a steal.

I still needed to spend a bit more on a camera (the Runcam Nano 2) and some smaller 4S batteries. But shortly, I was back in the air with my new goggles which I also won on an auction, the FatShark Dominator V6.

![](/img/posts/building-crashing-learning-quadcopters/328237682_731783041606209_4578961224804562245_n.jpg)

Again, stellar condition, very good price. I love Japanese people for taking care of their stuff.

After grabbing a set of diopter lens inserts (I have myopia), I was all set. Life was good. For the first time, I was actually flying with some decent gear, not stuff that were on their last breath.

* * *

### February 2023: Cinewhoops are boring…

I was still facing some problems every now and then. Broken antenna cables for example…

![](/img/posts/building-crashing-learning-quadcopters/329635275_544899800937287_6596596702174753249_n.jpg)

Or broken propellers.

![](/img/posts/building-crashing-learning-quadcopters/329219321_578242710835079_5541486374940194397_n.jpg)

But overall, it wasn’t the usual maintenance that made me lose interest in Siren. It was the flying characteristics of them.

I bought a cinewhoop because I wanted something that would be less intimidating. With the closed-prop design, I could fly this on less-secluded areas without scaring anyone around.

Turned out I liked the agility of the 5 inch more. The cinewhoop was only suitable for slow and smooth flying – which would be wonderful for taking some cinematic footage with an action camera. But I didn’t want cinematic footage, I wanted to feel the adrenaline rush again. So I flew the cinewhoop maybe once every other week, but that was it.

![](/img/posts/building-crashing-learning-quadcopters/330812846_6195725560497202_6489112346916662086_n.jpg)

I never really managed to love it.

### Technical details of Siren

- **Frame:** BetaFPV Pavo30
- **Flight controller & ESC:** BetaFPV F722 35A AIO Board
- **Motors:** BetaFPV 1506-3000KV
- **Propellers:** Gemfan D76 5-blade
- **Camera:** Runcam Nano 2
- **Video transmitter (VTX):** RushFPV Racing 500mw
- **Antenna:** Foxeer Lollipop 3 V3 on VTX, Patch & ImmersionRC SpiroNet (stock) on the goggles
- **FPV Goggles:** FatShark Attitude V6
- **Battery**: Tattu R-Line 4S 650mah 100C Li-Po

* * *

## March 2023: Meet Grasshopper, the tinywhoop

At this point, I was quite exhausted with the hobby. And although Siren (the cinewhoop) ended up becoming quite reliable (not breaking down every other flight) after the initial hurdles, I didn’t enjoy flying it. And while it was certainly less intimidating than 5 inch, it still was noisy as hell.

So I still couldn’t fly around people, because this time they were annoyed by the noise, not scared.

I decided to go even smaller this time. Ended up going for a Happymodel Moblite7.

![](/img/posts/building-crashing-learning-quadcopters/IMG_8876-Large.jpeg)

And I started enjoying the hobby again. Because although it lacked the momentum of the 5 inch, it was still extremely fun to fly. The best part was, I could fly indoor on campus without bothering anyone.

Had some really good time with it. Until, of course, things started going wrong again.

![](/img/posts/building-crashing-learning-quadcopters/IMG_8877-Large.jpeg)

The canopy was unprotected. And I crashed pretty often. At some point, the flight controller must’ve had it and stopped working.

However, it was an AIO board and the camera & video transmitter was still working. I thought, this is a good time to take a break and do something else for a little while.

* * *

### April 2023: When you can’t fly, you drive

![](/img/posts/building-crashing-learning-quadcopters/April-23.jpg)

I designed and 3D printed a custom adapter to fix the AIO board, its battery and the camera onto an RC car. My classmate and I drove it around and had tons of fun for like a few weeks. The car also bumped into the walls a lot so when board’s power light finally stopped lighting up, I concluded that the AIO board is fully dead now and left it at a corner of my desk. Didn’t bother to check the camera, just wanted to take a break from FPV altogether for awhile as I was really tired.

* * *

### July 2023: Resurrection, the fire, and I quit

![](/img/posts/building-crashing-learning-quadcopters/July-24-1-day.jpg)

Previously when the AIO board stopped lighting up, I thought the VTX part was finally toasted as well.

But one day, I was just looking at it and then I realized the pins inside the battery plug were way deeper than they should be.

After checking for a bit, I found out the problem. The pins somehow got pushed inside further than their usual distance so when I was connecting the battery plug, there was no connection at all. And I hadn’t caredenough to check if the circuit was actually getting power and simply concluded the VTX finally died too.

Replaced the plug with a new one and voila, the VTX was working just fine. The weirdest part that, the FC was also functioning and getting recognized by the computer too.

I have no idea why. Power plug issue shouldn’t have anything to do with connecting to the computer, right?

But anyway, hoping to get back to the hobby again, I put the 1S batteries on charge. On my clone Imax B6, the only piece-of-shit equipment I never upgraded. **And then I left it alone.**

![](/img/posts/building-crashing-learning-quadcopters/362881269_1672865713214889_4664747575387003340_n-2.jpg)*I was VERY lucky that the 4S pack didn’t catch fire as well. It just got burned a bit on the side. I discarded it along with everything else. Never ever leave your Li-Po batteries alone while charging, I had to learn it the hard way.*

After a few hours, I was greeted with this scene. Apparently a fire broke out and went out on its own. With some el cheapo GNB batteries and an el cheapo clone battery charger, I wasn’t sure which one to blame (along with myself for leaving it alone). But one thing was for sure, this was it.

The fire was the last nail in the coffin. I will still enjoy [Joshua Bardwell](https://www.youtube.com/@JoshuaBardwell)‘s videos and watching others’ builds, but for the time being, I was gonna be just a spectator.

Don’t be like me and use subpar equipment. Stay away from cheap batteries like GNB. Go for Tattu. Charge on a metal rack, which was probably the only reason why the fire couldn’t do much damage. But it could’ve been much much worse.

* * *

## August 2023: The end

I found a buyer for the remaining of my setup, shipped everything to him, and got out of the hobby. Just like that.

Looking back, it’s incredible to see how much I’ve learned and how far I’ve come in just one year. Through trial and error, I’ve gained a ton of knowledge and experience in the world of RC flying, and I’ve met some truly amazing and knowledgeable people along the way.

Although I had to end my journey on a sour note, I certainly hope to come back some day.

And now, with new projects on the horizon and a whole community of fellow enthusiasts to connect with, I’m excited to see where my main journey as a maker takes me next.
