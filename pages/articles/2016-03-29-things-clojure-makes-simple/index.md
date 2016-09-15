---
title: "Things Clojure Makes Simple"
date: "2016-03-29"
layout: post
path: "/things-clojure-makes-simple/"
category: "clojure"
description: "There's quite a few things that clojure makes simpler.

Some high level ones are:

- syntax (or lack thereof)
- composition
- async
- immutability

But there are tons more!"
---

There's quite a few things that clojure makes simpler.

Some high level ones are:

- syntax (or lack thereof)
- composition
- async
- immutability

But there are tons more!

<!-- more -->

Destructuring

```clojure
obj === {:x 1 :y 2 :z 3}

(let [{:keys [x, y, z]} obj])
```

Async

```clojure
(go
  (let [response (<! (http/get "http://example.com"))))  
```

Composition

```clojure
(filter (comp not zero?) [0 1 0 2 0 3 0 4])

; instead of this
(first (.split (.replace (.toUpperCase "a b c d") "A" "X") " "))
; => X

; we can write functions like this
(-> "a b c d"
     .toUpperCase
     (.replace "A" "X")
     (.split " ")
     first)
; => X
```

Immutability

```clojure
(def counter (atom 0))

(defn increase-count []
  (swap! counter inc))

(increase-count)
(increase-count)
(increase-count)

; @counter
; => 3
```
