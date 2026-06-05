---
title: I made something that people are actually using
description: Cafeteria Lunch Menu Scraper Bot and Vibe Coding
date: 2026-06-05
url: /first-project-with-users/
draft: false
categories:
  - Blogs
tags:
  - scraper
  - bot
  - discord
  - claude
  - ai
---
I eat lunch at my university cafeteria very often, almost five days a week. I like the food. I don't like the lunch rush (it gets too crowded). 

I also don't like the way the menu is distributed. We can either check it in person by coming to the cafeteria, or they also send an email every week  with the weekly menu from where I used to check. But the problem is that the menu is a big wall of text and not super convenient to check from my phone. 

Obviously, it's not a big problem, and it wasn't the end of the world. I decided to automate it anyway: a scraper bot that will automate the process of finding the menu from my email, putting it into a database, and then sending the daily menu to me over Discord in a more easily readable format.

That way, I could just open Discord to check the daily menu without having to search through my email. I quickly put together a prototype using n8n, PostgreSQL and Playwright. It works by:

- Scraping the menu from my email on a weekly basis using the built-in Google OAuth2 integration in n8n.
- Introducing the browser session saved in Playwright to access the SharePoint menu.
- Sending the PDF version of the menu to the Anthropic API for processing, which returns a JSON response containing the menu.
- Parsing the JSON response and saving it to a database for each day of the week.

I had two workflows in n8n:

- One workflow scrapes the menu on a weekly basis.
- The second workflow checks the database for the daily menu and sends it to me on Discord through a webhook request.

I used it that way for about a week. Then I asked a guy from the university who runs one of the biggest Discord servers if he would be interested in integrating this with their server so the daily menu could be sent there as well. Mainly because it saves me a little time each day. But if others could use it too, perhaps the collective time saved would be a better ROI for me. He was happy to add it to their server. I added the server's webhook URL to my n8n workflow, and I think around 33 people signed up to be notified for the daily menu posts. 

Just like that, I made something for the first time in my life that was actively used by other people. Felt pretty cool. 

### Then came the Discord bot

At first, I did not have any plans to turn this into a bot because I wasn't anticipating much interest from others. I thought it would be a small pet project, for which the duct-taped n8n and webhook-based automations worked fine. 

However, after getting initial traction, I changed my mind. Some other classmates started asking if they could use it for their servers, and I didn't want to set up webhooks manually for each person. A Discord bot that anyone could deploy sounded more scalable. 


The only problem was that I'm not very good at programming. I know a little bit here and there to get by with my solo projects (mostly firmware), and I know a little about networking and infrastructure management—that's about it. Creating a full-fledged bot would require a lot of time and learning on my part. I wasn't willing to spend that much time on a pet project. 

So I relied on Claude (free plan because I'm broke) to create it. More on that later. 

After a weekend, I had a basic bot ready to be deployed. I even made a basic website—[www.whatsforlunch.lol](https://www.whatsforlunch.lol) 

### Infrastructure and operations costs

- The domain cost me 1.24 dollars or about 200 yen. 
- Website is hosted on GitHub pages for free. 
- Discord bot, n8n, PostgreSQL database and everything else is locally hosted on my janky homelab, costs maybe 200-300 yen a month in electricity bills. 
- Each API call costs me about 0.2 dollar or 32 yen. With 2 API calls per week, the monthly cost is about 256 yen. 
- In total, the monthly running cost is 556 yen - roughly equivalent to one and half meal ticket at the cafeteria. 

### Things change when it's not a solo project with one user anymore

If I made something for myself and it was down for some time, I would not care much unless it's something critical to my daily life. I would get around it whenever I felt like or when I actually needed to use it myself.

The Discord bot is not critical for anything. It broadcasts lunch menu, not life-and-death information. Even so, whenever it goes down, I feel a bit more pressured to fix it because I don't want someone to run a command only to find out it's down at the moment. I find it interesting, because I know it's not a big deal to others as well. Still, considering how this sort of counts as a community service, it should be maintained better than something I only use myself.

So far I am liking the pace of the project. It started as a basic n8n-based automation using webhooks to send messages to Discord. Now it is a minimalist Discord bot that only has one purpose: to send the menu to the server. People can also check the menu for the next day, but that's all about it. Honestly, I don't want to add too many features to it. Perhaps better to keep it lean and as minimalist as possible. 

Let's see where it goes. 

### Lastly, my thoughts on vibe coding

The term vibe coding has a stigma attached to it for good reasons. A lot of the people who are AI enthusiasts and heavily lean on it don't really know what they're doing. Sometimes they really do go off on vibes, and the end result often has many critical flaws. Again, I don't really know a lot about programming or software engineering in general, so these are the sentiments that I have seen on the internet. From my limited knowledge, I agree with them. 

Having all that said, I don't think this phenomenon was introduced by the AI boom. Before AI, people were copying snippets without understanding from Stack Overflow. *If it works, don't touch it.*

But one could not get very far with that. It's hard to build something complex entirely by piecing random snippets copied from the internet - without having some understanding of the basics. 

Except that is no longer true with the rise of LLMs. Now, anyone who has basic computer literacy and instruction following capabilities can build and deploy a software. Will it be something high quality? Probably not. Do they get the job done? Generally, yes. 

So, now we have people who are not necessarily technical be able to build software (among other things, of course). There's a pejorative term for them: AI slop.  

Honestly, I don't know what to think of this. 

On one hand, it puts a lot of power into the hand of people who may not be aware of the responsibilities that come with the power. A lot of people who use AI to bring their ideas into lives may have good intentions, but their concerning lack of understanding of what is under the hood and not being able to make it secure oftentimes cause unintended harm. Like OpenClaw for example. 

On the other hand, I know I would never dedicate enough efforts and time from my side to build this Discord bot entirely from scratch, had it not been sped run massively by Claude. 

Interesting times we live in. 




