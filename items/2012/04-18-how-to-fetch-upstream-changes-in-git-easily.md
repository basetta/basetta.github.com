---
layout: post
title: "How to fetch upstream changes in git easily"
published: 2012-04-18 11:11
comments: true
categories: Git
---

It is quite common to update your git fork repository with the upstream changes.

Here it is the workflow I use to keep synchronize my branch with [Octopress](http://www.google.com).

+ First of all, we should configure the remotes.

~~~~~~~~~~~~~~~~~~~~~~~~~~
$ git remote add upstream git://github.com/imathis/octopress.git
~~~~~~~~~~~~~~~~~~~~~~~~~~

+ Check the remotes

~~~~~~~~~~~~~~~~~~~~~~~~~~
$ git remote
~~~~~~~~~~~~~~~~~~~~~~~~~~

+ Merge/Rebase the changes

~~~~~~~~~~~~~~~~~~~~~~~~~~
$ git fetch origin -v
$ git fetch upstream -v
$ git merge upstream/master
~~~~~~~~~~~~~~~~~~~~~~~~~~

If you prefere you can create an alias in your _.gitconfig_.

~~~~~~~~~~~~~~~~~~~~~~~~~~
[alias]
  pull_upstream = !"git fetch origin -v; git fetch upstream -v; git merge upstream/master"
~~~~~~~~~~~~~~~~~~~~~~~~~~

Now _git pull_upstream_ will fetch the changes of both remotes, and the merge in the upstream changes.
