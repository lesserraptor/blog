---
layout: post
title: "git usage reminder"
tags: git
---
i seem to forget how to use git everytime i sit down to use it. admittedly, i don't use it all that often, but i just really struggle keeping its "mental model" in my head.

so, to try to remind myself, here's some info on how to use it:

- first off, you have to make sure your local ssh key is installed in git. i wasn't able to get the tokens to work, but ssh definitely works and everyone seems to think this is easier overall anyway. here's an article to read about how to do that setup: [Setup SSH for GitHub](https://dev.to/taujor/how-to-set-up-ssh-for-github-on-linux-a-step-by-step-guide-1jmh)
- once you've got ssh set up, you need to point git at the repo: <code>git remote set-url origin git@github.com:your-username/your-repo.git</code>
- test out that it's working: <code>ssh -T git@github.com</code>
- if you are starting from scratch, and want to get the current state of a repo, that's what clone is for: <code>git clone url-of-rep</code>
- if you add a new file to your repo, you'll need to also add it to git: <code>git add .</code> is the lazy way to do that.
- once you have made a change somewhere, you need to create a commit: <code>git commit</code>
- finally, when you've got a commit out there and want to update the repo: <code>git push origin main</code>

i'm going to keep updating this post (and probably changing the date on it as i do that) so you might see this post pop up a few times on the blog.
