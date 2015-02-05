---
layout: post
title: "Learning with instant feedback"
date: 2015-02-04 17:50:04 -0800
comments: true
categories:
- tech
- musings
- learning
- puppet
---

I recently watched this somewhat mind-blowing video <link to instant feedback video>. I know he's making a larger point about purpose in life, and I think he's got a point, but really the part that blew me away was the idea of instant feedback not just as a "crutch" for learning, but as he put he "writing code without a blindfold on". It also occurs to me that part of the reason more people don't code is because it involves different parts of the brain, you have to constantly visualize data and what's happening inside the code while at the same time using your analytical brain to actually create the code.

I know there are people who can do this, to some extent, I'm one of them. But, I also know that I sometimes have trouble forming complete sentences when I'm deep in hack mode working on some problem. It's also why something like IntelliSense in VisualStudio is so popular, it gives you instant context.

I used to think of that kind of think as cheating, a crutch for those who couldn't remember how to do things. In retrospect, that attitude is probably what kept me from doing more coding after college. It's also an attitude that was reinforced in my CS classes.

Now that I actually have to do some programming as part of my work, I don't really care about cheating. I'll happily use every trick in the book to make things better or build them more quickly. This is especially true of copying or repurposing what others have done (with proper attribution obviously).

With that in mind, I've been trying to think of ways that I could make writing puppet manifests have a little more instant feedback. Khan Academy has a great project here http://github.com/khan/live-editor that they use for teaching basic programming with JavaScript. It allows a student to write their code and see the results even before they're finished. This makes errors like missing semicolons at the end of a line almost impossible, because the feedback is so immediate.

I think some of the could be translated to puppet. For example, as a student types code into an editor, puppet-lint could be checking the syntax live. That shouldn't be too tough and could maybe even be done by adapting Khan's editor and just wiring it up to a different output. But the output of puppet is more tangible, in order to check the results of a manifest, it needs to be applied to an actual node and then the node's state needs to be checked.

There are a few pieces to this puzzle:

* A responsive editor with live feedback on code
* A sandbox environment where puppet code can be tested
* Serverspec (or similar) tests with a live display of environment status
* Some way of arranging the whole thing

This isn't really on my official project list, but I'm going to try to tackle this one. I'll also write up as much as I can and make a blog series out of it.
