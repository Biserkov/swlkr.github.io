---
title: "Why clojure why now?"
date: "2016-03-28"
layout: post
path: "why-clojure-why-now/"
category: "clojure"
description: "Clojure is slow to start, it's not the fastest once it gets going either. It runs on the JVM and has interop with java which is my least favorite language. The stack traces are terrible, bugs are easy to create and large refactoring is difficult without a lot of well written, well thought out tests."
---

Clojure is slow to start, it's not the fastest once it gets going either. It runs on the JVM and has interop with java which is my least favorite language. The stack traces are terrible, bugs are easy to create and large refactoring is difficult without a lot of well written, well thought out tests.

There's a lot to dislike about clojure, so why would I choose to write clojure and why would I start in 2016?

I've written a lot of programs in statically typed languages, statically typed in the sense of types written so the compiler can generate faster running code, not in the sense of typeclasses like something like haskell or ocaml. There's some nice properties of statically typed languages like c, c# and java:

- One canonical model to represent things that come from outside of the system
- Every function returns a static type and takes parameters that are static types, so large refactoring is a breeze. The compiler will tell you what you broke.

There's also some downsides:

- One canonical model to represent things that come from outside of the system
- Things like composition are harder to accomplish
- Writing tests is usually less straightforward (at least in java/c#)
- Static types mean less flexibility in terms of higher order functions

I've also written a lot of programs in dynamic languages, as in the compiler or interpreter figures out the types and you don't type them. There are some nice properties of dynamically typed languages like ruby and javascript:

- It's simple to model data from multiple systems over time.
- Composition (code re-use without the gorilla banana problem of inheritance) is a lot simpler
- Writing tests is simple and straightforward

Along with the downsides mentioned earlier.

Clojure however takes the upsides and makes the downsides seem tiny in comparison. Clojure doesn't have:

- static types
- much syntax at all
- inheritance (kind of)
- and a whole bunch of other stuff

There's a lot more to it, but why clojure, why now? It is the simplest way to write maintainable, complex systems quickly.
