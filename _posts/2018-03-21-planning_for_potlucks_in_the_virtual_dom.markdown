---
layout: post
title:      "Planning for Potlucks in the Virtual DOM"
date:       2018-03-21 04:32:06 +0000
permalink:  planning_for_potlucks_in_the_virtual_dom
---

It's party time.

![Party Cat](https://i.imgur.com/YorPdUF.gif)

Or more like *potluck* time.

![Snoop Dogg and Martha Stewart's Potluck Dinner Party](https://i.imgur.com/H1LbweG.gif)

After over 3 weeks of struggle, one false start, at least two CSS nightmares of epic proportions, and several deep dives into YouTube tutorials (thank the Maker for those), my last project for the Flatiron School is complete. I'm not going to lie: I cried, I screamed, and I think I twisted my brains into some new loops, but it's done. And it looks pretty damn good.

![Potluck Planner About Page](https://i.imgur.com/mYqFfZR.png)

Oh. So. Pretty. 

Oh. The. Pain.

The past few projects (three actually) were cakewalks compared to this one; and the one before that was my first foray into code. So it got me thinking: why did this take so long? What made this project tear my hair out?

Certainly a part of it was the rate at which I moved through the material: I burned through it in about a week. But that rate was no greater than that at which I had gone through Javascript and jQuery, and that project only took me about three days. Besides, conceptually the majority of the lessons made sense. 

There was one warning sign: I was frequently on with technical coaches for help with labs . . . and just as frequently multiple coaches would have to work through the problems with me because the first coach was stumped. Now, I don't mean to impugn the technical coaches; they were incredibly patient and super engaged with the material. Without them, I wouldn't have learned half as much as I did. No, there was something else going on . . . 

The compiler? Working with a compiler is a pain. I'm sure there are strong advocates for compilers, and I know I will always associate them with Dennis Nedry, so maybe I'm biased, but when the compiler starts, that's when the bugs start crawling out my code's proverbial woodwork. 

![Roach on Fan](https://i.imgur.com/CxkoWg8.gif)

Plus it takes forever for the tests to run and the server to start. Woof. I do not care for compilers. But I think it points in the right direction: code written by a third party that trends toward opaque is just that: opaque. Automation and new-fangled architecture is great, but unless you are on board for its creation, it's hard to debug or get working. "Easy" becomes a relative term. If you happen to think like the creators or have a simple demo app, the architecture is easy. Trying to come at it from another perspective and do something a little more complex, and "easy" becomes "hard".

![Adventure Time Jake failing at starting a fire](https://i.imgur.com/kwC2wP9.gif)

Pretty much.

But that's what being a coder is; using new tech, taking on legacy code, jumping into someone else's head, and pushing things one step further. So what can I do to prevent the mind explosion of the past few weeks?

**1. Write Your Ideal Code**

I had momentarily forgotten this tenet, but if you're going to control the code rather than vice versa, this is essential. If you write exactly what you need your code to do in the best, most explicit, simplest terms, and flesh it out, you're making the code work for you, rather than just dealing with what some other piece of code poops out. And I don't know about you, but I don't take s . . . *poop*.

**2. Plan Smart**

This was an app heavy on client-side functionality. So I thought, well, I'll start with user functionality and work back from there. That seems smart. And it was. Partially. 

Yes, you need to know what you want your app to do. But thinking about UI can only get you so far. After all, I could adapt the UI from my Rails/jQuery app to React-Redux and have it come pretty close in terms of user interactions. But using React-Redux gives you a different--and at times, better--way to think about *how* that user interaction is created. I had to stop thinking primarily in terms of objects and more in terms of components. 

I believe that if I had planned smarter--looked at the functionality in terms of components and state--I would have got through this with less frustration. Or at least less freaking out.

![psychadelic brain](https://i.imgur.com/yiEb9Wq.gif)

**3. Information: what do you have and what do you need**

Know your serializer. It's your friend. You're not obliged to have all the attributes associated with model. For instance, do you really need that datetime object? This is client-side. Are you really going to just display all that gobbledygook in your component? Or do you need that business formatted? 

Use your serializer to create custom methods that format information (like dates) or sort it using the methods you create in your models. For example: if you need all the guests of a potluck that aren't going, simply make a method in your potluck serializer that calls an instance method in the Potluck class that filters out those guests that rsvped "not going". Which leads me to . . .

**4. Single Responsibility is Queen**

Manipulating data? Keep that functionality in the models of your database. Fetching data? Leave that to your API calls and controllers. Each bit has its own purpose. These are the easy ones. There are tougher, custom ones. 

If you plan correctly, you might see that you have a modal that keeps populating lists. Factor that modal out. It's presentational and doesn't control logic. That makes it reusable. It has one function: display lists. Other components can fuss with the details.

**5. Beware conditionals**

I love conditionals. They give us so much great functionality. But too many of them in the same file, and your code becomes brittle, difficult to read, and hard to debug for both you and anyone else whose woe it is to work on your code. 

Refactor them away. Chances are, they can be repackaged as components controlling specific types of data. This may make them seem more specific and less versatile, but if you think about it, two components in place of two complicated conditionals in one function can do the same stuff. But the two components are probably easier to read, more reliable (they ultimately are responsible for less code), potentially more reusable (since they are responsible for less), and don't have any detrimental impact on overall functionality. Less, in this case, is more.

Besides scrolling sucks. It's hard to remember the code that's availble in the same file if you don't have it all at a glance. It's cumbersome. And it's not like reading a book; it doesn't go from left to right, top to bottom. It just gets hairy.

![werewolf](https://i.imgur.com/HoJ558h.gif)

And that is where I leave of. The last project done. The next page turned. I have no doubt I will be coming back to these projects--the ideas are good, and I want to do more. But for now, it's time emerge from my code den. It's spring time, and my code wasn't the only thing getting hairy.






