+++
draft = false
date = 2009-12-18T18:25:09Z
title = "Millennium Leaper"
description = "An Apple II game I wrote a long time ago"
slug = ""
authors = []
tags = ["apple-ii", "game", "6502", "programming"]
categories = []
externalLink = ""
series = []
+++

(This post was converted from [the
original](https://carlgay.wordpress.com/2009/12/24/millenium-leaper/) with
minimal changes. Some links were removed because the targets were missing and I
replaced the section about the Apple2Oasis emulator with the in-browser
scullinsteel emulator.)

In 1982-3 I wrote an arcade style game for the Apple II called Millenium Leaper
and sold it to a disk magazine called
[Softdisk](https://en.wikipedia.org/wiki/Softdisk). I didn't think much about
it again until in 2007 I was having a conversation with someone about old
computer games and it occurred to me to search for references to it on the
net. To my utter surprise I found that it could be downloaded in a bundle with
another game from the same period called Beer Run, and I could run it on
Windows in an Apple II simulator. I didn't do much with it since I was involved
with a fun project at work. It came up in conversation again recently and I
decided to write up my experiences developing the game, and to document the
game itself. This effort is mainly for my own satisfaction in recalling old
memories, but I hope it will be of some interest to others as well.

In 1982 my dad bought an [Apple
II+](http://en.wikipedia.org/wiki/Apple_II_Plus) computer. I was just out of
high-school and had a job washing dishes while I figured out what to do with my
life (although I didn't realize that's what was going on at the time) so I had
time to burn. My dad showed me how to do a few simple graphics tricks in
[Applesoft
BASIC](https://mirrors.apple2.org.za/Apple%20II%20Documentation%20Project/Software/Languages/Applesoft%20BASIC/Manuals/Applesoft%20II%20BASIC%20Programming%20Reference%20Manual.pdf)
and before too long I relocated the computer from his room to mine.

Pretty quickly it became obvious that there was no way to do the types of
things I was seeing in the video arcades and in some of the more advanced Apple
II games of the time with Applesoft BASIC. I had to use something that would
allow me to write directly to the HI-RES video memory and I ended up getting a
copy of the LISA assembler by Randy Hyde and teaching myself 6502 assembly
language. (Some time later I contributed code to that assembler but for the
life of me I can't remember what my code did. I received some paltry royalties
for my contributions...I have to wonder if Randy was just being kind to a young
kid since I'm sure he could have easily written the same thing himself.) I'm
not sure if there were any C compilers available at the time for the Apple II,
but I didn't know enough to look for them if there were.

I embarked on what turned out to be an almost two-year project to learn 6502
and write a video game. Many of the details of that process elude me. I
remember learning some basic techniques like a routine to convert hex to
decimal, then experimenting endlessly to create some cool sounds on the speaker
($C030). There was a mode in which you could display hi-res graphics on the top
3/4 of the screen and text on the bottom 1/4, and I used this to manually
modify memory and see what happened to the graphic display. For example I might
store #$81 at location $4000 and see the pixel at x=7, y=0 turn green. I played
around with this enough to start writing some graphics routines like drawing
lines and circles. Eventually I wrote a very simple graphics editor with which
to create images and save them.

## The Game

At the arcade I was heavily into Robotron, Donkey Kong, Defender and Joust, and
I basically set off to figure out how to make something similar to Donkey Kong
because it seemed the most doable on an Apple II+. Here's a description of
Millenium Leaper, approximately in the order the screens appear during play.

![How to play](/images/ml01-how-to-play.jpg)

The very first screen you see upon startup is this little beauty. Apparently it
never occurred to me that making the title page appear first might be a good
idea.

![Baud Bandits pirating info](/images/ml02-baud-bandits.jpg)

Should I call the cops? No, seriously, kudos to whoever preserved this stuff!

![Key bindings](/images/ml03-key-bindings.jpg)

Instructions.

![More instructions](/images/ml04-hints.jpg)

More instructions.

![Title page](/images/ml05-title-page.jpg)

The title page is animated. The title appears one letter at a time as the
aliens run back and forth underneath it making noise.

![Level one demo](/images/ml06-level1-demo.jpg)

The game enters a demo mode where it shows each level in action, while it waits
for you to remember that you have to hit the '1' or '2' key to select the
number of players.

![Transition to level 1](/images/ml08-transition.jpg)

The game commences. Why is the timer set at 9990 instead of 9999? I have no idea!

![Level 1 jump](/images/ml09-level1-jump.jpg)

Level 1 -- You control the little man, who runs around trying to collect the
numbers 1..9 and finally 0 (because 0 comes after 9 of course). The green
blocks disappear if you run over them, which can be used to isolate the aliens
since they can't cross the holes. But if you isolate an alien and later a
number appears in that area it can be hard to get the number. The hole in the
bottom floor moves left to right, which makes it difficult to jump when running
left to right.

![Going up to the next level in the elevator](/images/ml14-up-elevator.jpg)

On completion of a level, the screen scrolls down and an elevator drops down
(with attending sound effects) to take you up to the next level.

![Level 2](/images/ml13-level3-demo.jpg)

Level 2 — Run up to get the numbers while jumping the rolling barrels. The
barrels may fall off the end of each ramp or decide to come down the ladders.

Level 3 is pretty much the same as level 1 except that the floors “slide” left
or right as though they were conveyor belts.  It is probably the hardest level
to get past, and the least well designed.  The running of the little man is
extremely choppy, so it can be hard to transition to the ladders.  I think I
was trying too hard to come up with something a bit different that didn’t
require a huge amount of additional coding.

![Level 3](/images/ml07-level2-demo.jpg)

Level 5 — Getting a bit random now, by mixing up barrels and ramps and
whatnot. I haven’t been able to make it to this level in the emulator yet, but
if I recall correctly one of the main difficulties was needing to jump between
the left and right sides and having to open the parachute quickly.

![Game Over screen](/images/ml15-game-over.jpg)

![Top Scores screen](/images/ml12-top-five.jpg)

High scores.  I don’t think they were saved to disk.

### Implementation

I don’t recall a lot of specifics about the implementation except that I didn’t
know anything at all about game design or good coding style. Abstract data
types? Functional decomposition? Never heard of them. You might have noticed
that all the surfaces on which the aliens and the little man run are solid
white. That’s because I used that to detect where the floors were rather than
encoding any sort of model of the virtual world into data structures. That,
plus a few rules such as the maximum height of a jump and bouncing off the edge
of the screen were all there was. Spaghetti code, 6502 assembly style.

## Commercial Success?

Sometime in 1983 I managed to sell Millenium Leaper to
[Softdisk](https://en.wikipedia.org/wiki/Softdisk) magazine for about $300.
That probably works out to about $0.50 per day or around $0.08 per hour.  In
1984 Softdisk [offered me a job](/images/softdisk-offer.jpg) as a game
programmer and flew me down to Shreveport, LA for a look see.  Despite the fact
that I was still working on the loading dock at Symbolics at that point, I
turned them down.  I was fascinated by the Lisp machines at ‘bolics and I just
couldn’t imagine living in Shreveport at the time, though I often wondered how
things might have turned out if I had.

## Play the Game!

I found this in-browser Apple ][ emulator and asked them to put Millennium
Leaper in it. Here's a direct link to play the game on
[scullinsteel.com](https://www.scullinsteel.com/apple2/#millenium). Press `R`
(for run) followed by `C` to start Millennium Leaper.
