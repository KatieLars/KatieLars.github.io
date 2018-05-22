---
layout: post
title:      "Take It From The Top"
date:       2018-05-06 22:56:58 -0400
permalink:  take_it_from_the_top
---

This should really be called "Eat Your Veggies". 

See I have this problem where I forget sometimes to eat my code veggies.

![Man Fondling Lettuce](https://i.imgur.com/WgfV54W.gif)

Thankfully most projects are dessert-oriented rather than veggie-oriented in that their bulk is that wonderful sweet code that I can just hang out in.

![Spinning Chocolate Torte](https://i.imgur.com/WtkE12S.gif)

And by code veggies I mean all the little things that go into starting projects and keeping them up and running, particularly via the CLI. So here is a blog post to make my life easier that lumps all that goodness together so I can spin my projects up without having to Google the same commands over again.

**Git CLI Commands**

Love those CLI commands, but for some reason they never stick.

Get started:
  --Create your repo in GitHub.
  --Clone your repo
  --Run `git clone $paste-your-repo-name-here`
  --Run `cd $repo-name-without-extensions`
  --Spin up `atom . `
Boom. You have a master.

![Anna Kendrick Boom](https://i.imgur.com/o77SyO2.gif)

Branch out:
  --Create your branch locally inside your master branch with `git checkout -b $branch-name-here`
  --Change to your branch `git checkout $branch-name`
  --Push the branch to GitHub `git push origin $branch-name`
Boom. Boom. You have a branch.

![Tiny Dog Falls, Goes Boom](https://i.imgur.com/Nu7CeHx.gif)

Merge your branches (for when you're ready to deploy):
  --From master branch: `git merge $branch-name`

And don't forget your `-m` flags to leave a message at the tone.

Sources: [https://git-scm.com/](https://git-scm.com/)

[https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches](https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches)

**Creating Apps from Scratch**

Get cozy in your GitHub local repo's master branch before pushing ahead with these.

Ruby:
  --Just make the files in .rb
  --Run from terminal with `ruby $file-name.rb`
  --For more complex OO programs, `ruby bin/program-name` with cascading modules/classes and call method
Ruby on Rails:
  --`rails new app_name`
React:
  --`npx create-react-app $app-name `

Sources: [http://guides.rubyonrails.org/command_line.html](http://guides.rubyonrails.org/command_line.html)

**Running the Show**

Get those servers up! But be sure to be in that master branch

Ruby:
  --`ruby $file-name.rb`
Ruby on Rails:
  --`rails server`
  --Drop into your db (not tb) sheets with `rails console`
Sinatra:
  --Be sure to have a config.ru to run `rackup`
  --Install Tux gem and run `tux` to get Sinatra version of console up
React/Redux:
  --Be sure to add a proxy server address to package.json if you are running a separate API backend
  --Run `npm start`
Python Simple Server:
  --`python -m SimpleHTTPServer` default port is 8000, but you can change it to any port just by adding a 4-digit number afterword

Sources: [http://www.pythonforbeginners.com/modules-in-python/how-to-use-simplehttpserver/](http://www.pythonforbeginners.com/modules-in-python/how-to-use-simplehttpserver/)

Getting to dessert faster is always the way to go.

![Cracking Creme Brulee with Spoon](https://i.imgur.com/bcj0V0f.gif)
