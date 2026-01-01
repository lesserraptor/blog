---
layout: post
title: "embedding metadata in a siriusxm stream"
tags: ai
---
i'm continuing to experiment with claude. continuing on my siriusxm fix post from last time, i noticed that the stream from siriusxm didn't include the metadata about the song currently playing when it was displayed in moode. this seemed like a good opportunity to try to get claude to work out a solution!

first up, i described the issue: i have a stream of audio coming from siriusxm, and it isn't showing metadata in my moode player. i want to get it to show metadata similar to how other channels do (and i gave it some example channels).

next, i had it start to do some exploration. what was the format of the stream coming from siriusxm? did it have any metadata already in it? did the sxm-player implementation have any api calls that might help?

once we got all that information squared away, we got to work -- claude started implementing embedding metadata in the stream, but it was continuing to modify my patch to get sxm-player working in the first place. this was suboptimal, i didn't want this new work to conflict with the already working patch i already had. so i had it start again.

this time, we kept the code isolated from the initial fix, but we assumed that the initial fix was already applied. awesome, this is a much better way to build incrementally.

claude tried a bunch of things -- and in the end i didn't like any of the results. the obstacle i eventually bumped up against was that i was trying to inject the metadata into the stream, but due to my moode player's buffering, it was taking too long to reflect in the UI. i did manage to get the metadata injected, and it was definitely displaying in moode, but for all the complexity of adding this functionality, it was showing the song name way too late in the song's playtime to be useful.

the eventual architecture that moode decided on was to regularly ping the sxm-player api to get the "now playing" information, then inject it into a second streaming endpoint (to preserve the original working properly). i'm not wild about the constant pinging approach, but there isn't an event stream that tells me when to update the metadata. additionally, due to buffering, it seems like even "every 5 second" updates weren't going to be sufficient because it would depend on how long the buffer was.

this outcome was frustrating, but if you look at how much progress i was able to make on this in such a short amount of time, it's a bit staggering. i didn't know how to do really any of this work, but i was able to get a brand new endpoint set up that was able to inject metadata into the stream and not corrupt it. and it worked! it just wasn't fast enough.

i'll keep noodling on this, i might come up with a better idea that gets me aroudn the buffering issue, but claude wasn't helpful in coming up with alternatives. this is where i find that the human in the loop is still necessary. claude gets painted into a corner quite easily -- the context it has ends up trapping it behind incorrect conclusions. keeping it moving is actually a bit tricky, because it's a weird mix of understanding what it's doing better than it does, but also delegating all the drudgery of the details back to it. definitely gotta keep hacking on this, there's so much potential!
