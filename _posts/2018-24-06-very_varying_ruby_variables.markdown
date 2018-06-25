---
layout: post
title:      "Very Varying Ruby Variables"
date:       2018-06-24 20:35:58 -0500
permalink:  very_varying_ruby_variables
---
A series of thoughts on Ruby variables.

I like variables. They can store complex chunks of data, functions, links, small animals, and general splendoorz.

![Wishmaster](https://i.imgur.com/iUzNAck.gif)

They have different scopes that allow that information to be as generalized or specific as I need it to be in space(i.e. objects) and time(i.e. methods).

![Nebula](https://i.imgur.com/j5x4WxP.gif)

On a recent code challenge, I thought I was being super clever by using `token.send(color)` to basically turn a string--represented by the local variable `color`--into a method that operates on a separate local variable `token` via `send`. It's a neat trick.

So I thought, "There must be a way to do turn a string into a local variable." Indeed, there came a moment when I needed to dynamically produce a bunch of local variables and set them to a bunch of new objects. Something like having a local variable, let's call it 'num', generate a bunch of other local variables like this `"player_#{num}"` and have these equal to a bunch of new Player instances. So in the end, there is a `player_1`, a `player_2`, a `player_3` etc.

![Ready Player One](https://i.imgur.com/k26aDKb.gif)

Now had I been dealing with an instance variable, this would have been fine. I could have used `instance_variable_set("@player_#{num}", Player.new)` and boom, I would have had a new instance variable for, say, `@player_1`.

But I had to keep it local. I wasn't dealing with an instance, just something inside a method, so the scope really didn't need to be any larger than that.

Turns out: there is no way to do this with local variables. Sure, there was `binding.local_variable_set`, but this posed a few problems:

First, I didn't want to have to set it to a value immediately. The value would be changing based on a conditional statement in a subsequent part of the method. So while there would always be a `player_1`, that value would be contingent upon other factors being fulfilled.

Second, it doesn't appear to have a repeatable effect . . .

![Seth Meyers Shrug](https://i.imgur.com/qgd3vJm.gif)

Like `binding.local_variable_set(:foo, "bar")` will return `"bar"`. It is essentially the same as `eval`: it evaluates the expression, and so, of course, returns `"bar"`. But type `foo`, and an error message for an undefined variable pops up. As Louise Linton says, LOLOLOL.

![Louise Linton Mean Facebook Quote](https://i.imgur.com/ynV8k0g.jpg)

So how did I get around this: turns out, I didn't need this sort of functionality in the end. My methods were refactored and the need vanished.

Some other folks had suggested using hashes to store the information, which would make sense if I already knew the values I wanted. But I didn't. I had to go through some conditional statements first. Arrays came up as well. The underlying problem was that I wasn't storing the data in the correct structure. But the data hadn't been generated yet . . .

So this story doesn't have a happy ending. Turns out there is no way to do this with Ruby without some sort of monkey patch, which is an absolute nope for me.

I guess I can only conclude by saying Ruby variables very much vary.

Oh, and LOLOLOLOLOLOLOLOLOLOLOLOLOLOLOLOLOLOLOLOL.

![Louise Linton and Steve Mnuchin](https://i.imgur.com/ccdrIaw.jpg)
