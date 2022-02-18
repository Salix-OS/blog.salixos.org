---
title: "New Website Design"
date: 2013-10-22
draft: false
tags: ["pelican", "txt2tags", "website"]
author: "George Vlahavas"

autoCollapseToc: true
---

As many might have noticed, we now have a new main website design!

Since the Salix project was started, the main website was actually a
part of our wiki, which is using the MediaWiki engine. That had one main
advantage, which at that time seemed enough to justify that choice; we
would use a single CMS to manage both our wiki and our main page. So, we
created a custom MediaWiki theme that would look good as a main project
page and as a wiki. And admittedly, that worked fine for several years!

During the last months though, disadvantages started to become obvious.
What happened first was that the latest updates to the MediaWiki
software broke our custom theme. So, that meant that we should either
fix that custom theme (which mostly meant writing it from scratch again)
or separate the main page from the wiki and use the wiki with a
standard MediaWiki theme. We went for the latter option as that was
considerably less work! So, the wiki would look more like any other
MediaWiki based wiki out there, but we were free to upgrade it to
newer versions, covering security issues without thinking of what it
will do to our main webpage.

That left us hunting for a system to manage our main page. The first
option we tried was [Pelican](http://blog.getpelican.com/).
It really looked like a good choice.
The content was written in simple markdown and then using Pelican we
would take that markdown and transform it into a full website that
Pelican could also upload and sync to the main server. And what
Pelican created was simple HTML content. No database was needed to
run in the background and there was no PHP content anywhere. Nice
and simple. The fact that the content was plain HTML, would mean
that the website would be less prone to attacks. Also, the fact that
[kernel.org](http://blog.getpelican.com/)
also used Pelican for managing their website was very
reassuring too. So, we took the Pelican theme that kernel.org was
using, tweaked it a bit and that looked good and very close to what
we wanted!

The advantages of using such a system became apparent shortly after
we switched. Unfortunately, we had hardware troubles with the server
that hosted our main page, our wiki and our forums. The MySQL
databases that the wiki and forum were using would become corrupted
and the wiki and forums would stop working. It took us a while to
realize that this was actually caused by a hardware problem. We
first thought that it was a hard drive in the RAID array failing,
but all hard drives passed any tests without problems. Then, since
we were getting filesystem errors constantly, we thought that it may
be the hard drive controller card, but that looked OK too. It turned
out that the mainboard was faulty, so after a mainboard replacement,
everything was back to normal again. But during all that time, the
wiki and forum was mostly down, but at least our main page was
working! The fact that it was only static HTML pages and it didn't
need a database or any code for that matter running on the server
made it work with no problems with even such severe hardware errors!


So, Pelican looked indeed like a very nice choice! And it worked
nicely as our main page for a month or so. Serving static content is
also a lot faster than serving a complex CMS, the main page would
load a lot faster than before. But then trouble started again. I
wanted to update some content on the main page. For generating the
main page, we had originally used Pelican 3.0 and that was what I
had installed on my laptop which I had used then. Unfortunately, I
had forgotten that laptop at my parents house after a weekend visit
and wasn't going to get it back for at least another couple of
weeks. So, I went ahead and installed Pelican 3.3 at the laptop I
actually had with me, which was now the latest version (and the one
that was easier to install using pip). And then realized
that everything was broken. The upgrade from Pelican 3.0 to 3.3,
meant that the theme that we were using needed a major restructuring
(possibly a complete rewrite) because it wouldn't work at all any
more. So, we either had to do that, or switch to something
different, once again. During all that time, it also became apparent
that Pelican was mostly suited to writing blogs, instead of mostly
static content which is what we wanted. It could create static
content, but it's main thing is really blogs...


It was then that I remembered that I was already using a tool that
could create simple, static HTML content using simple markdown. I
was already using [txt2tags](http://txt2tags.org/) to create man pages for all the system
tools that you can use in Salix, but it can also create HTML pages
too (among over a dozen other different output formats). So, maybe
it was simpler to switch to txt2tags. And it was! txt2tags can be
used to create simple HTML pages and those pages can look like
anything you like, using CSS! That is an even simpler system than
Pelican and closer to what we were looking for in the first place.
The txt2tags website itself is written in txt2tags as are a number
of other different websites which you can find on the txt2tags
website. I liked the looks of the txt2tags website so much that I
used exactly the same CSS, with only minor changes. So, that is why
both pages look very similar.

In the spirit of Pelican, I created a simple Makefile that would
help with generating the static HTML content and also with updating
the main webpage with it. Everything is online in my
[github repo.](https://github.com/gapan/www.salixos.org)

If in the future we decide to switch to a different look, it's just
as simple as using a different CSS. Since the txt2tags syntax is
highly unlikely to change, our main page is now beautiful, fast,
more secure and future-proof!

I'd like to thank Thorsten for all his work with our wiki, forum and
Pelican website. I'm mostly ignorant of how it all works...