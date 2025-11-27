---
layout: post
title: "zwift and wine in linux"
tags: zwift linux
---
i'm a linux user. long ago i moved to linux (probably around 2001) and i really haven't ever looked back. sometimes i have to use windows or mac os at work, but for my own personal computers i'm 100% linux.

there's one problem, though: i'm also a zwifter. i ride my trainer on [zwift](https://www.zwift.com/) 5 nights a week, and it's my main exercise routine. zwift can run in linux using wine, and it actually performs pretty well -- but the accessories that make the cycling possible all connect to the computer via bluetooth. and bluetooth doesn't work very well in wine.

so what is missing? wine can run zwift, and the trainer, controllers and heartrate monitor can all connect to BLE in linux. the missing piece is that there isn't a way to pass the signals from BLE into the wine application. so i've been patiently waiting for this to get resolved. wine 10 came with some BLE compatibility enhancements, and so it seems like it's going to happen soon.

there is a workaround for running in linux; you can use your smartphone to connect to the bluetooth devices, and then have the phone bridge to the wine install to pass the signals in. this actually works, but there can be some slight lag, and you need to have the phone up and running during all your training sessions. i'm not excited to have both the phone running and the possibility of lag, so i'm not doing this at this time.

the main way i'm monitoring this situation now is to watch a thread in [netbrain zwift container](https://github.com/netbrain/zwift) project. [the thread](https://github.com/netbrain/zwift/issues/188) has been recording progress from the devs as they dilligently test each subsequent wine release to see if it works yet.

so far, the news hasn't been what i want to see, but i'm optimistic that it will happen soon. once it does, i can get windows off that last "gaming" computer i use for zwift.
