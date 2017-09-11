---
layout: post
title:  "The Struggle of Gem Mining"
date:   2017-09-11 20:12:04 +0000
---


Whew. Long time, no write-y. I've been chipping away diligently at the CLI gem data project, writing some glorious code, and some real stinkburger code. For a month. And now I'm finally ready to turn it in. So the end. is. finally. here. 

![No Homer. Not near. Here.](https://imgur.com/zvnPSaf)

So in the spirit of wrapping things up, here's a brief summary of the app I built, from start to finish.

**A Need was the Seed**

So in my past life, I was laboring on a PhD in art history with an eye toward working in a museum. Alas, that was not, ultimately, what I wanted (see my first blog post for more info on that journey), but I still want to stay in touch with museum events.

Now, I've always seen code and tech as powerful tools to a) solve specific problems and address particular needs; and b) make the world a better place for all. And my desire to keep in touch with museum events and exhibitions presented a rather irritating obstacle: other than the so-called "blockbuster" exhibitions, it was sometimes difficult to know when either of these things were happening. Why museums bury this info, I'll never know. So I thought, "Gee, wouldn't it be great if there were an app that would allow users to simply access this sort of information? Or even send push notifications to my phone when certain events or exhibits are happening or ending? Wouldn't that just be great?"

![Low hanging fruit, guys, I know. ](https://imgur.com/FSxSRGL)

Well, after further discussion with one of my fellow art historians, I realized I wasn't the only one who had this problem. So that's when I decided that I would create an app to address the issue, at least for one museum: the Art Institute of Chicago.

**The AIC**

![The lions at the AIC are symbol of Chicago. Also, if you climb on them at night, they roar and call the police.](https://imgur.com/ofswBf7)

The Art Institute of Chicago, or AIC, is literally one of my favorite museums ever. It has a horde of late 19th century stuff, which was what I studied, as well as a beautifully re-installed arms and armor section, American masterpieces, and a wonderful new Modern wing. It's collections put it on par with d'Orsay in Paris and the Met in NYC. If you have a chance to go, go.

Ok. Museum plug over. I'm a member at the AIC, but don't use the perks of said membership nearly as often as I would like. I don't know what's going on there typically and find the process of looking for this info tiresome. I'm sure I'm not the only one. Plus, I fully believe that when people are empowered as users--when they are making demands and interacting--data automatically becomes more dynamic and people feel in charge. Now I'm no user experience expert, but hopefully this would translate to increased attendance at these events. So there was the kernel, the seed, of my app.

**The Beginnings: Architecture.**

The idea of what I wanted this app to do was fairly set out in my mind. I also knew who I imagined as the target user for such an app(mostly college educated, culturally and technologically aware adults ages 19-55--with and without children, with modest-to-ample financial means). Thus I knew from the beginning what kind of functionality was required. I began sketching.

I found the AIC pages I would need to scrape (thankfully, they are put together in a very linear, straight-forward fashion), and what I wanted users to be able to access as information. For example, if a user types "all", I wanted all events to display (a feature I also ended up limiting, because, let's face it, no one is going to peruse 800+ results). As I did this, I started to see Ruby objects: Events would clearly have to be one, Exhibitions, EventType (functioning much as the Genre class did in the Music Importer lab), a CLI class of course, and a general Info class. The scope--and future scope--of the project began to emerge and expand. And then I knew I was in for it. 

**The Middle aka The Process aka The Grind**

![Indeed.](https://media.giphy.com/media/OCu7zWojqFA1W/giphy.gif)

I actually had fun with the bulk of the code. Ruby is a great, intuitive language for first-time coders like myself, and each object really cemented many of the concepts already covered during the course, such as has-many/is-one relationships and working with the CLI class. Some of my initial classes proved to be unnecessary (I did not need an EventDate class, for instance), and I learned rather quickly error patterns and how (almost) to anticipate them.

Once in the flow of the code, I was *there*. Sure, I could've done more Git commits; sure, my refactoring needs work. But the satisfaction of getting one piece of code to fire was all it took; I was hooked. Until things broke. And I do mean *broke.*

**The Breaken-ing**

![I know the feeling](https://media.giphy.com/media/dcOEiSBI8Gxzi/giphy.gif)

So there I was, toolin' along, writing code, stumbling through GitHub and bundler, but all-and-all, getting things straightened out. When the Learn IDE suddenly stopped working. I mean, dead. Dunzo. Kaput. Didn't want to load any repo, much less my own.

I still don't know what happened. But I got online and chatted with several Flatiron folks, including one dev who works on the IDE, and we tried everything. Closing, opening. Uninstalling, re-installing. Logging out, logging in. Removing every vestige of the program, then installing the beta version of IDE 3. That version didn't work. Shout out to all the great people that sat with me through this and their patience. Mine was definitely wearing thin. I wanted to move forward. I had already spent somewhere in the neighborhood of 2 weeks on this thing, I was in the zone, and I wanted to push through.

So the only thing left to do was install a local environment using Atom. Now, thankfully the Flatiron folks had an easy-to-follow guide (although I didn't always understand what, exactly, I was doing). My consolation was that I knew that eventually I would have to install Atom or Sublime. Still, while it was happening, I felt like Ray up against Nedry's security shutdown. There was even compiling involved.

![I couldn't find the frickin' magic word](https://media.giphy.com/media/ZXIw1GQPMI7aU/giphy.gif)

**The End (and the future?)**

In the end, everything got set up: GitHub, Atom, my app. And unbeknownst to me, I was still at least 2 weeks away from finishing. But I pushed and pulled, learned to reuse previous user input and the value of a class counter (that was a huge dawn-dawn moment), installed the truly life-saving Chronic gem, and learned my lesson of paying attention to details while you code because going back and adding code for outliers, for example, can break a helluva lot of other business. Pry was invaluable. Terminal's weird antipathy towards copy-and-pasting drove me nuts. And every time I thought it worked well enough to proudly show my partner, he would break it almost instantly. 

But I enjoyed the struggle. So much so, that I would have probably kept going with this for a while longer if I could. And I want to return to this program, expand on it. The need it addresses is real; I'd totally download an app that sent me notifications about cultural instutitions of my choosing. There is sooooo much room for expansion. I would love to go back and add more code for taking care of the outliers that could occur everytime a user enters new input. But for the purposes of this course, the whistle had blown. I had to stop. Just like now. I have to stop. 

![See ya](https://media.giphy.com/media/26tk1RUHNm9zbdoXK/giphy.gif)






