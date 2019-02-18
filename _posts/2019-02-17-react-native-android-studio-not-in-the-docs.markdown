---
layout: post
title:      "React Native and Android Studio: What's Not in the Docs"
date:       2017-05-04 15:25:58 -0400
permalink:  react-native-android-studio-not-in-the-docs
---

<Picture of Jason Crow Campaign>

I'm back! After spending about 4 months working as a technologist on Congressman Jason Crow's campaign, I'm back in the thick of things and looking for my next gig as a full-blown web developer.

So I've decided to switch tracks a little and do some mobile development in React Native. I have ideas . . . 

React Native, like React.js, is a Facebook framework that cna be deployed on either iOS or Android operating systems. This cross-platofrm quality was what drew me to it in the first place. I want to make one app that can work for both my Android-toting self and my iPhone-loving friends.

Also like React.js, it has pretty good--and at times, great-- documenation. So I followed the step-by-step procedures for getting started on OSX for Android (check it out [here](https://facebook.github.io/react-native/docs/getting-started)). Now I'm not sure if the docs were just slightly outdated, or simply written by somehow who doesn't know how to teach to newbs, but it was less than perfect. A couple of things needed to be added, which is the point of this whole blog post. 

Everything was going along hunky-dory until I saw this: "Add the following lines to your $HOME/.bash_profile config file:"

Which leads me to my first point:

**What the hell is a .bash_profil config file?**

The answer: it's a hidden file (which is why it begins with a dot) that determines (or configures) your shell environment. 

So in this case, you have to tell your shell how to configure your `ANDROID_HOME` variables and other native tools. Facebook does give you the exact code you need to add to the file, and you can access and alter it by following Nate Landau's instructions and awesome explanation [here](https://natelandau.com/my-mac-osx-bash_profile/). 

On to the next. 

I followed all the instructions for initializing a project, setting up Android Studio, and getting a virtual device up and running.

Now to run `react-native run-android`.

**BUILD FAIL**

(INSERT IMAGE OF FAILURE)

 Gradle (our little automated builder) couldn't build our app. And the emulator remained stubbornly on the homescreen. 

 So what happened? This error: `Could not create service of type InitScriptHandler using BuildScopeServices.createInitScriptHandler().`

 Fabulous. I have no idea what that means.

 Then I tried to run it in Android Studio. No such luck. Said it couldn't find the SDK (this was a separate issue).

 Here's what I did for the first error:

 1. It has to do with Gradle's wrapper. So go into android > gradle > gradle-wrapper.properties and change your distribution version to 4.10.1. So the last line in this file should read: `distributionUrl=https\://services.gradle.org/distributions/gradle-4.10.1-all.zip`

 2. Configure your app. When you select "Run" in the top menu of Android Studio, you should get a pop up that has the option to Configure your app. 

 <insert screen shot>
 
 Click that. A new window will open that looks like this, but blank. In the Name field at the top and Gradle Project field underneath, type the location of build.gradle file. 

 It should look like this:

<Insert screen shot>

The click `Apply`. 

That's it! You're ready to go!

Now for the second error . . .

**Could not locate the Android SDK.**

 Well, turns out you have to tell your app where it is. If you followed the instructions from Facebook up until this point, you should have the SDK installed. 

In the root of your `android` directory of your React Native project, create a file called `local.properties`. Add a line specifying where the SDK lives. Mine looks like this: `sdk.dir=/Users/katielarson/Library/Android/sdk`

Yours probably will too. And that's it. When you run `react-native run-android` in your terminal, your emulator should start and you should be on your way.

**CAVEATS**








