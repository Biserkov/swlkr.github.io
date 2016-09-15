---
title: "Full stack clojure"
date: "2016-04-04"
layout: post
path: "/full-stack-clojure/"
category: "clojure"
description: "Full stack clojure, started from the server now we're here."
---

Clojure is great and all but...

How do you just send some json from a server, how do you even write server side code?
Where can you put this clojure code that runs on the jvm? TOMCAT?!

We'll go from terminal to deployed clojure app in a few steps so strap in!

<!-- more -->

The app we're going to build is going to be called "sets" and it's going to track workouts, and hopefully encourage me to work out more often.

Let's get started.

Some assumptions:

- You have java, leiningen and heroku toolbelt installed
- You're not using windows
- You have a basic understanding of clojure
- You like to learn new things
- You are willing to install stuff
- You're awesome
- The best girl scout cookies are caramel delights

```bash
$ lein new reagent sets
$ cd sets
$ lein repl
sets.repl=> (start-server)
```

In another terminal...

```bash
$ lein figwheel
```

They say if you aren't embarassed by your first version, you've launched too late.
So let's just commit and deploy right now ;)

```bash
$ git init
$ git commit -am "Initial commit"
$ heroku create name-your-app
$ git push heroku master
```

That was easy. And we're done! No I'm kidding, but still, look over the source, prepare yourself for the upcoming onslaught of datomic pull syntax and clean, terse logic.
