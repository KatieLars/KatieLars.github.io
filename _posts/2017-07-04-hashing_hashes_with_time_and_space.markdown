---
layout: post
title:      "Hashing Hashes with Time & Space"
date:       2017-07-03 21:06:34 -0400
permalink:  hashing_hashes_with_time_and_space
---

![Hash Browns](http://i.imgur.com/0FWkzpm.jpg)

Because no one has made that joke before.

But beyond the dance of the salt pork fairies, hashes, it turns out, are a great way to store information. They're intuitive: you have a keyword conceptually related to a value; they are good at handling unique information: keywords are one-of-a-kind to access particular information; and, as key/value pairs inhabit no particular location inside the hash, they are more fluid than arrays at organizing information. The information contained in hashes isn't nailed down.

Problem is, there are times when I need things nailed down.

Put visually, sometimes this:

![wasps pinned to board](http://i.imgur.com/8zHAYGq.jpg)

is better than this:

![swarm of bees](https://media.giphy.com/media/Z1zd9yQlbkaCQ/giphy.gif)

See the problem I found with hashes was trying to set values equal to any one constant key/value pair. In other words, I needed an initial value equal to the first key/value set that appears in the hash (of course, choosing the first pair is completely random since pairs don't have a strict order within a hash). If the data set were an array, I would simply say array_name[0] to access the data at that unique location. But location (i.e. order) is not the unique part of a hash; keys are.

![Cinderella Gus trying to get key](http://i.imgur.com/H3oXwA9.jpg)

So when I was confronted with the challenge of comparing integer values in a hash against each other, and then having my method return the key for the smallest value in the hash, it was difficult to get a toe hold. How could I set a variable to an initial value when I a) didn't know the key to that value (because we wanted the method to be as abstract as possible so it could act over *any* hash) and b) couldn't pick a specific key/value pair because there are no unique locations (i.e. indices) in hashes.

Here's an actual image of me, trying to figure this out:

![man fighting swarm](https://media.giphy.com/media/A1SNSC8s40O64/giphy.gif)

Turns out, I was thinking about location in the wrong way, or rather, not in a useful way. I did have to do a screen share with Flatiron pro Matt Cassara to figure this out, so credit is his on this one. I'm just pleased I understood what was happening.

You see, my conversation with Matt revealed that there is another way (not index, not key) to establish a unique identity: time. If you're iterating over a hash, pinpointing a "location" (i.e. key/value pair) can be a matter of time. It's what allows you to set a counter. And a counter is an important piece of this, for this counts each time that you iterate over the hash, and of course, each of those iterations (or times) is unique. So that count in turn becomes unique.

![mind blown](http://i.imgur.com/r86rI5l.jpg)

So to set my initial values for comparison, to pin them down, I (with Matt's help) wrote this:
```
  if counter == 0
    lowest_key = key
    lowest_value = value
  end
```  

So at the first iteration (0), two variables (`lowest_key` and `lowest_value`) are set to that iteration's corresponding key/value pair (in this case, the key/value pair that appears first in the hash).

Now, I'm like

![Oprah loves bees](https://media.giphy.com/media/VhFps32TlNgsg/giphy.gif)

Of course, all of this would've been moot had I just been allowed to use `min` . . . But wasn't it so much more fun to work in the space/time continuum of iterations???

**WASN'T IT?? WASN'T IT??**

![SNL Kristen Wiig](https://media.giphy.com/media/l2JhAmuESLx73WWbK/giphy.gif)
