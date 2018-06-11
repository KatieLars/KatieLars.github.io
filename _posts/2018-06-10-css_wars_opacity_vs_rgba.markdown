---
layout: post
title:      "CSS Wars: Opacity vs. Rgba"
date:       2018-06-010 20:35:58 -0500
permalink:  css_wars_opacity_vs_rgba
---
![CSS King of the Hill](https://i.imgur.com/GaBMkKo.gif)

CSS is so seductive: you can see the pretty happen right before your eyes. You love it. It's an easy triumph. But then you want the pretty to do something slightly different. And like herding cats or catching small birds, the pretty just doesn't want to do it.

So we gotta find ways to hoist the pretty on its own petard.

![Hoisted on his own petard](https://i.imgur.com/R5CcCsu.gif)

This particular instance of CSS-pretty-not-doing-what-I-wanted came when I tried put opaque text inside of a transparent box. Simple enough. Or not.

I started by adding an opacity property to the box I needed (i.e. opacity: 0.6;). Note: this was about modifying a fairly complex CSS template not made by me.

This was actually for the blog index page of this very site, which uses the Jekyll blogging framework. As each box is dynamically generated, the CSS needed to be flexible enough to allow for a transparent box that could change in size according to its opaque content.

**Strategy One: Wizard of Id**

![Wizard of Id](https://i.imgur.com/7zi1WNL.jpg)

The header tag was the parent element that contained all the text. So I thought I would simply right some code that looked something along the lines of ``#opaque { color: black; opacity: 1.0;}`` with the matching HTML ``id="opaque"`` in the header tag.

Now normally, whenever you have a specific identifier like that, those attribute values take precedent over more general class or element attribute values. This way the article tag--which wraps the header and all the text inside--would be transparent while the interior header tag would be opaque.

This did not work.

![Monkey Throwing Computer](https://i.imgur.com/ygrefA5.gif)

Turns out that the opacity property in CSS3 affects every element that is a child to whatever the opacity property is assigned to. In other words, my text was transparent despite me having giving it an id and CSS selector that made it, well, not transparent.

**Strategy The Second: No Child Of Mine.**

![Axl Rose](https://i.imgur.com/ylk5mhI.gif)

CSS Tricks recommended a frustrating but elegant solution to this: simply take the text out of whatever wrapper it's in and position it over that transparent wrapper.

For example: my text was in a couple of wrappers, but the one that was the correct size and set to dynamically change according to the size of the content was one that had ``id="main"``.

So to test this theory, I removed a p element and styled that using ``id="opaque"`` with the same properties as before, but with additional positioning elements: ``position: relative; margin-top: 3em;``.

I kept the position relative because I still wanted it to be responsive so it would remain in the flow of the page; I didn't want anything else appearing on top of it and I wanted it to scroll like a normie.

The problem was this: because the size of the transparent box was dependent on its content, if I removed all the text, when there was no content, there was no box. I would have to set the size of the box. And therein lies the rub: each box is dynamically generated based on varying input sizes, which are rendered as HTML children. No children, no transparent box.

By now I was tearing my hair out.

**Strategy For The Win: Notorious RGBA**

![Notorious RBG](https://i.imgur.com/j6YzUQh.png)

This transparent box/opaque text problem is a fairly common one, and if you're using a static HTML layout, Strategy The Second would work rather nicely once you get all the positioning and such down.

But for dynamically generating HTML, you need it to be flexible. And that's where RGBA comes in. See, the opacity property is rather possessive; it likes to boss all the children around and tell them that no matter who they are, no matter their identity, they will be transparent. RGBA is not so bossy.

RGBA--Red, Green, Blue, Alpha--is a way of constructing a color based on red, green, and blue values (note: these are the primary colors for additive colors--colors composed by adding wavelengths of light together--vs. subtractive colors--colors composed by having wavelengths cancel each other out. Subtractive colors mostly work for inks and pigments.). The final value is alpha, which determines the transparency of each pixel.

In CSS, it's written as function rgba() with four parameters: red, green, blue, and alpha. The first three are given as integers on a scale of 0 to 255, with 255 being the maximum value for that color. The final parameter, alpha, is just like opacity: it has a value between 0 and 1, with 1 being completely opaque.

So, I got rid of my bossypants opacity property and put in the much more civil ``background: rgba(255, 255, 255, 0.6)``. Note: additive colors are basically like adding wavelengths of light, so think of it like a prism. A prism splits white light into the visible spectrum. When you add all those colors (max red, green, blue--or 255) you get white. And 0.6 is the opacity.

AND BOOM. Worked like a charm.

![SNL Ruth Bader Ginsberg](https://i.imgur.com/vdNz0h8.gif)
