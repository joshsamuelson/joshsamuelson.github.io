---
layout: post
title: "Control Stack"
date: 2015-03-15 09:22:34 -0700
comments: true
categories: 
- musings
- productivity
- gtd
---

One idea that keeps kicking around in my brain is how hard it is to get back to work after being interrupted, and how computers are able to handle that with ease. I wonder if it might be possible to deal with interruptions the way a computer handles a Control Stack. For the uninitiated, let me explain how a computer deals with things.

For a simple program here's how it works: The computer goes merrily along performing the actions you give it, for example if you tell it something like `print "hello"` it will print out "hello" and then move on to the next thing. Maybe the next thing is `print 2 + 2` and it'll print out "4" and so on. That's all pretty useless and boring until you add the ability to interrupt what it's doing.

Those interruptions take the form of functions. So, if you wanted to do something fancy, like count the number of letters in a word, you'd use a function. That might look something like this `print number_of_letters("hello")` "number_of_letters" is the name of the function and "hello" is the word we're counting. Assuming we've defined "number_of_letters" somewhere (or someone else has and we're using their library of functions) we'll see "5" printed out on the console. But here's the thing, the computer has to remember where it was before it went off to count out those numbers.

The way the computer handles this is with a data structure called a stack. A good analogy is when you're reading a book and you find a word you don't know. Now you could place a bookmark in the book and close it, then grab a dictionary and open that and find your word, close the dictionary and open your book at the bookmark. But keeping track of that bookmark is a hassle, a smarter way is to set the dictionary on top of the open book and find your word. When you're done with the dictionary, you can move it out of the way and pick up where you left off. That's how a control stack in a computer works, execpt it stacks many more levels, a bit like if you're reading a book in a Spanish you might need to look up a word in a Spanish/English dictionary and if you didn't understand the English you'd need to look that word up in an English dictionary.

The computer is able to handle a huge control stack and it allows you to do some fancy stuff. For example, for our "number_of_letters" function we could write it some thing like this:

    define number_of_letters(word_to_count)
      count = 0
      for each letter in word_to_count
        add 1 to count
      return count
    end

I hope that's clear enough for people who don't know programming, I don't want to over explain.
That way of doing it is fine, but there is another way of defining that function that makes use of the control stack and it's called "recursion"

    define number_of_letters(word_to_count)
      if word_to_count is blank
        return 0
      else
        return number_of_letters(word_to_count minus the last letter) + 1
    end

So if we're using it will "hello", first it tries "hello", then "hell", then "hel", then "he", then "h", and finally it's blank. Like the stack of dictionaries, as it closes each function, it sends back a value as it looks it up. The number of letters in nothing is 0, so it picks up where it left off which was `number_of_letters("h")`. But now that it closed that top "book", all it has to figure out is "0 + 1", so `number_of_letters("h")` returns 1 and we can close that "book" and pick up where we left off with `number_of_letters("he")`. Since we've figured out `number_of_letters("h")` is equal to 1, we'll return 1 + 1 from `number_of_letters("he")`, so `number_of_letters("hel")` will return 2 + 1, and so on.
This is a trivial example of recursion, but it can be incredbily powerful and it can save a ton of keeping track of the counts of things and elaborate loops. It also let's you make the computer smarter. All it needs to know how to do is check if a word is blank, how to drop the last letter from a word, and how to add. Hopefully this isn't too hard to understand for someone who doesn't know programming.

The point is, that the computer handles all of this with ease because it has the control stack, it adds new tasks to the top of the stack and removes them as their completed and painlessly picks up where it left off. What if we handled interruptions in the same way?

Here's a human example: Checking your email when you start work in the morning.

Say you open your email and see there are 10 new emails. So you start from the top, and read the first one, 

So here's what your stack looks like:

- Check Email
- Read First Email

Except, that isn't quite right. Even though that's the order you did the things, in a stack the first thing is on the bottom. As you add new tasks, they get put on top.

So the stack is really this:

- Read First Email
- Check Email

The first email is about how you're long lost relative in Nigeria has left you a substantial fortune and the sender just needs some money up front to pay the bank transfer fees. After reading that, your stack would look like this:

- Delete SPAM
- Read First Email
- Check Email

But at that point you decide that you want to complain to the IT department about all the SPAM you'd been getting, so before you delete it you send an email to IT.

- Send Email to IT about SPAM
- Delete SPAM
- Read First Email
- Check Email

Once you've sent the email to IT, you remove it from the stack (or to use the CS term, "pop" it off the top of the stack). So know you're back to this:

- Delete SPAM
- Read First Email
- Check Email

So you delete the SPAM, and pop that off the control stack, and since that was the first email, you can also pop "Read First Email" off the stack. That puts you back to this:

- Check Email

Now there are 9 emails left so you follow the same procedure. Since you deleted the SPAM, the 2nd message now become the "first"

- Read First Email
- Check Email

This one turns out to be from your boss saying "Turn in your TPS reports, they were due yesterday!". Which makes you realize that you need to actually write the reports before you can turn them in so your stack turns into:

- Finish TPS reports
- Email TPS reports to boss
- Read First Email
- Check Email

And as your working on the reports you need to contact other people, look things up, get drafts reviewed, etc., etc. And everything is going fine until someone from IT comes by and asks about the SPAM email you contacted them about or you go to get a cup of coffee and someone mentions something else you need to be working on or your dentist's office calls to remind you about your root canal tomorrow. Or all of those things plus the other 8 messages that you haven't even looked at yet. And unlike the computer, your brain loses its control stack and you don't remember that you need to finish the TPS reports until you get an email from your boss saying "Your reports are two days late!"

Ok so, I know it's not realistic, who only has 10 emails in their inbox every day.

My idea is somewhat simple, just use a stack of sticky notes to emulate the control stack. That way, even if you get 10 interruptions you could still jump right back to working on those TPS reports. Now, I've seen people use sticky notes to keep track of work and usually it takes the form of a decorative fringe around their computer monitor, with every blank surface covered. That is not what I mean. I'm talking about a simple stack, whatever currently has your attention is on top. So you intentionally can't see what's underneath until you're ready to work on it. If something else comes up, just add another note to the top.

So yeah, that's a little wasteful of sticky notes. Maybe a better idea would be to always keep a blank note on top. Then as you're working along if you get interrupted you can just write on that note what you were doing. Once you deal with the interruption you can go right back to whatever that note says and the one below it when that's done and so on. That keeps focus narrow, you don't have to hold all the to-dos in your head while you're doing one of them.

It might even work with a Kanban style system. As interruptions come, sometimes they don't need to be completed, but simply recorded and added to the backlog. So the control stack would always have "grab task from backlog" at the bottom. Or in reality it would have "Plan next project" at the bottom, something like this:

- Do subtask
- Do task
- Grab next task from backlog
- Plan next project

Although, most people probably don't need something like "plan next project" at the bottom since once you've cleaned everything out you usually know how to decide what you want to do next.

Well, there's the idea and probaly way over exlained. I'm going to try it out, I've been doing pretty well at work getting my tasks done, but I think I end up wasting time and mental effort because I'll get interrupted and need to remember what it was I was working on. This was much worse at previous jobs, where I was interrupted all the time.

I'll report back on how it's going, I can already think of tools that might improve the process like a simple app to keep track of the stack.
