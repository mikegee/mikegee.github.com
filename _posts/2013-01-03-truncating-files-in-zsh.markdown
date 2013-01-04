---
layout: post
category: posts
title: Truncating Files in Zsh
---

Backstory
---------
I was setting up Time Machine on my laptop and figured I should look for big useless files and avoid backing them up.
I like [GrandPerspective][grandperspective] for scanning directories to find disk space hogs.
This showed me that I had a bunch of huge Rails logs (from development and testing).

The Syntax
----------
The following command truncates all the log files in all my projects.
    : > ~/Projects/*/log/*.log
That colon at the beginning is part of the command.
I think Bash is the same without the colon, but don't take my word for it.

Postscript
----------
I could have just deleted the files.
    rm ~/Projects/*/log/*.log
Rails would simply recreate them as needed.


[grandperspective]: http://grandperspectiv.sourceforge.net/
