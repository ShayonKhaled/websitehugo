---
title: "i made a web app to start book-crossing"
description: "A build log for Boiboi.xyz — a personal book-crossing tracker web app built with Vue, Chakra UI, and Firebase; notes on development, deployment, and lessons learned."
date: "2021-10-14"
url: "/boiboi/"
draft: false
categories:
  - Projects
tags:
  - boiboi
  - web-app
  - vue
  - chakra-ui
  - firebase
  - netlify
  - book-crossing

---
October 14, 2021

# From Zero to Boiboi.xyz: My Rather Unorthodox Dive into Developing a Web App

![](https://shayonkhaled.com/wp-content/uploads/2022/01/boiboi.xyz_-1200x632.jpg)

**Before I say anything about what this is, let me show you the About section of Boiboi first so you get the concept from that.** You can also visit the website [here](http://boiboi.netlify.app/).

- ![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/Screenshot-2023-02-25-at-17.21.10.png?resize=2940%2C1912&ssl=1)
- ![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/Screenshot-2023-02-25-at-17.21.16.png?resize=2940%2C1912&ssl=1)

**In summary, Boiboi served as my personal book-crossing tracker.**

This was my first attempt at making a proper web app from scratch. I had previously worked with (web) apps for mobile devices before, but they were very basic and made by no-code solutions like MIT App Inventor and Thunkable. Not like I have anything against the no-code movement, but I just wanted to explore the frameworks and start something that would be both fun and a great learning experience for me.

That’s where Boiboi.xyz came in.

It took me about a month to build the first version of the website. While I would love to say that it was because I was taking my sweet time with learning the basics – that’s not how it happened.

I decided to take a different approach with it.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2903.jpg?resize=720%2C960&ssl=1)The $100 Startup @ Second Cup![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2906.jpg?resize=504%2C960&ssl=1)Inferno @ North End Coffee Roasters![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2907.jpg?resize=504%2C960&ssl=1)Inferno @ North End Coffee Roasters![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2905.jpg?resize=1170%2C2532&ssl=1)Animal Farm @ Crimson Cup![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2904.jpg?resize=720%2C960&ssl=1)Zero to One @ Glorea Jeans![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2920.jpg?resize=504%2C960&ssl=1)Schoolgirl @ Crimson Cup North![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2915.jpg?resize=504%2C960&ssl=1)The Archer @ Crimson Cup North![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2914.jpg?resize=719%2C1372&ssl=1)The Archer @ Crimson Cup NorthSome pictures I took during the drops

Instead of learning from the bottom up (mastering JavaScript and etc.), I researched what tools I needed to learn to build Boiboi, and simply started learning Vue JS and Chakra UI instead of mastering HTML, CSS and JavaScript first.

That resulted in a lot of going back to the basics and learning new things on the fly, and of course – a lot of frustration. While I would definitely recommend everyone to learn the basics first, it still ended up working out just fine for me.

As a matter of fact, I think I probably would have lost interest if I tried to learn the basics and make simpler projects at first. Choosing a hard but tangible goal pushed me out of my comfort zone and made me work harder for it, which is not a bad thing right?

Anyway.

I dropped books around the city for five months – from October 2021 to February 2022. Got busy with university admissions and left Bangladesh soon, so no drops happened since that. But despite the abrupt ending, it was still one hell of a 6-month project.

#### What did I put inside the books?

- ![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2919.png?resize=640%2C1024&ssl=1)
- ![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2918.jpg?resize=853%2C1024&ssl=1)
- ![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/IMG_2916.jpg?resize=1024%2C585&ssl=1)

Each book had a printed copy of a letter to the reader, a letter to the authority (in case some staff found the book and brought it to the manager) and a code that was to be entered on the website.

#### Did I get any response?

Yes, surprisingly I got my first entry on the website after dropping only five books. I wasn’t expecting anything before at least the 20th drop (which never happened), so my excitement went through the roof when someone actually filled out the form on the website.

![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/Untitled-design.png?resize=473%2C1024&ssl=1)![](https://i0.wp.com/shayonkhaled.com/wp-content/uploads/2023/02/Untitled-design-2.png?resize=473%2C1024&ssl=1)Some screenshots from that day haha

It always feels so good when someone uses something you’ve made – no matter how insignificant it is.

#### How is it going now?

The app is still live on Netlify, but I didn’t renew the domain (www.boiboi.xyz) last year so currently it can be just accessed with the [Netlify subdomain](http://boiboi.netlify.app/).

I do want to revive the project at some point, but I don’t think that would be anytime soon.

#### Technical details

- **Technologies used:** Vue JS, Chakra UI & Firebase.
- **Hosting:** Netlify

#### Things I wish I did better

- Making the website mobile-friendly, which is what probably anyone who picked up the book would use to check the website.
- There’s a bug in the website which prevents users from using direct links to visit a page. For example, you will get an error if you try to visit the About page directly using [https://boiboi.netlify.app/about](https://boiboi.netlify.app/about). You need to go to home page and click on the About button in the menu to do that.

#### Conclusion

Before Boiboi, I always thought of myself as a hardware guy, someone who enjoyed building things that can be touched. The closest I ever got to coding was when I had to write code for microcontrollers and software to control them from my computer.

Because of my lack of experience in programming, I was pretty bad at it, which is why the thought of programming scared me.

But with this fun little project, I managed to overcome my fear of coding and threw myself into finishing a software project. This is what I consider as the most significant outcome of creating boiboi.xyz.

Sure, the website has plenty of room for improvement. But whenever I reflect on it, I think of all the awesome memories I made while creating the website and leaving the books around.

And that’s what matters the most. To me, at least.

In

* * *

* * *
