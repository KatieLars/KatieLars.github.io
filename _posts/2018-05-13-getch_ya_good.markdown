---
layout: post
title:      "Getch Ya Good"
date:       2018-05-06 22:56:58 -0400
permalink:  getch_ya_good
---

Ruby. Not Ruby on Rails but straight up command line Ruby. Sometimes I forget what it can do and what it "can't" (I put this in quotes because it doesn't necessarily mean that Ruby can't do something; it's just I don't know if it can).

So the challenge for this month's ChicagoRuby Hack Night was to make a version of the 100-yard dash from the old video game Track & Field.

![Track & Field 100 Yard Dash](https://i.imgur.com/taFSN3S.png)

I've never played Track & Field, digital or otherwise. I was a drama kid with a Sega and not a NES. But the goal of this hack was to create a CLI version of the 100 yard dash.

Step 1: Create 100  . . . dashes

Actually underscores. You have to determine how and with what the viewer will interact. The basic gist of this game was not really a race, but a time trial. In other words, we're only looking to see how fast a user can press a single button or a combination of buttons to get her token to the end of the dashes (i.e. how long it takes for a viewer to press button/buttons 100 times).

So the board is: x____________________________________________________________________________________________________

Basically user token plus 100 underscores

Step 2: Decide what user input should be.

Give the user instructions on how to win. They have to press x (we kept it simple, aligning the token with the keypress) 100 times, then the game is over, and they get their time.

Step 3: Grab that user input

And this is where things got tricky: getting that user input. This actually took the bulk of our time to do because it meant digging back through some old. friggin. Ruby.

Lesson: Old stuff is a double edged sword. In any field. Coming from art history, old stuff can be great. You can get an idea of what people were thinking, what contemporary reception of a piece was, and so on. But there's a problem: people lie or at least aren't truthful.

There was a time when academia wasn't striving towards being impartial (and there are methodological debates about the role of impartiality, whether it's even possible to be impartial, whether we should even strive to be impartial, etc.). Generally speaking, we try at least take in as many viewpoints and go where the evidence leads us regarding artworks than establishing a view and very narrowly channeling the evidence towards that view.

Back in the day and outside the political theater, people jumped to conclusions, they puffed up their own theories at the expense of others, they were open (or closested) propagandists, and they just straight up weren't as educated. So their stuff is useful . . . . to a degree.

Same as stuff in Ruby. Sure, when I see that Stack Overflow date that's from 1999, I pretty much stop reading. But what happens when you Google something and *all* the results are from 1999?

Could be outdated and useless (usually is), or it could just be an old post about old code that still exists. After all, Ruby 5 is still, well, Ruby, just as Ruby 1.95 was and is Ruby.

That brings us to inputs: in Ruby CLI, I've always used gets.strip or gets.chomp (depending on if I need to to go down a line or not).

Normally, this isn't a problem. The behaviour for gets is basically to grab whatever value the user presses, show it in the command line, and wait for the user to press enter.

But this isn't the behavior I wanted: 
