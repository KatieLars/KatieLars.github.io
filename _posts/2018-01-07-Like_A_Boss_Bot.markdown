---
layout: post
title:      "Like a Boss (Bot)"
date:       2018-07-01 20:35:58 -0500
permalink:  like_a_boss_bot
---
New framework, increased visibility, enhanced personal joy--my Souls Borne Boss Bot covers it all.

[IMAGE DARK SOULS]

**New Tech: Node.js**

So I've been looking to expand into new languages, frameworks, and tech in general, so when starting a new project, it was obvious I had to go beyond Ruby/Redux/React/Sinatra/jQuery, etc. etc. I had to learn something new.

Node.js has popped up a couple of times in my job search: servers for code challenges have used Node, talks at meetups have been about Node, people have said "Node", whatever. So Node was there, lurking in the back of my mind.

[IMAGE LURKER]

But tech should always fit its function. In other words, the question became, is Node a good fit for this project? Answer: yes.

Node is like a little client-side server. It's focused on runtime events, rather than inputs and outputs. That's not to say that there none of these things, but rather it's primary purpose is to do stuff. It's not a database or ORM (although it can certainly handle data); it's good for frameworks, but not particularly concerned with UI; and it's good at doing nothing when nothing is needed to be done.

So if your app is a verb--tweeting, say--Node might be a pretty good choice for it.

[IMAGE NOD]

**Learning about Learning**

I'll admit it: I was in a bit of hurry getting this thing up as I wanted a codeditty (a code ditty--small, fun nearly pointless app) to add to my portfolio.

This was my first time learning on my own without the help of a straight up course or tutorial (there wasn't one tutorial that did everything I wanted my bot to do). So here's what I learned about learning:

**First: Reverse Engineering Stuff Is Hard**

I started with the following tutorial: https://community.risingstack.com/node-js-twitter-bot-tutorial/. It was great. I set all my variables, installed my libraries, and saw the basic structure. I was up! Were the tutorial failed, the Twitter API docs stepped in, and I was able to tweet `Look, I'm Tweeting!`

But there were some problems: it assumed I wasn't using GitHub, so there was no protecting API Keys/Secrets; it was focused on passing around callbacks--basically chaining events, with very little hard `returns`; it wasn't making any original tweets, just retweeting and favoriting other tweets.

But I could follow the flow of events, and see what each line of code was doing. I installed the dotenv library, added a .gitignore, set my constants, and `process.env`ed where need be.

Then I came to the Google Sheets API. OMG. This was where the real reverse engineering pain was felt.

The Node.js docs for using the Google Sheets API were pretty good, but didn't go through their code sample line by line, so it was hard to decipher what, exactly, was happening. For instance, I had to get a token from an OAuth2Client, which is fine. Pretty standard. But they started their code with `const TOKEN_PATH = "credentials.json"`. Where or what the hell was `credentials.json`? It wasn't a pre-established variable. It wasn't a file the sample tutorial had asked me to create (like it did when I exported my credentials from the developer console). So what the heck was it?

[IMAGE WHAT IS THAT]

Turns out, it's a file created once you get the token. Once I had completed the authentication process, *poof* it appeared and the dawn-dawn moment in my brain happened.

It was real slick: `TOKEN_PATH` was being set to a string, that eventually got used as a token holder. IT WOULD HAVE BEEN NICE TO KNOW THIS BEFORE HAND. But I guess I'm just a beginner, so I can't be a chooser. Wait. That's not how that saying goes. . . .

Lesson is: figuring out someone else's less-than-perfectly-explained code is rough. Then, since I was using dotenv, rather than the `client_secrets.json` file they wanted me to use, I had to take a hard look at how they were setting their credentials and adjust that code accordingly. And I think my code was much, much cleaner than their business. But whatever.

**Second: Good Documentation and Comments are Gold**

That was another takeaway from reverse engineering. And it's been my takeaway before (see my entry DEPLOYMENT OR BEST TUTORIALS)

[IMAGE GOOD DOCS]

**Third: `console.log` is Your Friend**

I've never been a big debugger with `console.log`. In fact, I never really even use it unless I'm using someone else's code. And here I was basing my bot on a tutorial code. So for error catching, which is not my forte, I let the `console.log`s hang out. AND THEY WERE GREAT!

So useful. Debugging in Node.js is kinda weird (it wasn't stopping at my debugger, but rather, you have to tell it to listen for a debugger. It's only a reserved word if you want it to be). So for this simple little bot which would only need Google API authentication about twice a year(tokens last 6 months), `console.log` was great for looking at the value of variables and the minor debugging I had to do.

In a framework dominated by events and not outputs, `console.log` was a godsend to getting some output, any output, in this process. By placing them strategically throughout the codebase, I could see what my code was doing and when it was doing it.

So, I made a new friend.

[IMAGE NEW FRIEND]

**Fourth: Always More**

And this is just the beginning. List of other things to build out:
  ~State. Knowing which bosses have been tweeted already would be good. I don't want people to see Pinwheel forever. Cuz that boss be dumb.

[IMAGE PINWHEEL]

  ~Retweet. I want the bot to retweet everything with #DarkSouls or #SoulsBorne or #ShadowsDieTwice or #Sekiro as From builds up to a new epic release.

  ~More Bosses. This one's one me. I started with a very basic database of bosses for Dark Souls Prepare To Die edition. Now I need to add Demon Souls, Dark Souls 2, Dark Souls 3, and Bloodborne. But this is on me.

So check out my code at GITHUB LINK and follow ATBOSSBOT for all your Souls Borne love. Because god, gleepglops unite, I love a good Souls Borne Boss.
