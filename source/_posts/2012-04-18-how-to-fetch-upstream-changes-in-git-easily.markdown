---
layout: post
title: "How to fetch upstream changes in git easily"
date: 2012-04-18 11:11
comments: true
categories: Git
---

It is quite common to update your git fork repository with the upstream changes.

Here it is the workflow I use to keep synchronize my branch with [Octopress](http://www.google.com).

+   First of all, we should configure the remotes.
{% codeblock %}
$ git remote add upstream git://github.com/imathis/octopress.git
{% endcodeblock %}

+   Check the remotes

    {% codeblock %}
    $ git remote
    {% endcodeblock %}

+   Merge/Rebase the changes

    {% codeblock %}
    $ git fetch origin -v
$ git fetch upstream -v
$ git merge upstream/master
    {% endcodeblock %}

If you prefere you can create an alias in your _.gitconfig_.
{% codeblock %}
[alias]
  pull_upstream = !"git fetch origin -v; git fetch upstream -v; git merge upstream/master"
{% endcodeblock %}

Now _git pull_upstream_ will fetch the changes of both remotes, and the merge in the upstream changes.
