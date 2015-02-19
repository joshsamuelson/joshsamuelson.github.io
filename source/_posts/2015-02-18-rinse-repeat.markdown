---
layout: post
title: "Rinse Repeat"
date: 2015-02-18 09:51:58 -0800
comments: true
categories: 
- musings
- tech
- puppet
---

The last few months have been a major crash course for me in configuration management and Puppet in particular. I wouldn't call myself an expert at least considering what counts as a puppet expert at Puppet Labs, but I feel like I know enough now that I could easily do my previous job almost entirely using puppet. A big part of my job now is building VMs that we will use in the classroom. The part that has really changed my perspective is how freely I can now throw something away that doesn't work. My attitude with computers has often been that if something is seriously screwed up, it's often simpler and faster to just start fresh rather than figure out some arcane issue. This is espeically true with Windows desktops OS's. It's also why I get a little annoyed when someone asks me to fix their computer, because if it were mine, I would just wipe it out and start fresh. Doing that too often can be a big pain and with servers it can be seriously risky because it's easy to miss something important.

That's where puppet has really changed my perspective. I realized that I no longer think of the server (or the VM image in my case) as the "thing" I'm managing, that's just the expression of the real thing. The puppet code is what I'm managing and maintaining. That let's me make and undo small changes as I work toward improving things, without having to worry how undoing a change might cause issues down the line. It's so easy to start fresh that I don't mind trying something out, throwing away the result, and trying another variation until I find the right solution.

I think this isn't quite what puppet has been used for, or maybe what it was initially intended for, but I think it's really the future of how people will manage most of their systems. Puppet is a great tool for addressing drift, i.e. when something has changed on one system that should otherwise be identical to the others. In the long run, I think it's going to become simpler to just trash a system that has drifted and redeploy from the code. 

If you think of it in terms of software its more obvious. If a piece of compiled software becomes corrupted, say because of an issue with the disk, you would never go in to the file and try to repair it so that it matched a known good copy. No, the correct thing to do in that case is to simply redploy the file. Now that so many servers are virtualized or containerized, I think it makes much more sense to think of them as files.

What's been remarkable about this for me is how much it's shifted my thinking. Even when working on projects at home I find myself wanting to set things up in puppet just so I don't have to worry about it when I need to start fresh. It also has me doing something I'd never bothered with before for person tinkering, documentation. I'm actually documenting my work as I go by writing the puppet code.
