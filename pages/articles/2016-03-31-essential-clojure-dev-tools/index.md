---
title: "Essential clojure dev tools"
date: "2016-03-31"
layout: post
path: "essential-clojure-dev-tools/"
category: "clojure"
description: "It's 2016, not 1958, the tools for writing lisp (clojure) have evolved. No one balances or even sees parens anymore. Here are the essential tools you should be using to write clojure and clojurescript code."
---

It's 2016, not 1958, the tools for writing lisp (clojure) have evolved. No one balances or even sees parens anymore. Here are the essential tools you should be using to write clojure and clojurescript code.

<!-- more -->

### [parinfer](https://shaunlebron.github.io/parinfer/)

If you use one tool to write clojure with, this is it, it turns clojure into a whitespace significant language. Don't balance parens.

### [atom](https://atom.io)

Atom + [vim mode](https://github.com/atom/vim-mode). It's not emacs or cursive but it gets the job done

### [figwheel](https://github.com/bhauman/lein-figwheel)

Stop reloading your browser and losing your app state. Immediate feedback is the only way to program (one advantage over statically typed apps I never went over)

### [test-refresh](https://github.com/jakemcc/lein-test-refresh)

Writing tests is essential and getting quick feedback from them is too. Have your tests running once you hit save

### [mount](https://github.com/tolitius/mount)

Clojure startup time is slow. So don't ever restart a repl again. Use mount!

I'm sure there's more I'm missing, but these are all necessary to keep you in the zone and writing clean, clear, ambitious code.
