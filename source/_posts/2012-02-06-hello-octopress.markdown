---
layout: post
title: "Hello Octopress"
date: 2012-02-06 13:00
comments: true
categories: 
---

## This My First Octopress blog! ##

I came across in setting up the two problems.

One is:

    rake aborted!
    You have already activated rake 0.9.2.2, but your Gemfile requires rake 0.9.2. U
    sing bundle exec may solve this.
    (See full trace by running task with --trace)

The solution is Use

    bundle exec rake 

instead

The other is:

    * * Invoke generate (first_time)
    * * Execute generate
    # # Generating Site with Jekyll
    Unchanged sass/screen. SCSS
    D: / RailsInstaller/Ruby1.9.2 / lib/ruby / 1.9.1 / psych. Rb: 148: in ` parse ': peasants' t par
    Se YAML at line 68 column 0 (Psych: : SyntaxError)

The solution is to check ':' if a space behind less

## Submit command ##

    bundle exec rake generate && bundle exec rake deploy

## Using Octopress ##

 - [Blogging Basics](http://octopress.org/docs/blogging "how to create blog posts and pages")
 - [Deploying Octopress](http://octopress.org/docs/deploying "simple deploy instructions for Rsync and Github pages")
 - [Sharing Code Snippets](http://octopress.org/docs/blogging/code "share code snippets with ease")
 - [Blogging With Plugins](http://octopress.org/docs/blogging/plugins "overview of plugins for blogging")
 - [Theming & Customization](http://octopress.org/docs/theme "guide to making changes to your Octopress theme")
 - [Updating Octopress](http://octopress.org/docs/updating "a guide to help you stay current with Octopress")