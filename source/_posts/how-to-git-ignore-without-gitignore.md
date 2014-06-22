title: 'How to Git Ignore without .gitignore'
tags:
  - git
id: 640
categories:
  - 'Tech Tips'
date: 2014-03-23 17:12:48
---

So I had this problem at work. I'm running a `virtualenv` instance on our main git repo for all my python packages. The global `.gitignore` obviously doesn't know about it the way it knows to filter out node modules and other fun bits of localization and I sure as heck don't want to add my own one line fix to the global `.gitignore` file.

So what's a girl to do? Does she just ignore that one annoying untracked file line every time she does a `git status` from the terminal? Nope, she uses git exclude.

    $GIT_DIR/info/exclude

So for me this meant I had to create a `info` folder in my `.git` folder in the repo. Then I created a file called `exclude` (no file extension). The syntax in that file is exactly like the `.gitignore` file, it's just very very local (to your computer and only for that repo).