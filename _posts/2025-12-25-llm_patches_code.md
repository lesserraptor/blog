---
layout: post
title: "llm patches code"
tags: llm linux
---
alright, i'm going to sound a little like an llm cheerleader here, but i had a pretty big success with claude today and i wanted to write about what i did.

i play music on my stereos through the [moode audio player](https://moodeaudio.org/). it's really great, and you should install it. i loved my chromecast audio, but i hated how google made it progressively worse over its lifetime. moode can replace chromecast audio, but it's got some quirks.

one of the quirks it has is that the "casting" button that chromecast made so ubiquitous doesn't work for anything but a chromecast (anymore -- there was a while it worked for DLNA devices, but of course google ended up killing that). to get around this quirk, you have to figure out how to support apps that you used to "just chromecast" from.

here's the apps that i wanted to be able to work on moode:
- my local mp3 collection
- sirius XM 
- internet radio (like [weqx](https://www.weqx.com/))
- spotify (i don't like spotify, but many people do)
- youtube

i've now figured out a solution to all of these with the exception of youtube.

the one i just figured out today was sirius XM. i ended up using [sxm-player](https://github.com/AngellusMortis/sxm-player) to convert channels i like to listen to on siriusXM into internet radio channels served by the raspberry pi that hosts moode.

but here's the kicker -- that project hasn't been updated in 4 years, and in the meantime there's been some code rot. if you try to follow the install instructions, you'll end up with something that doesn't work and throws errors.

here, try it out if you want:
<pre>
<code>
> python3 -m venv ~/.venv/sxm-player
> ~/.venv/sxm-player/bin/pip3 install sxm-player
> sxm-player -U your-username -P your-password
</code>
</pre>

i looked all over the place and couldn't find a good solution for this. i'm not some pro programmer, but this was defintely going to take me a lot of time to figure out, and i simply didn't know that much about all the packages being used or how to troubleshoot them.

enter claude.

rather than poke around endlessly, i figured i'd see if claude could help me figure it out. i got it set up, explained what i was hoping for it to do, and asked claude to try to figure out how to fix it.

here's what i told claude i was hoping it would do:
the thing i like about sxm-player is that it sets up an http server that provides a URL i can use like an internet radio station in m3u8 format. this works for any channel that sirius XM has.

using that information, claude did a lot of trial-and-error troubleshooting that would have taken me a very long time to pull off. claude tried to change the python version, tried to lower the version of some of the dependencies, tried to use a previous commit to the repo, and even searched the github pull requests and issues for solutions. 

none of that worked, by the way, but claude was able to systematically work through that stuff without making everything worse, and in a way that i could verify the steps taken. it was SO MUCH faster than me trying to do it myself, and i think i learned the same amount from this approach as i would have if i had had to fumble through it on my own. but this was infinitely faster.

eventually, claude realized that the solution was to stop "forking" the process and spawn multi-processing mode -- which is something i don't think i would have come to without an enormous effort, if at all. 

claude figured out the three places to fix the python code, made the changes, and then we tested it out. to be quite anti-climactic, it worked! 

i had claude go back and document what worked, and i also had claude write a "patch" that i could apply to the installation so that i could repeat the steps. additionally, i had claude clear out the virtual environment we had been working in and start again fresh so that we had a live test of the work. 

WOW. the sxm-player software would have been DOA for me if claude hadn't been able to do this work. i wouldn't have been able to fix this myself, and i would have still been looking for a solution for getting sirius XM to work on my moode player. instead, i can now listen to any sirius XM channel on my home stereo in any room with a moode player now. 

i think this is the promise of AI. it sort of democratizes writing code. you still have to know enough to direct claude, but you don't have to be intimately familiar with 1000 python packages, or how multi-threaded architecture works for playing sound in python.

if i was an overachiever, i'd submit a pull request to the github repo to see if the owner would want to incorporate this change into the source tree. i'm not sure i'm ready for that sort of work yet, but if i end up repeating this pattern, i might have to give it a try!
