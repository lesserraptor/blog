---
layout: post
title: "raspberry pi trouble"
tags: linux
---
i run 3 raspberry pis at my house. each has a specific function:
- (pi4) one for the stereo in my office/workout room. this one runs [moode audio](https://moodeaudio.org/) so that i can either listen to internet radio (mostly to [WEQX](https://www.weqx.com/)) or to my MP3 collection.
- (pi4) one for a [pihole](https://pi-hole.net/), which my network uses as the main DNS server. pihole is fantastic for limiting the number of "waste" network connections that are made across my network. it definitely saves bandwidth.
- (pi0) a third is for my stereo in my kitchen, and it, too, runs moode audio. this is so that we can listen to music in the main kitchen or out on the deck. this one streams internet radio and MP3s, but it also gets used pretty heavily for spotify.

i started having problems with the kitchen one recently; i'm not sure why, but it stopped smoothly running audio, and the spotify connect got really choppy and mostly stopped working.

the kitchen pi was a [pi zero](https://www.amazon.com/CanaKit-Raspberry-Zero-Basic-Official/dp/B0CT1Y3CQJ?crid=2SGW3740G0TBO&dib=eyJ2IjoiMSJ9.t-BTW30Tluhki6lWlHIi2hsI9RqlbxfT86ilD5P__ArpY81-d2cnwqfPDVuPX34cFFDgTmPUp_FeHJ2JSPnlQN0MhvtLsWjXG4WzsLjP23kG6RD2z3LTEY9D47JS0IMo75OSPstRBuNDDIvHSO8na4l3-qWG6yv-BIEdGacgG2bgl0zWNBUFvRR23K7RLfXGQz4FZv0pKQyD4HODbFb3h6lRxyfybrWgd4nfQJys5e0.pTS8ShP71YDI2_FNpWBJvK5ABYXyTg7VLxDhm22DkQc&dib_tag=se&keywords=raspberry+pi+zero+2+w&qid=1764474510&sprefix=raspberry+pi+zero%2Caps%2C120&sr=8-9), and i suspect it just didn't have enough RAM in it to keep moode running smoothly. i can't find any evidence of that on the internet, but the [pi4](https://www.amazon.com/CanaKit-Raspberry-4GB-Starter-Kit/dp/B07V5JTMV9?crid=2P2U0AIFUG1HA&dib=eyJ2IjoiMSJ9.Xksc4QMnpl0XTxlxg-mR1u1Q8FxhT5CyPuv79OaTx_c7OhNUVhAJrmDv2F07sZvH077QTkH0Ojg5gRlPdjc5hyEUENsE9_nTXl7esUmuORq0qFKQIxSiVyWNw2vZ9Hhyrh2zQ_xpZRqSgQGvLJyXAUgy0IIft1pdH_QOqcQof-dPLUFs58jzZH5kptScc1r-rktHOI0BRLPu0qBqm5rckjLE_fQBXS7HkbOVhQGWLG0.zCkWbKsCSaOWfXs7k164R75Q_qn7ET-ohMpt3yPQ-CU&dib_tag=se&keywords=raspberry%2Bpi%2B4%2B4gb%2Bcanakit&qid=1764474647&sprefix=raspberry%2Bpi%2B4%2B4gb%2Bcanaki%2Caps%2C127&sr=8-1&th=1) in my office never has any issues. 

to deal with this, i decided to swap the pi zero for the pi4 that was running pihole. i figured that a pi zero should be able to handle pihole with ease, while the pi4 had already demonstrated it could run moode well.

i started the swap today -- but ran into a problem. i was trying to re-image the pi zero with the lite version of debian, but it just refused to connect to the wireless router. i tried many, many things and wasted a ton of time. 

i say i wasted time because when i tried the "legacy" version of debian, it "just worked" -- so there was something wrong with trying to install "debian trixie" that didn't cause issues with "debian bookworm". i wish i had just tried this from the start, i could have saved a whole afternoon.

luckily, installing moode 10 (which is trixie-based) went smoothly on the pi4. i think the pi zero is just a very small device, and so you have to be careful what you try to put on it.

i'll update in a while on what i see, but so far everything is working properly.
