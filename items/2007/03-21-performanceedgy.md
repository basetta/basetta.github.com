---
comments: true
published: 2007-03-21 06:00:00
layout: post
slug: None
title: Performance Tip For Edgy/Feisty Users
wordpress_id: 43
---

Now and again I've been experiencing poor performance in GNOME.
Looking for a solutionI have found this tip [ here ](http://ubuntuforums.org/showthread.php?t=388765).
It really works at leat for me.

Edit your /etc/hosts file:

~~~~~~~~~~~~~~~~~~~~~~~~~~
$ sudo gedit /etc/hosts
~~~~~~~~~~~~~~~~~~~~~~~~~~

You should see something like that:

~~~~~~~~~~~~~~~~~~~~~~~~~~
127.0.0.1 localhost

127.0.1.1 basetta-laptop
~~~~~~~~~~~~~~~~~~~~~~~~~~

Now write on the first line your hostname (my hostname is basetta-laptop).


~~~~~~~~~~~~~~~~~~~~~~~~~~
127.0.0.1 localhost basetta-laptop

127.0.1.1 basetta-laptop
~~~~~~~~~~~~~~~~~~~~~~~~~~

Now Save.

**Explanation why**



>
This is a fix for the new system that was started back in edgy where the host name was split off to 127.0.1.1, the problem is that some applications still look for the host name @ 127.0.0.1, so to keep those applications happy and running smoothly you simple need to add the host name where those applications expect it to be.





