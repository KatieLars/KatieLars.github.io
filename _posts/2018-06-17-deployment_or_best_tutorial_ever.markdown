---
layout: post
title:      "Deployment, or Best Tutorial EVER"
date:       2018-06-10 20:35:58 -0500
permalink:  deployment_or_best_tutorial_ever
---

I deployed my ReactJS/Redux/Rails app today on Heroku.

I'd love to say it wasn't a struggle, but it was. So here's what I learned:

**Tutorials Are Great**

![Chow Yun Fat Thumbs Up](https://i.imgur.com/K8jZPTj.gif)

Specifically this tutorial: https://medium.com/@bruno_boehm/reactjs-ruby-on-rails-api-heroku-app-2645c93f0814 Thank you to Bruno Boehm for making it AND citing your sources. Note: those source tutorials are great too, but Mr. Boehm's was definitely my main squeeze.

There was one small addition I needed to make work: the API calls (GET, POST, etc) needed to be to Heroku's url to your app (`"https://potluckers.herokuapp.com"`, for instance)

**A Good Tutorial Is Gold. And Specific**

![Gold Nuggets](https://i.imgur.com/yCFmk9s.gif)

I come from a teaching background (I taught college art history for non-majors), and the number one thing I learned about human beings is this: if there is a workaround, an alternate meaning, a misunderstanding, or just plain a way to screw things up, humans will find it.

I don't mean this as a criticism exactly; the fact that these things happen regularly is a testament to the human mind and its diversity. Humans are clever animals, and I am rightly proud of that. Different modes of thinking are, in my opinion, great and should be nourished.

But underlying a tutorial is an underlying assumption: that we're all on the same page. For a step-by-step how-to that people can implement on their own (which is ostensibly the purpose of a tutorial) having the author and the reader think the same is integral.

As a relative newbie to all of this I noticed that some times in tutorials there is a lack of specificity in certain respects. Strangely enough, I've noticed across written tutorials, this lack occurs in fairly predictable areas.

As someone who has written 0 tutorials, I am by far not an expert. But as a academic writer (I'm published, folks, so I guess that makes me legit) who has had to form complex arguments based on biased and atypical source material, I can say that spelling things out and assuming nothing is key to reader retention and understanding.

In short, show: when giving CLI commands, explicitly show or tell me which directory you're in (this drives me crazy); show your errors--knowing common errors you received during the process and how you solved them is very useful; show me the exact location of the file you're altering (I have at least 2 `package.json`--when you're not being specific, I don't know which one you're referring to); assume nothing about my experience level or brain--you don't know me; and finally, explain your code to me like I'm a two-year-old. The folks most likely to use tutorials are newbs, and while it's great to get a beautiful line of code like `api: PORT=3001 && bundle exec rails s` but it's not going to be a reusable line of code for your reader unless you explain what it means.

Remember: the reader isn't inside your head. She can't read your mind.

**Every time I say 'deploy' in my mind, I hear 'exterminate'**

![Dalek](https://i.imgur.com/TJzxyAZ.gif)

**Deploying to Different Browsers Tells You Different Things**

![Geralt from Witcher 3 vs The Witcher](https://i.imgur.com/IBOV9b4.jpg)

Like these fantastic renderings of Geralt, we can tell that different tech yields different things.

There are two parts to my app: an API and a React UI. Now the React UI is basically a SPA, but the React-Router library gives us some great way to simulate page changes. But the front end needs to talk to the API, otherwise it can't POST, GET, or UPDATE and sort of data.

Initially, my app deployed its front end successfully. And the router was working; I could change pages. But as soon as I tried to log in or sign up, I got an error saying that the network connection was refused. On it's own, this was not very useful. It didn't say why it was refused, if there was a lack of database, a security issue, Postgres wasn't wired correctly, whatever.

So of course, when I Googled the error, I got a few different answers. One of them was a security issue, and so wonderful person recommended trying to run the app in Firefox.

I had been running in Chrome, but sure enough, when I ran it in Firefox I got a different, more useful error: mixed active content. And through Mozilla's own extensive documentation, I learned that this was essentially because I was calling `http://localhost:3001`, which is 100% not secure. They recommended I change it to `HTTPS`.

Now you can't just go in there and change it to `https://localhost:3001` (although I totally tried). That's not how that works. I had to change it to the actual url for my app (if you've read this far, see above seems kind of moot, but see above).

In short: not getting a useful error message? Try running your app in a different browser.

**My Own Tutorial . . . Sort Of**

![Adele reading How to Write Good](https://i.imgur.com/okl22cn.gif)

Let's see how well I take my own advice.

Looking to deploy your own ReactJS/Rails app? Follow the tutorial from Bruce Boehm. But where you make your API calls, use the app URL given to you by Heroku.

What I ended up doing was to create a new file `server.js` in the api folder in my client/src directory (where my React/Redux app lives). I made it export a constant, `PRODUCTION_SERVER` and set that equal to the app's URL. In other words, this:

`export const PRODUCTION_SERVER = "https://potlucker.herokuapp.com"`

I then imported that into all my separate API call files, so at the beginning of a file named, say, `friendApi.js`, I had `import * as serve from './server'` (I did have a second export value in `server.js`, so that's why I did the asterix). Then for each API call, I just did some interpolation for `serve.PRODUCTION_SERVER`. That way if I wanted to change the server that was being called, I could just change the value of PRODUCTION_SERVER.

 Oh, and make your node_modules folder visible (in other words, take them out of your `.gitignore` file) or Heroku's buildpack for Node.js gets confused and the compiler will fail.

 **Google is Your Friend**

 Or Duck Duck Go in my case.

![Simpsons playing Duck Duck Goose](https://i.imgur.com/cytAqE9.gif)
