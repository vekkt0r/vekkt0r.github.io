---
layout: post
title: "First Post"
description: "Short introduction"
excerpt: "Introductionary post"
date: 2015-01-11 12:13:00
categories: articles
tags: []
---

So, some years after everybody else I have finally come around to
creating a _blog_. My intent is to write about different personal
projects, both hardware and programming related. No thought that this
will be found / read by so many people but more of a experiment to
play around with documenting my projects to gain experience in
techical writing. If somebody manages to find something interesting
then that will be a nice bonus. Probably it will end up abandoned in a
while like most peoples other blogs.

Some short information about myself: IAmA EE working as a consultant
with Embedded Linux kernel and application development. Some of the
areas I enjoy spending my time off on is sensor networks, reverse
engineering, home automation and other small embedded projects.

The blog is setup using GitHub [pages] and [Jekyll] which for me as a
web-design-illiterate was very pleasant to setup and customize. Awesome to
be able to write and publish without leaving Emacs and the
terminal. With the existing themes it even looks acceptable (unlike
something I would have designed...).

_Update 2015-02-22_

_After using default Jekyll for a while I quite soon discovered that
it was not as awesome as I first though. As soon as I started writing
and wanted to include an image I found out the stock themes were quite
bad at presenting images (no scaling, if including a huge image then
it was presented in native resolution). Looking for alternatives I
tried out some different plugins but most of them required using
special liquid tags instead of normal markdown which heavily limits
the portability of the raw posts._

_For a while I used Tom theme and changed the css file to limit the
width of `img src` tag which kind of worked. Then I wanted to use some
[MathJax] formulas and discovered the deployment was no longer so
smooth because plugins are not allowed by GitHub pages (totally
understandable though)._

_Back to the drawing board... What I ended up with was publishing the
generated site instead of the Jekyll source on GitHub. There are many
examples of how to do this but none of them were as simple as just
pushing the code and letting GitHub handle generation. Feels like
something that should be built into Jekyll to be able to easily deploy
to servers without ability to generate._

_What I did was something like this (taken from [here]):_

~~~ sh
git branch -M master source
sed -i '/_site/d' .gitignore
git add .gitignore
git add _site/
git commit -m "Add _site to vc'
git push origin :master # Remove the currrent master from GitHub, had
                        # to change the default branch under the repo
                        # settings of GitHub to be able to delete
git subtree push --prefix _site origin master # Publish the contents
                                              # of _site to master branch
~~~

_Then on each change I locally run `jekyll build` and then commit the
changes before running the subtree push again to update remote
master. This way I keep both the source and generated files in the
same repo._

[Jekyll]: http://jekyllbootstrap.com/
[pages]: https://pages.github.com/
[MathJax]: http://www.mathjax.org/
[here]: http://stackoverflow.com/questions/7539382/how-can-i-deploy-from-a-git-subdirectory
