---
title: "2015 Year in Review"
date: "2015-12-29"
layout: post
path: "/2015-year-in-review/"
category: "life"
description: "2015 was kind of a crazy year for me, I mean I didn't jump out of a plane like I did
in 2013, or get married in Hawaii like I did in 2014, it was crazy for different reasons."
---

2015 was kind of a crazy year for me, I mean I didn't jump out of a plane like I did
in 2013, or get married in Hawaii like I did in 2014, it was crazy for different reasons.

First, my wife and I went to Australia and New Zealand, hiked up mountains, around lakes,
camped in the middle of nowhere, saw amazing things, and had amazing experiences. That isn't
to say that we didn't go other places domestically, like Havasu Falls, AZ, Yosemite and NY.

My wife definitely keeps my life interesting.

2015, well the second half anyway was a year of learning for me, trying to get to the
fundamentals, the things I missed majoring in Electrical/Computer Engineering
instead of Computer Science.

After I saw what facebook had done with react.js, graphql, relay and immutable.js
I realized what I had missed out on without the fundamentals. They just moved
client side web app development and with react native, mobile development forward
by at least 5-10 years. In fact they moved GUI programming in general forward for the
first time since Xerox PARC came up with MVC.

I read and watched what probably wound up being 100s of blog posts and videos about
the history of programming languages in general and I found out about lisp and books
that were written decades ago that appeared like new ideas but they were just old ideas
in new idea clothing. Most of my reading and discovery started converging on a few things.

1. [Structure and Interpretation of Computer Programs](https://mitpress.mit.edu/sicp/full-text/book/book.html)
2. Lisp and functional programming in general
3. Clojure and Clojurescript

I was always kind of fascinated by things like haskell and lisp but I never really
thought they were for me because I'm really low on the computer science totem pole.
I'm really a data janitor by trade. When you hire me, I take data from your database
and I send it your customers' web browsers in a nicely formatted user interface. Then
when your customer wants to send you something, I take their data and I inspect it,
I make sure it adheres to what your database is expecting and I put it in there.
Multiply this across hundreds if not 1000's of tables (glorified excel spreadsheets)
with relationships between them and you've got something that appears complex but it
turns out that's a lie because facebook basically replaced a large part of my data janitor
job with software.

After reading SICP (which was a journey in and of itself) the realization that I was lied to about
the complexity of programming was compounded by the fact that I kept learning about
functional programming concepts, the algorithms behind it, like immutable data structures
and why the problems I kept having at work and in my personal projects weren't really
problems in the functional programming world.

Around the time I was reaching the end of the discovery phase and the beginning of the
I want to build stuff phase, I saw David Nolen's talk about Om.Next and he coined the term Graph Query View
as a sort of successor to MVC, and that took me over the edge, that was it, I had had it with this old crappy tech,
it was all about this new tech now clojure and clojurescript. Even though clojure is older than node.js
and lisp is over 50 years old.

Cloned the tutorial project, knew to expect parenthesis but I didn't understand anything. The syntax was a lot
simpler but it definitely wasn't easier for someone who had only ever written in OOP languages before.
I mean I understood the concepts but I didn't understand what I was looking at.

OK, back to the drawing board, I basically had to start from the very, very beginning, I watched a few more
of Rich Hickey's talks for motivation, I recommend Simple Made Easy and I started a new clojure project
and followed along with braveclojure.com. Within a few hours of focused learning I had finally mastered most of
the basic concepts at least when applied to data janitor-ing.

I went so far that I wrote something I wanted coming from the koa.js framework, a super simple logger with ansi
colors. I've never actually written a "logger" before but clojure made it pretty easy.

It's named after Paul [Bunyan](https://github.com/swlkr/bunyan) because you know he's a
lumberjack and it's a logger middleware so that's clever. Unlike some of the other loggers
I've seen it doesn't have any dependencies and it doesn't require any configuration. It also
does exactly what I want, just print to the terminal with the url, http method and the response time.

My journey to enlightenment this year has reached a local maxima with me understanding a
much wider scope of the history of software development and the very edges of functional programming along
with the very basics of the algorithms, combinators, compilers and lambda calculus underpinning it all.

2015 was crazy and enlightening, 2016 is the year I will graduate from the computer science school of hard knocks
and hopefully write my own lisp which actually compiles and repls, write a graphql parser in clojure, finally understand datalog, and write something profitable with my new found super powers.
