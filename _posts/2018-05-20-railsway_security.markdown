---
layout: post
title:      "Rail(s)way Security"
date:       2018-05-20 22:56:58 -0400
permalink:  "railsway_security"
---

![Elevated Railway](https://i.imgur.com/2jaqwrJ.jpg)

I didn't quite get to the second part of Ruby inputs, but I promise I will get back to them and win at Ruby Track & Field.

So as I was going through tech training questions, I came across a little refresher in basic security. Equifax take note.

![Equifax](https://i.imgur.com/A8GJSce.jpg)

**CSRF and Security**

So Rails is pretty awesome. We all know that. But did you know it protects its own awesomeness against evildoers? It comes with tokens.

![Tokens](https://i.imgur.com/CN2guJ4.jpg)

Now the power of these tokens comes from web browsers' own "same origin" policy: scripts are allowed to interact with each other only if they came from the same origin (URI scheme, port, and host name). Basically it makes it so that a) we can still access the DOM but b)that access doesn't transfer across sites, preventing us from altering potentially sensitive data.

When an evildoer does this it's called Cross Site Request Forgery.

![Jack Nicholson](https://i.imgur.com/8MaYuxj.gif)

Adding `protect_site_from_forgery` in your ApplicationController (the module from which all your controllers should inherit) means that for Rails to make any POST, PATCH, or DELETE requests, it expects there to be a token.

How do you get one of these radical little tokens?

You clean your inputs and make your params strong.

![Shower Doggo](https://i.imgur.com/IoLXmeB.gif)

At the bottom of each of your controllers, in a private method area, you have to tell Rails to require certain params and permit certain inputs. For instance, `params.require(:credit).permit(:name, :amount)` requires params to have a credit key, that points to a hash of inputs. Of those inputs Rails only permits the use of the name and amount keys. Your views should have a corresponding `name` attribute for each input so that the data is correctly labeled.

That's it. Your data is sanitized and ready for use in your database.

Clean data = secure data = good data.
