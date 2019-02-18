---
layout: post
title:      "React Native and Android Studio: What's Not in the Docs"
date:       2017-05-04 15:25:58 -0400
permalink:  react-native-android-studio-not-in-the-docs
---

![Final Campaign Picture](https://i.imgur.com/Y2qBfnA.jpg)

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

**Caveats & Tips**

<IMAGE FOR CAVEATS>

Caveats first: Of course if you have other bugs or issues, I would say a) check your work for both these instructions and for Facebooks to make sure you've installed everything correctly; then b) start Googling. You're never alone with these types of things.

Tips: As I started developing, I noticed some issues that were more user error than anything. But to save you time, here's what I learned.

1. **ANDROID STUDIO IS DESIGNED FOR JAVA/KOTLIN.** Since Android's preferred native language is Java and Kotlin (a Java based lang too), the editor for the Studio is essentially IntelliJ. It's not built for JavaScript, which is what React Native is based in  (or JSX specifically). I've found that when dealing with Java or Kotlin, it's best to keep those editors separate. I use VS Code for pretty much everything except for Java, where I switch over to IntelliJ.

So why have Android Studio in the first place? Answer: the emulator.

I use it to get the emulator up and running first, then close Android Studio, and open VSCode and my React Native project. I run the emulator through VSCode's terminal. 

**2. To run the emulator in Android Studio,** click on this icon

<IMAGE OF DROID>

found here, in the top right corner:

<IMAGE OF MENU>

Then press the "Play" triangle button to run the emulator you created (mine is the Pixel 2; the Nexus was the default one).

You should see an Android phone pop up somewhere on your screen. 

**3. You must launch the emulator before running `react-native run-android`.** The latter part of this command looks for an already running emulator, so get it running. A second terminal running Metrobundler will also pop up in the background as a separate window. I pretty much ignore it until I shut everything off. Then I Ctrl + c it.

**4. Also, to enable hot reloading, the developer menu of the emulator can be located by pressing Cmd + m and selecting "Enable Hot Reloading".** (Facebook says this can be done, but doesn't give great instructions on how to do so).

<INSERT DEV MENU>

And that's all I got! Hope that fills in the blanks for those starting out. One of the hardest things about not having a CS degree and only knowing code is getting started with architecture, servers, webpack, environments, etc. It's like I don't do it frequently enough for it to be a muscle memory, but I don't have a good enough theoretical grounding in it to intuit it's structure. 

Nothing to do but to keep on learning!

<IMAGE FOR LEARNING>












