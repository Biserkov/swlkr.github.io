---
title: "Clojure, SQL and You"
date: "2016-03-30"
layout: post
path: "/clojure-sql-and-you/"
category: "clojure"
description: "Data access made simple"
---

Having a difficult and time consuming time writing dozens of classes just to represent data from your database?

Finding yourself writing sql statements in your code?

How much of your app do you think is data access code?

How much do you think is really necessary?

Well I'm here to tell you that you don't need to write that stuff anymore. I'm not talking about ORMs, or a query builder with some strange dsl. I'm talking about a true separation of concerns. I'm talking about [yesql](https://github.com/krisajenkins/yesql).

Yesql is the last sql library you'll ever need. And then once you switch to datomic, you'll never need any sql ever again.

Your SQL goes in SQL files, and yesql creates functions from the SQL files automatically. All you have to do is pass a connection string and parameters. Behold:

```sql
/* sql/users.sql */

-- name: users-by-email
select *
from users
where email = :email

-- name: users-by-id
select *
from users
where id = :id
```

```clojure
(defqueries "sql/users.sql"
   {:connection db-spec})

(users-by-email {:email "hi@example.com"})
; => ({:email "hi@exmple.com" :id 1})

(users-by-id {:id 1})
; => ({:email "hi@exmple.com" :id 1})
```

Use it, love it. Don't fear the SQL.
