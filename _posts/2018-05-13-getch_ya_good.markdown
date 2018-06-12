---
layout: post
title:      "Getch Ya Good"
date:       2018-05-06 22:56:58 -0400
permalink:  getch_ya_good
---

**PART ONE**

Ruby. Not Ruby on Rails but straight up command line Ruby. Sometimes I forget what it can do and what it "can't" do (I put this in quotes because it doesn't necessarily mean that Ruby *can't* do something; it's just I don't know if it *can*).

So the challenge for this month's ChicagoRuby Hack Night was to make a version of the 100-yard dash from the old video game Track & Field.

![Track & Field 100 Yard Dash](https://i.imgur.com/taFSN3S.png)

I've never played Track & Field, digital or otherwise. I was a drama kid with a Sega, not an athlete with an NES. But the goal of this hack was to create a CLI version of the 100-yard dash.

**Step 1: Create 100 dashes**

Actually underscores. You have to determine how and with what the viewer will interact. Your basic GUI. The gist of this game was not really a race, but a time trial. In other words, we're only looking to see how fast a user can press a single button or a combination of buttons to get her token to the end of the dashes (i.e. how long it takes for a user to press button/buttons 100 times).

So the start board is: x____________________________________________________________________________________________________

Basically the user token plus 100 underscores

So, we initialize our Dash class with an array-representation `race_track` and a `board` method to display that track as a series of underscores.

**Step 2: Decide what user input should be.**

Give the user instructions on how to win. They have to press x (we kept it simple, matching the token with the keypress) 100 times, then the game is over, and they get their time.

**Step 3: Grab that user input**

And this is where things got tricky: getting that user input. This actually took the bulk of our time to do because it meant digging back through some old friggin' Ruby.

**Aside: Musings on Old Stuff**

For posterity, let it be known that old stuff is tricky. Handle it with care. In any field. Coming from art history, old stuff can be great. You can get an idea of what people were thinking, what contemporary reception of an artwork was, and so on.

But there's a problem: people lie or at least aren't truthful. Shocking, right?

![Lego Batman Gasp](https://i.imgur.com/PzqF8T9.gif)

There was a time when academia wasn't striving towards being impartial (methodological debates aside). Generally speaking, we try at least take into account as many viewpoints as we can and go where the evidence leads us rather than funneling evidence to fit a preconceived theory.

Back in the day and outside the political theater, people jumped to conclusions, they puffed up their own theories at the expense of others, they were open (or closeted) propagandists, and they just straight up weren't as educated. So their stuff is useful. . . . to a degree.

![Abe Simpson Talking to Lisa](https://i.imgur.com/buZbz8v.gif)

Same as old stuff in Ruby. Sure, when I see that Stack Overflow date that's from 1999, I pretty much stop reading. But what happens when you Google something and *all* the results are from 1999?

Could be outdated and useless (usually is), or it could just be an old post about old code that still works. After all, Ruby 2.5.1 is still, well, Ruby, just as Ruby 1.95 was and is Ruby.

That brings us to inputs: I've always used `gets.strip` or `gets.chomp` (depending on if I need to to go down a line or not).

![Jurassic Park T-Rex Chomping Fries](https://i.imgur.com/6SIY6AO.gif)

Normally, this isn't a problem. The behavior for `gets` is basically to grab whatever value the user presses, show it in the command line, and wait for the user to press enter.

But this isn't the behavior I wanted: on every keypress, if that keypress is an x, move the x token one dash to the right (delete dash, replace with x), delete the previous x token, and repeat over and over without changing lines.

So I had to do some deep dives into Ruby inputs and pull `STDIN.getch`. This allows you to grab the input value without needing to press enter. And you do need to `require 'io/console'`

This, however, still didn't do exactly what I wanted. I ended up in a loop that repeated 100 times and redrew the board game every. single. time.

![X moving slowly across board game](https://i.imgur.com/Qd2yozF.png)

But I was on the right track (see that? See what I did there?)

![Jake from Adventure Time Laughing](https://i.imgur.com/WYoQTEL.gif)

STDIN--or Standard Input--was a revelation. It opened up a whole new way of getting input from the command line. But it still left me with a program that didn't do what I wanted.

So unless we rename the 100-yard dash 100-yard descent, more research into Ruby inputs remains to be done to get our token over that finish line.

**TO BE CONTINUED . . .**

![Jerry Seinfeld Crossing Finish Line](https://i.imgur.com/4fUNrPo.gif)
