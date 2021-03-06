---
layout: post
title:      "Spicing up Sinatra"
date:       2017-11-10 17:26:10 -0500
permalink:  spicing_up_sinatra
---


I don't believe in CRUD, except when I'm in the kitchen!

![Nope](https://i.imgur.com/Qh21yee.jpg)

But I do always try to think of my apps as answers to real world problems. My CLI gem was a test run at getting updates (and in my dreams, push notification) of museum exhibition and event information. This Sinatra app is designed to keep track of spices and the recipes to which they belong. Now in my mind, I have a beautiful app that links to a variety of other cooking apps and blogs--it includes herbs,has ping notifications when spices expire or when you put a recipe on your menu and don't have one of the spices on the list, etc. For the moment I got none of that. It doesn't even look that great on the front end. But it works!

![It's alive](https://media.giphy.com/media/3oEjI6hkw6nbYNQkz6/giphy.gif)

It signs you up, logs you in, adds spices(and/or recipes), edits spices(and/or recipes), deletes spices (and/or . . . you get it), and links spices with recipes. Basic CRUD stuff.

As with any project, along the way I hit multiple snags. Admittedly, the snags are still not very pretty. But it works. And I like things that work. I'm actually looking forward to doing some refactoring to make them look pretty, because I do feel as though there are perhaps some issues with my understanding of ActiveRecord associations that are not at 100% and a better understanding would make the code a lot more palatable.

So here were the snags:

![Snags](https://i.imgur.com/zrbmmdt.jpg)

**Params and Object Creation**

So you're going to add a spice to your rack. Here's your form:

![Add spice form](https://i.imgur.com/NrzN8Fx.png)

As you can see, one can also add a new recipe or--using nested forms--choose from pre-existing recipes. I did have validations in place and flash warnings enacted should one fail to, say, enter a spice name, which is required in my model. But the problem was if any of the params were empty--say, you wanted to simply create a spice but not associate it with any recipe, new or old--the params with user data regarding recipe creation and lookup would be blank. Only thing is, when they were connected back to the post route, they weren't *really* blank. Meaning, if the user did not enter a new recipe or select an old one, ActiveRecord would still create a new recipe with a blank name (in which case my code would break to a validation I had set in the Recipe model) or attempt to update the spice's recipes with . . . .nothing (in which case, my code would break again).

It drove me crazy.

![Gordon Ramsay](https://media.giphy.com/media/26ueYXr2bONg1Y8ms/giphy.gif)

So my `post '/spices/new'` ended up being HUGE. I mean, I methodically went through and wrote out a conditional for each and every possible scenario: is the user the current user, are the spice params empty, are the recipe params empty, do the spice params have a recipe id associated with them, and so on and so forth. It's big.It's messy. BUT IT WORKS.

As I write this, I think there is a way to organize my params a little better and create some helper methods that would rectify this problem. Perhaps if I had created a params organization that was more along the lines of `{spice => {:name => "Curry", :flavor_id => "2", :recipe_ids => [ "2", "3"], :recipe => {:name => "Daal", :url => "daal.com"}}`

That way if `:recipe` were ever blank because the user didn't actually want to create an associated recipe, the code (in theory) wouldn't break . . . hmmmmm . . . On a more critical note, I'm still figuring out best principles for organizing params. Like, when you have a nested form what are the best practices for how your params should look? In the Nested Forms lesson, the example students/courses/grades was organized much like it was above. But in subsequent lessons, I found that instead of one big hash (in this case a spice hash) there may be another hash corresponding to a new object you created. And this was how I ended up arranging my params `{spice => {:name => "Curry", :flavor_id => "2", :recipe_ids => [ "2", "3"]}, recipe => {:name => "Daal", :url => "daal.com"}}` So now there are two hashes--spice and recipe--that correspond with the new objects the post request will create. And that's how we run into the aforementioned issue of blank params.

But right now IT WORKS. IT. WORKS.

![My Code Works](https://i.imgur.com/Rij3pTK.png)

**Heroku & Postgres**

Once complete, the finishing touch was deployment. Now I've always had a little bit of trouble with this last step, as it's never been clearly explained to me how the average person would download/install programs I made. The CLI tool was easy enough: run `gem install aic-cli-info-app`. It's a little program that you run in the terminal. But while I suppose you could do this here, my Sinatra app is not meant to be confined to the CLI; it's an independent web app. I wanted it to have the ability to run on the web. Therefore I said to myself, "Wouldn't it be great if I could do that? Let's use Heroku and deploy to the web!" Brilliant! So I went into the Heroku weeds . . . and right into the Postgres pit.

![ostrich fall](https://i.imgur.com/G1Lkbl5.gif)

Man. I uninstalled the Postgres app, reinstalled the Postgres app, created 6 or 7 Heroku apps, and deleted all but one. My app would fail to load, and the logs would tell me nothing I could understand. I ended up in a Stack Overflow wormhole regarding Unix Sockets and the whole time all I could think was a) what the hell?; and b)

![It's a Unix System](http://kepford.github.io/cracking-the-shell/assets/unix-system.gif)

So after about 7 hours of pure frustration punctuated by moments of astonishment as some little part worked then failed, I decided last night to go back to sqlite3. I finished retooling my app for sqlite3 and was preparing to begin this little post when I found a fortuitous discussion on the Flatiron Slack channel. Turns out there were at least 2 other folks on Slack attempting to do this, and were running into the same issues. Some more advanced students jumped in the thread, and presto! Resources!

I decided to give it another crack in the morning.

I did.

It cracked.

![cracked](https://media.giphy.com/media/eLQPdSfP4IlPi/giphy.gif)


HUGE shout out to Flatiron student Luke Kisabeth for the step by steps (check it out [here](http://lucaskisabeth.com/2017/06/24/deploying_your_sqlite3_sinatra_app_to_heroku_using_postgresql/)) and all the folks on Flatiron's great online dev Slack channel!

And IT WORKED.

![It worked](https://i.imgur.com/b4CEjns.jpg)

Check it out here: [Spice Rack](https://spice-rack-app.herokuapp.com/)
