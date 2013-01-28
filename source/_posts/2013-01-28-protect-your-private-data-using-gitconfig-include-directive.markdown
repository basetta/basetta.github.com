---
layout: post
title: "Protect Your Private Data Using Gitconfig Include Directive"
date: 2013-01-28 13:59
comments: true
categories: git 
---

I am using a [dotfiles](https://github.com/basetta/dotfiles) git repository in order to keep my machine preferences in sync. 

This is working pretty well, until you realise that are some config entries that are clashing with each other.

One of those cases, is the common situation  of having two github accounts -- one for work and one for private purposes. In this case we would like to share the common git configuration but not the committer's author name and email address held in the .gitconfig.

Recently, git added a new feature, the include directive for config files ( since 1.7.10 ) that can solve the problem.
With the include feature you can split your gitconfig across multiple files, so you can have the common git configuration in one file, and private information in another.

Let's have a look at an example :

* Add the include directive to your .gitconfig ( this is the file in your git dotfiles repository )
	{% codeblock %}
    	[include]
	       path = ~/.gitconfig_user
	{% endcodeblock %}

* Add to ~/.gitconfig_user your private data
{% codeblock %}
[user]
     name = Silvio Berlusconi
     email = silvio.berlusconi@bungabunga.it
 {% endcodeblock %}
 
* Test if the config is working properly
{% codeblock %}
$ git config user.name
Silvio Berlusconi
$ git config user.email
silvio.berlusconi@bungabunga.it
{% endcodeblock %}



