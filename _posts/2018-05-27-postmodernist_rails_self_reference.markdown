---
layout: post
title:      "Postmodernist Rails: Self-Reference"
date:       2018-05-27 22:56:58 -0400
permalink:  "postmodernist_rails_self_reference"
---

"That postmodernism is undefinable is a truism."

Exactly how I would have put it. Thank you, Stanford Dictionary of Philosophy. How ever did you know?

Postmodernism clumps disparate groups of thought and practice together into this undefinable mass of *stuff*. Roughly speaking, it's a historical philosophical backlash against the unity of meaning, the goal of consensus in thought, and the general structuralism that defined French philosophical discourse in particular. We're talking late '60s and '70s, here, a time coincidentally of great social upheaval. It's about simulacra, excess, difference, performative knowledge, etc. It's about revealing the essentially constructed nature of thought and society, how we produce our reality, and calls into question the nature of legitimacy. Got that?

Yeah. It's glorious and tough and full of arrogant white dudes.

![Rosie Perez Eye Roll](https://i.imgur.com/w3n3T1S.gif)

I'm getting to Rails, trust me.

But what it did was reveal how our world is really defined by us. Even the absences--all the Derridean *différance*--are really just us, the modern subject (or so Habermas says in his *The Philosophical Discourse of Modernity*). We can never escape us; we can never escape ourselves.

So here we are again with echoes of 1968 bouncing off our historical walls and social media dominating the discourse.

![Students in Paris 1968](https://i.imgur.com/BPxiQ66.jpg)

Of course, social media apps are standard these days. We just spend our personal data like it's fliff night forever as long as we get to continue playing Farmville with our friends. Needless to say, I wanted to make one of these social media apps. And I did: The Potluck Planner.

![Screenshot of Potluck Planner](https://i.imgur.com/mYqFfZR.png)

This is basically Facebook's Events functionality combined with a tracker for who's bringing what (so you don't end up with a bunch of potato salad and no hamburgers). Users can friend other users and then invite them to their potluck.

So how did I do that? Self-Referentiality.

![Vache qui rit](https://i.imgur.com/3xhE2e5.gif)

Basically self-referentiality describes the relationship between a model and itself. In this case, the User model. Because friends are also users, Users has to reference itself.

Here's how you do it:

**Database**   


1. Create a users table like you normally would with your `password_digest`, username, email, etc.

2. Create a join table called "friendships" (or whatever best describes the relationship between different users--frenemyships, parenthoods, whatever). This table will have a `user_id` and a `friend_id` as values. Each unique `friendship_id` describes that relationship. For example, if I'm friends with Joe, that one friendship will have an id to identify it (e.g. the Katie-Joe friendship has `friendship_id` 543).


  **Models**  


1. Create a Friendship and User model. Remember, the term "friend" just describes a type of User. We don't have a friend table.

2. User: Now a user `has_many :friendships`, but what we actually want to use is something like `katie.friends`, which should return a bunch of User objects associated to the user represented by the variable `katie`. So, we add `has_many :friends, through: :friendships`. Now ActiveRecord knows to look for `friend_id` as a column in friendships.

3. Friendship: Each friendship `belongs_to :user`. That's the easy part. But we have to let the Friendship model know where to look for the `friend_id` (because we don't have a model called Friend, because friends are actually just fellow users). So you must include: `belongs_to :friend, :class_name => "User"`. Now it knows `friend_id` is really just another name for `user_id`.


  And that's it. You're wired. You tired?

  ![Shark Jumping](https://i.imgur.com/zb7lfOt.gif)

  Let's get to the point. Which is this: in this current age of social media, where Cambridge Analytica and Facebook sway entire elections of nation states, where people fight with bots on Twitter, and we feel lonelier and more divided than ever, it is perhaps not coincidental that the model for all of this is self-referentiality. To make social media, you use self-reference. Users refer back to themselves. We revolve around our own online subjecthood that establishes relationships with people who are, for all intents and purposes, the same set of data points as us.

  This is the age of social media, the era of self-referentiality, the post-truth period, the acme of postmodernism. We're at the eye of this socio-philosophical storm.

  ![Eye of Hurricane](https://i.imgur.com/LP5FqNI.gif)

  Code Help Us, let's get through this.
