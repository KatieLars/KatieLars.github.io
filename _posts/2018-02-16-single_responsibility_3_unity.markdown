---
layout: post
title:      "Single Responsibility <3 Unity "
date:       2018-02-17 04:52:50 +0000
permalink:  single_responsibility_3_unity
---

The business in the front and the party in the back must work together. Albeit with programming, it's usually a party in the front and business in the back. Which is much better looking than a mullet.

![Reverse Mullet on the Runway](https://i.imgur.com/C2sG65l.jpg)

Whatever metaphor you chose, that a program's front end and back end must work together goes without saying; when one end is broken, users will miss out on the inherent awesomeness of the other. An ugly Angelfire-era front end, and users will likely stop checking out the amazing functionality of the back end. Buggy back ends, and a person can't even become a user--there's nothing there to even use. And so you get the collective shrug ("Eh. Whatever. There's lots of other rad apps out there"); the collective scream ("Why won't this bleepin' thing work?!"); or the collective siren ("SECURITY BREACH! SECURITY BREACH!"). All are potential death knells for your app, and the latter, potentially the death knell for so much more.

![Lego man destroys computer](https://i.imgur.com/7NjztoI.gif)

So save your users the frustration and potentially life-altering problems of a failed app or website and get your code good and running before living beings attempt to use it. Easier said than done in some cases. Refactoring is tough. Refactoring legacy code is tougher.

Now what I did with my Cold Open app (refactor some of the functionality of a simple Rails CRUD app into Javascript/jQuery) is not truly working on legacy code (I suppose that depends on how long it takes to establish a legacy). But it is taking an existing code base, front end and back end, translating it into another language, updating it, making improvements, and expecting everything to be copacetic. In the process, I learned a few things about clean code.

**More code = more broken code**

As a rule in life, I generally tiptoe around the "less is more" axiom. Baroque art appeals to me more than Neoclassical; I'd rather eat steak, potatoes, and scallops instead of just steak and potatoes; I like more clothes in my closet rather than fewer. Sometimes more is more. And (sometimes) it's better.

Not that I try to enact this "more is more" theory in every facet of my life, and I definitely don't purposefully try to do it with code. But refactoring with JavaScript has made the problems with "more is more" even more salient. I found that one more line of code means one more line of code to break; one more line of code that breaks other lines of code in surprising ways; and one more line of code I have to check when I change or add subsequent/related lines of code. The smaller and more clever my code base, the easier my life is. Plus . . .

![Clutter Obscures Elegance](https://i.imgur.com/jnJL3Ye.gif)

**If you have to manipulate a return value, think about why you got that return value in the first place**

But I noticed a few things, psychologically, about how I code. My original Rails code was pretty tight. It did exactly what it needed to do with no serious frills attached. And the whole time I was coding it, I felt like I was in charge of the code, rather than just twisting its output around to manipulate and mold it into what I needed. I was one with the code.

Contrast this with my first Ruby CLI scraping project, where the code was not so tight. In fact, that's a project I would definitely like to refactor to make it tighter. Granted that was my first code project ever, but I knew from that experience that the way I was coding was just taking what I got from an original function and forcing it to give me the result I desired--which led to a lot of extra code. And a lot of extra bugs.

![Bug ho-down](https://i.imgur.com/Bwte04q.gif)

I did notice that this type of "coding behavior" as it were was distinctly tied to front end development. I was trying get an acceptable looking result for the user no matter the cost to my code. Takeaway: I need to be a better front end coder.  I am still learning to recognize patterns and fixes for these patterns. It's a work in progress. But at least I'm a learning work in progress, and I did discover one big fix . . .

**Compartmentalize your code**

You don't need one function to do everything. In fact, one function shouldn't do everything. Place large chunks of code--especially HTML that you might need to spit out later--into smaller functions with pithy, to-the-point names like, `showNoteForm`. This has so many, many advantages: debugging is easier--you only have to fix things once even if you use a chunk of code multiple times; these smaller helper functions make your main functions easier to read--you can clearly tell what your larger function is handling; and finally, these helper functions serve as a tool chest for future functions--need to spit out a new form for something? There's a function for that. Plus compartmentalizing has a psychological effect: you are in charge of your code now. Cat is in the box.

![Cat being boxed up](https://i.imgur.com/7rgBNRf.gif)

**Single Responsibility leads to unity**

This principle of single responsibility--one function does one thing and returns a controlled value--is a lynch pin. I was able (at least in several instances) to check myself, and say "Ok. I'm adding another line of code here. Why? Can I separate this functionality elsewhere?". I also began to recognize when code was getting repetitive--do I really need to regenerate that form or can I isolate it into a function and just use that function?" One function, one goal.

It's definitely not perfect: I want to refactor certain functions into a JavaScript Item class; I want to distill my buttons and their corresponding event handlers (the constant struggle of attaching event handlers to dynamically generated HTML was a huge issue) into a single function that for every time it's called, creates the button, appends it to the DOM, and brings in the necessary event listener. So refactoring is definitely in the cards for me. Now back to the main thrust.

Single Responsibility leads to a more harmonious front end and back end experience: one bug can still crash the whole production, but because it's been isolated, it doesn't have to. And it can be more readily fixed. Each singly responsible function unit works toward the end goal of the app.

So now I know--and not just know know, but know in that kind of lived-experience sort of way--of my own psychological (and logical) ticks and the principles behind beautiful code.  It will take time to undo the habit of adding more lines to manipulate return values. But I'm in it to be a better coder. I'll get there. You might even say, that at this moment, in this context, it's my single responsibility.

![Obama Long March To Progress](https://i.imgur.com/VjwyVaX.gif)
