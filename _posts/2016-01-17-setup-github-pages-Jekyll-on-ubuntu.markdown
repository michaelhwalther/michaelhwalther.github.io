---
layout: post
title:  "Setup github-pages / Jekyll on a Ubuntu"
date:   2016-01-17 16:13:34
categories: ubuntu blog
---

## Setup Prerequisites

### The basics

If not already present, check that the system-level infrastructure is present:

    sudo apt-get install ruby ruby2.1-dev zlib1g-dev 

Install a JavaScript engine for Ruby:

    sudo gem install therubyracer

Create file Gemfile in the repository `michaelhwalther.github.io`:

    source 'https://rubygems.org'
    gem 'github-pages'

Finally, run this to install gem “github-pages” (and Jekyll as one of its prequisites):

    bundle install

Check-in the `Gemfile` and the generated `Gemfile.lock` (=snapshot of versions as found/installed on this host)

### Generate first blog site

Run somewhere:

    jekyll new some-name

Then move generated content into the top-level repository.  
This “trick” allows to ‘adopt’ a generated repository (e.g. cloned from github) to be used as the source for the blog.

Setup a `.gitignore` for Jekyll-files and check it in:

    _site/
    .sass-cache/
    .jekyll-metadata

To locally test the Jekyll site, use: `jekyll serve` and point your Browser to `http://localhost:4000`

Now, check the `git status` and add any files listed using `git add`.
Finally, commit and push the changes to github and check the result in the [blog](http://blog.mmwalther.name).

