---
title: "New blog site"
date: 2018-10-21T22:50:02+03:00
---

I wanted to do this for a long time. The old blog site at blogspot was
always supposed to be something temporary. It lasted five years...

I never really liked the look of the old blog site that much. And there
weren't that many options to customize it in the first place. The
WYSIWYG editor was ugly and difficult to work with. And it was hard to
prepare content and post it later. I could create new posts in HTML
though and that's how I ended up creating all previous posts. I would
first write the post in [txt2tags](https://txt2tags.org/) markup,
convert that to HTML and create a new post with that. But then, editing
existing content was cumbersome too.

On the other hand, I always liked static site generators. I've used them
on several occasions too. I started up with
[Jekyll](https://jekyllrb.com/), which has an astonishing number of
features, but it was a burden to install in
Salix. There are lots of different Ruby dependencies involved and I
didn't want to have to install all of them on every PC that I wanted to
edit the site from. It was possible to contain all that in a Python
virtualenv and I was using it like that for a while, but in the end it
was too much tinkering with tooling. I wanted something simpler. I
tried a few other static site generators, but in the end I ended up
with [Hugo](https://gohugo.io). It's just one binary, I find it much
simpler to use and it's also really fast.

So, the new blog site is built with Hugo and is hosted
at Github, using [Github Pages](https://pages.github.com/). I found a
[theme that I liked](https://themes.gohugo.io/hugo-theme-even/),
[tweaked it a bit](https://github.com/gapan/hugo-theme-even) to match Salix
aesthetics and just went with it.

Github Pages was not a real option until a few months ago, when they added
support for HTTPS for all sites with a custom domain that are hosted
there. I could have always uploaded the blog at one of our servers, but
not having to maintain yet another thing is always nice. In fact, I'm
thinking of moving the main website over to Github Pages with a similar
setup. And maybe even our [wiki](https://docs.salixos.org/), since
content is not really updated that often and contributors are very few.
A Hugo theme like [DocDock](https://themes.gohugo.io/docdock/), or
[Material Docs](https://themes.gohugo.io/material-docs/) would possibly
fit fine, but it would take some effort to convert all existing content.

Since Github only supports Jekyll natively for automatically building
the website, I needed to find a way to have at least a semi-automated
way to build and update the content. While there are some instructions
in Hugo's documentation on how to do that, I wasn't particularly happy
with any of them. So I ended up doing something a bit different. I have
everything detailed in my
[personal blog](https://vlahavas.com/posts/20180919-hugo_with_github_pages/).

All in all, I like the new setup. It looks nice and it's really simple
to create new posts using markdown.  And who knows, maybe I'll get to
update this a bit more often than the old one.
