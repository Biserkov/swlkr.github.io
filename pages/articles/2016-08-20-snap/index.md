---
title: "Snap"
date: "2016-08-20"
layout: post
path: "snap/"
category: "clojurescript"
description: "Dealing with restful APIs from a react based web app can be very ad hoc and informal."
---

Dealing with restful APIs from a react based web app can be very ad hoc and informal.

Do I put the call to get the state of this list component into componentDidMount? Do I put it in componentWillMount?

Should I put this post request in the parent component or the child component with the items?

What do I do when I have to keep multiple components in sync with the other components and the server? One large parent component with props all the way up from the children? Context?!

Enter clojurescript
---

Well the clojurescript community has had the answer to the first part about keeping all of the child components in sync when a child changes a piece of data: global state atom. When the page loads, a sort of "app database" is created which stores everything related to the app, so you can change pages with push state and not have to refresh from the server if you didn't want to.

The second part however, keeping the global state in sync with the server is being worked on and there are several solutions to choose from:

- Replace your crappy rest API backend with a graphql one and use relay
- Replace your crappy rest API backend with a falcor one and use falcor
- Replace your crappy rest API backend and your crappy relational database with datomic and use pull syntax to query the database directly with filters for auth and permissions

Those solutions are all fine and I think they represent the future of server side code in varying degrees, but they also add a bit of complexity where you may not need it.

What if we applied react's virtual dom diffing idea to the global state?

Light bulb 💡
---

If we're going to do this, we'll need to formalize the "shape" of the global  state.

1. Everything needs a name

    This:
    ```clojure
    {:posts [] :comments: [] :post {} :comment {}}
    ```

    Not this:
    ```clojure
    [{} [], {} []]
    ```

2. Zero nesting

    This:
    ```clojure
    {:posts [{:id 1 :title ""}
             {:id 2 :title ""}]
     :comments [{:id 1 :post_id 1 :content ""}
                {:id 2 :post_id 1 :content ""}
                {:id 3 :post_id 2 :content ""}]}
    ```

    Not this:
    ```clojure
    {:posts [{:id 1 :title "" :comments: [{:id 1 :content ""}
                                          {:id 2 :content ""}]}]}
    ```

And that's it, with those two rules we can diff global state atoms easily and return data representing restful urls. Here's how it works.

A working example
---

```clojure
(ns your-project.core
  (:require [snap.core :as snap]))

; define your remotes
; a remote is a map between your api and the keys in
; the global state
; notice remotes has :posts and :comments and so does the state
(def remotes {:posts {:get "/posts"
                      :post "/posts"
                      :put "/posts/:id"
                      :delete "/posts/:id"}
              :comments {:get "/posts/:id/comments"
                         :post "/posts/:id/comments"}})

; current state
(def state {:posts [{:id 1 :title "title"}]
            :comments [{:id 1 :post_id 1 :content ""}]})

; pure function transforming state
; takes existing state and new value
; returns new state
(defn add-post [state post]
  (let [{:keys [id title]} post]
    (update-in state [:posts] conj {:id id :title title})))

; new state
(def new-state (add-post state {:id 2 :title "new title"}))

;
(snap/build-http-requests state new-state remotes)
; => [{:url "/posts" :method :post :body {:id 2 :title "new title"} :key :posts}]
```

A few more examples
---

_Updates_
```clojure
; in this simple example, only one remote matching the :post key
; from the global state is needed
(def remotes {:post {:put "/posts/:id"}})

; update to an item
(def state {:post {:id 1 :title "t" :content "c"}})

; just pretend that there was a function that did this
(def new-state {:post {:id 1 :title "title" :content "content"}})

; diff it!
(snap/build-http-requests state new-state remotes)
; => [{:url "/posts/1" :method :put :body {:id 1 :title "title" :content "content"} :key :post}]
```

_Deletes_
```clojure
; in this example, the key :posts from the state
; is matched with a delete http method or verb and a url
(def remotes {:posts {:delete "/posts/:id"}})

; starting state
(def state {:posts [{:id 1 :title "" :content ""}
                    {:id 2 :title "" :content ""}]})

; just pretend that a function did this
(def new-state {:posts [{:id 1 :title "" :content ""}]})

(snap/build-http-requests state new-state remotes)
; => [{:url "/posts/2" :method :delete :body nil :key :posts}]
```

_Nested resources_
```clojure
; in this example, the key :posts from the state
; is matched with a delete http method or verb and a url
(def remotes {:comments {:put "/posts/:post_id/comments/:id"}})

; starting state
(def state {:comments [{:id 1 :post_id 1 :name "n" :content "c"}]})

; just pretend that a function did this
(def new-state {:comments [{:id 1 :post_id 1 :name "name" :content "content"}]})

(snap/build-http-requests state new-state remotes)
; => [{:url "/posts/2/comments/1" :method :put :body {:id 1 :post_id 1 :name "name" :content "content"} :key :comments}]
```
