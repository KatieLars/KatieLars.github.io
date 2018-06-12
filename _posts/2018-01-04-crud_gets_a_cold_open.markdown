---
layout: post
title:      "CRUD Gets a Cold Open"
date:       2018-01-04 20:35:58 -0500
permalink:  crud_gets_a_cold_open
---


You had CRUD in your kitchen, now there's CRUD in your freezer!

I'm not a terribly imaginative designer when it comes to apps; but I am terribly practical. I want my apps to answer real world problems and inconveniences with the most efficient and user-friendly functionality. It's just how I do.

So for my Sinatra project it was spices; this time it's freezers (ultimately I want to create a large app-- a Digital Pantry--that is comprised of several smaller pieces that manage and track the foods in a household or small commercial kitchen). Spices expire quicker than you think, and freezers aren't bullet-proof storage vessels. Clearly, they're better than the alternative (caves, holes) but they have flaws in them, such as temperature fluctuations and defrost cycles, which are compounded by folks' bad storage habits, like not vacuum sealing meat or leaving air in a container. Plus food just goes bad.

Cold Open is designed to prevent the mystery beige Tupperwares at the back of the freezer, or the glacier of ice on top of that T-bone by letting users know when their stuff is expiring and what they actually have in there. I mean, you never want to open up your freezer to the prospect of this:

![Zuul](https://i.imgur.com/h2luNq8.png)

Plus it saves money, food, and flavor! ;)

**The Process**

Everything fell into place for me this time around: the models seemed clearly related (finally feel solid about those AR associations); the forms nested snuggly together, and sessions were less of a hassle than with Sinatra.

Honestly, Rails was the magic everyone promised.

![I love magic](https://i.imgur.com/pHAzPNG.gif)

I used generators to get my models and migrations set up; the console to dive into my database (lack of access to the DB was a frequent source of frustration with Sinatra); wonderful class-scoped query methods and custom helpers to DRY out views; and some great gems to help with authentication. Routes, actions, views, partials, skinny controllers--it all clicked in a way that made Sinatra seem like such a struggle. I get it now.

I feel the love for Rails.

![Can you feel the love?](https://i.imgur.com/UQ5HEty.jpg)

**Sometimes when you move, the world moves with you**

In retrospect, I don't think my relative ease (relative to my Sinatra app, which drove me haywire) with Rails was entirely attributable to it's intrinsic magic. I think that a part of the magic <gulp> was inside me!

I *felt* much more comfortable with the process of wiring my models with associations. I *felt* much more comfortable dealing with validations (and I love Pundit--I'm a policymaker now). When I debugged, I *felt* much more competent in diagnosing the problem. I could trace the HTTP requests through my program, what they were hitting and where and why.

And although feelings are necessarily subjective, this one *felt* solid. This was the first app where I was in control of my code rather than just patching up functionality that had crumbled around the struts of my design. I got this. I felt like, well, a developer.

A things that unabashedly helped:


1. **Planning:** I took my sweet time on paper figuring out every. single. association, where my join tables were, whether some models needed to have associations at all (freezers don't have notes or need to know about item notes).

2. **Separation of Concerns:** I actively tried to incorporate principles into the act of coding, such as DRY and Demeter, but the one that aided me the most was the Separation of Concerns. I tried to ask myself every step of the way, what I was doing and what should be responsible for doing it. As good ol' Marky Aurelius wrote in Book Eleven, "Consider whence each thing is come, and of what it consists, and into what it changes, and what kind of a thing it will be when it has changed, and that it will sustain no harm." Indeed.  
![Marcus Aurelius](https://i.imgur.com/xPcRi1D.jpg)

3. **Prior knowledge:** I can't quite put my finger on it, but by building up to Rails through SQL, ActiveRecord, Sinatra, Ruby and the like Rails' magic was actually less mindboggling. Simply put, it was the next logical step (although Devise--another, perhaps, logical step--is not my friend). It's like how Chicago is the Second City: a chunk of it burned down, and now, secretly (or not), all the ritzy apartment buildings between Michigan Avenue and Lake Michigan are just built on top of ashes. My Sinatra app difficulties are the ashes, and the shining towers of Rails stand atop them.

4. **Pushing it:** Perhaps due to this comfort level and greater control over the app (although my CSS is definitely in need of work), I decided to do a mock run at a more professional sort of development. I created a separate Git branch called 'development' (yes, I know it should have been 'develop') which was where I worked until the final version was ready. I created unit tests for my model classes. It may have taken me a couple of extra days to do so, but it was great to be able to run those tests to know if my models were wired incorrectly (which I did even on the very last day).


**The Leftovers**

![Leftovers](https://i.imgur.com/w7cDHL2.jpg)

What's left is basic deployment and CSS. I'd like to say I have a wonderful Heroku app link like I did for my Sinatra app, but alas, I do not (as of this writing, the JavaScript portion of this app looms, so I will wait until that is ready to deploy). So that's left to do. Oh goody.

And then there is the front-end. Once I loved CSS. Now I do not particularly care for CSS. It brings back all the struggles with Microsoft Word formatting I went through as an academic. I think Word literally owes me a year of my life back for how much I struggled with all the weird formatting rules they implemented when they updated to 2007 (Calibri? Why? What was wrong with Times New Roman?).

Javascript is up next. The party in the back I guess has to be followed by the business in the front.

![Mullet](https://i.imgur.com/zm6ZTXv.jpg)
