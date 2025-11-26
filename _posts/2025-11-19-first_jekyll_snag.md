---
layout: post
title: "first jekyll snag"
tag-name: jekyll
---
ah well. i hit my first jekyll snag. 

i was trying to add "pagination" to my blog posts here. it seems like it would be nice to limit the number of posts on this front page to, say, 8. and then of course, i'd want a "next 8 posts" type link, and probably a "previous 8 posts" link.

it gets a little weird here, because you have to remember that this site is serving statically -- that means that to achieve what i want, there needs to be a page for "posts 1-8", and then another page for "posts 9-16" and so on.

but of course, the point of jekyll is that it's supposed to automate that mundane process of "putting 8 posts per page and saving it". so i have to figure out how to do that.

that's where the first real snag came in here. it seems like the logic to do that actually resides in a "gem", and i need to load that gem and configure it. i don't love this. this is the first actual "complexity" that i've seen here. to get this code added in, i need my project to be able to get a new gem, configure it, and then i have to make changes to the templates to get them to do the right thing.

this wasn't simple to figure out, and so i gave up after about 45 minutes of fiddling. i will have to come back to this.

for the record, i looked at [this page](https://jekyllrb.com/docs/pagination/) to get started. the jekyll docs seem a bit dated, and maybe incomplete or assuming i know more than i do. not a great look. it's too bad, because i've loved all the paradigms jekyll uses up to this point.

i suppose an infinite page depth isn't the end of the world, but i just don't like the way it looks. i'll get this fixed.

also, i think i need to start experimenting with categories, too, these posts should have a bit more organization, especially if i'm using software to do the organizing. more to come!
