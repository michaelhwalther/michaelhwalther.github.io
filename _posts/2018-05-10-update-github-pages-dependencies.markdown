---
layout: post
title:  "Keeping a github-pages-based blog on current technology on Ubuntu"
date:   2018-05-10 20:44:00
categories: ubuntu blog
---

## The task

Well, it's probably been a couple of ... weeks since you last updated your blog.
It may have been a little longer, even, come to think of it.

So, you start receiving email alerts from github, bringing to your
attention the fact that your libraries used in your (blog) project are falling out
of date, including continuing to expose security vulnerabilities.

The solution is usually simple: just update to the latest version.

But: how would you do that? Where did I put my "blogging platform" again?
I think, there used to be a command somewhat ... or other... oh, yes, it was
ruby-based... hm.


## The procedure 

### Reminder of the basics

Instead of repeating the steps, please refer to the prior post about the [initial setup]({{ "/ubuntu/blog/2016/01/17/setup-github-pages-Jekyll-on-ubuntu.html" | absolute_url }}).

### Update dependencies

The "magic command" you are looking to execute is this:

    sudo bundle update

This takes all the gems currently installed on your system to implement
the `Gemfile` dependencies and checks whether there is an update available.
If so, the update is downloaded and installed.
Also, the new version is noted in the `Gemfile.lock` file.

To test whether your site still works after this, try the stock:

    jekyll serve

and point your browser to the indicated site (usually http://localhost:4000/)

### Publish your update

Now check what actually has happened, using:

    git status

It is expected that only file `Gemfile.lock` shows as "modified".

The modifications should indicate the new versions used, potentially including
new or removed dependencies.

If this is all to satisfaction, it is now time to push the changes to github:

    git commit -a -m "Updated Gem dependencies"
    git push

Finally, check the result in the [blog](http://blog.mmwalther.name).
