---
title: "Side effects as data"
date: "2016-09-15"
layout: post
path: "/side-effects-as-data/"
category: "clojure"
description: "One thing Ive noticed about programming in clojure is that usually there is a separation of functions that return data and functions that use that data to perform what are usually called side effects. By that I mean operations that when performed may have a different output even when given the same exact input."
---

One thing I've noticed about programming in clojure is that usually there is a separation of functions that return data and functions that use that data to perform what are usually called "side effects." By that I mean operations that when performed may have a different output even when given the same exact input.

So to make these functions easier to manage, there's always three functions that correspond with any side effect-y function.

The first function is the pre-side effect function. This functions only responsibility is to take its inputs and combine it into a hash map with keys and values that make sense for the side effect-y function.

The second function then takes that hash map and performs the side effect, network call, reading/writing to disk, that sort of thing.

The third function takes the output of the side effect function and does anything it needs to do.

That's it! It sounds like more work than just doing it all in one function and it is, but when you have these three separate functions, you're in the pit of success and it's hard to cause bugs this way.

Here's a more concrete example for a network request:

```clojure
; pure function to start
(defn build-request-map [env id]
  {:url (str (env :base-url) "/resource/" id)
   :method "PUT"
   :body {:prop "val"}})

; side effects go here
(defn send-request [req]
  (http/request req))

; pure function here
(defn parse-response [response]
  (json/parse (:body response))

; wrap it all up in an easy to use function
(defn update-resource [id]
  (-> (build-request-map env id)
      (send-request)
      (parse-response)))
```

There is one more benefit of doing things this way: easy testing. Since your side effect function is usually a dependency or library function that has already been well tested, there's really no point to test it. So when it comes time to test your code, you only have to test the pure functions with various inputs (error inputs, invalid inputs) and then you're covered and you can rest assured that your code will work in all kinds of situations!
