---
title: "On Display Managers"
date: 2019-07-05
tags: ["packages", "GDM", "default apps"]
author: "George Vlahavas"

autoCollapseToc: true
---

A Display Manager is the application that provides a graphic user
interface (GUI) that is displayed at the end of the boot process and
lets the user authenticate themselves by providing their username and
password, before entering their preferred X11 session, for example
Xfce, KDE, fluxbox, etc.

Up until Salix 14.2, we've been using a very old version of GDM as the
default display manager. Actually we've been using the same major
version of GDM, which is 2.20.x since the first release of Salix, 10
years ago! The version that we have been using since 2010, is 2.20.11,
which is the last release in that branch.  Thankfully, it doesn't
seem to have any major bugs. But still, hanging on to a very old
and unmaintained release such as this, obviously has its problems.

So why don't we just use a newer version of GDM? Well, since GDM 2.22,
the Gnome devs decided to integrate it further with their entire
desktop, so it depends on gnome-panel. The gnome-panel package in turn,
requires almost all of Gnome as dependencies. Essentially, what they
did, is that the tied GDM to Gnome. So, even if you want to use it to
launch Xfce, you'll need to have most of Gnome installed. That simply
won't work for Salix. To add to that, even newer versions of GDM, also
require PAM and Systemd. While there is no other reason to do it, we
could possibly include PAM, but Systemd is completely out of the
question. So, newer versions of GDM are definitely out.

What about other display managers then?

The LinuxMint folks have decided to fork an old version of GDM and
create MDM, which stands for MDM Display Manager. I tried to package it
for Salix and test it, but there were a lot of compilation errors. I
started fixing them one by one and the build process continued. But then
I realized that MDM depends on webkit for some reason. They seem to have replaced
the renderer with one based on webkit, probably borrowing code from
newer versions of GDM.
Plus, it seems that MDM is not even used by LinuxMint anymore, I think
they probably switched to LightDM, along with almost every other Ubuntu
derivative. So, no reason to switch from one unmaintained display
manager that still works OK, to another unmaintained display manager,
that we haven't tested and needs extra dependencies.

So, why not just use LightDM then? It seems to be the choice by lots of
distributions out there after all. To be honest, I haven't tried it, but
I know it needs PAM. There's no way around it, so if we want to switch
to it, we must adopt PAM. The problem is that PAM introduces a ton of
complexity, that is not at all needed by a desktop distribution and
that's probably the reason why Slackware hasn't included it yet either.
I really want to avoid having to include PAM if we don't really really
really have to.

What other choices are out there? There is of course LXDM, the display
manager 
provided by the LXDE project. We can make this work for Salix. It has
actually been updated to use GTK+3, so that's some progress. But still,
the latest available release is from 2015. It seems that this one isn't
actually maintained by its developers anymore. Distributions offer some
patches that fix some issues that the latest released version has, but
I'm not sure we can depend on accumulating patches for such a crucial
piece of software. Additionally, while it does work, it is not as
feature-rich as our old version of GDM is. There is no GUI configuration
app and honestly, I don't find it as good looking as our old GDM is. So,
if we were to swap our old GDM with LXDM, we would switch to an inferior
option.

Then of course there is Slim. This could work too, but is even more
spartan than LXDM, there is also no GUI configuration app for it. What's
more, it hasn't had a commit to its codebase since 2013.

XDM is the standard X11 tool for the job. But apart from offering a
dialog for the user to input his credentials, it offers no other
functionality. Plus, it's ugly. Admittedly, some Slackware users
have been doing some
[interesting things with it](https://www.linuxquestions.org/questions/slackware-14/%5Bann%5D-xdm-slackware-theme-2019-0628-a-4175656722/).
But still, although impressive, this is nothing more than a (nicely done) hack.
There is still no GUI configuration tool, and even localization would
probably be impossible. I can see this being a nice choice for a
personal setup, but not as the default DM for a distribution.

WDM is another long unmaintained display manager, that is a fork of a
much earlier XDM release. It is written using the WINGs toolkit, so it
would look a little out of place in Salix.  Well, not if we had a
WindowMaker release :P. Still, I took a brief look into its code,
because the GUI part is detached from the rest of the
program, I was thinking that maybe I could replace the WINGs
login window with a GTK+3 one and keep the rest of the app
as is. Unfortunately, WDM does not support any kind of
dynamic discovery of desktop environments or window manager
sessions using the standard .desktop files. What it does, is
that it has hardcoded some of them in the code. This is not
really an option if you want to be able to launch a desktop environment
or a window manager that the WDM developers weren't aware of. Adding
that functionality myself would be more than I bargained for. Oh, did I
mention that it has been completely unmaintained for almost 10
years now?

KDM, from the KDE project, is one that was used as the default display
manager in Slackware for ages. It has now been superseded by SSDM.
However, SSDM, as KDM before it, requires Qt and I wouldn't want to add
this huge dependency on a default installation. The qt5 package in 14.2
is about 55MB. That's too much additional space for a distribution that
doesn't include any other Qt applications by default.

So where does all this leave us? I'm not sure. We seem to be out of
options for the next release, whenever that will be. Anything we choose
to replace the old GDM package, will be in one way or another, inferior.
The thought of forking the old GDM and assuming its maintainance has
crossed my mind, but I don't think I have the time to do it.