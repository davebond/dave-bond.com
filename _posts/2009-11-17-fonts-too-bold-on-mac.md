---
layout: post
title: Font too bold on a mac?
redirects:
- /css/font-too-bold-on-a-mac/
---

Ok this seems to be a very rare problem, when I ran into this problem nobody on the entire internet seemed to know... Any advice I found was to change the colors I was using....

The problem occurs when you put a light colored font over a dark background (the issue doesn't seem to affect all fonts), the anti aliasing seems to go into overdrive and makes the font much bolder than it should be. OSX uses the quartz system to render the text which is optimized for dark text on a light background, but when we do the opposite it goes crazy and the font goes super bold.

Example: Text with issue on the left, the text you really want on the right.

![Example](/images/2009-11-17-fonts-too-bold-on-mac/example.png "Example")

Well I have a present for all you, just cause I'm a nice guy. Want it to look like the text on the right?

Apply `opacity:0.99;` to the CSS of all affected text, we've only dropped the opacity by 1% but suddenly we have the right weighting :)

Cya