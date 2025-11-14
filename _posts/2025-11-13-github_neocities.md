---
layout: post
title: "github + neocities"
---
this is really cool -- i've got this site building static HTML using [jekyll](https://jekyllrb.com/) and hosting it here on [neocities](https://neocities.org). i'm digging this as an approach because it keeps the HTML really simple -- there isn't super complex templating, and there isn't super complex server side construction of each page. what you see is what i built, and it serves statically.

i wasn't going to use software to build the HTML, but i realized that maintaining categories and permalinks was going to be a lot of work to do by hand. that's where jekyll really shines -- it just automates the boring parts of building a website. everything else you can still tinker with by hand, but the boring maintenance stuff is gone!

but, that means i have to build the site. which means i need to keep the source code somewhere, and i need to build it, and then i need to take the output of that build and upload it into neocities. again, that sounded painful.

enter [github](https://github.com/). i set up a repo on github, set up a github action that basically says "if you do a git push to main, build the site with ruby/jekyll, then take the output and upload it to neocities." how cool is that? if i do a git push from my local machine, the site updates on neocities. alternatively, if i'm at work and i want to update the site, i can do it right in github. as soon as i commit in github, it renders the site and pushes it to neocities.

it's sort of shocking that github lets you do that kind of stuff in a github action for free. i'm literally spinning up a container, running ruby in it to use jekyll to render my site, interacting with the neocities API and then shutting down. i would have considered running shell scripts to do this, but it's much easier with github!
