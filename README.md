# cljs-uuid-utils

This is an official fork of https://github.com/franks42/cljs-uuid-utils in
order to switch maintainers. Thanks Frank Siebenlist.

PLEASE NOTE THAT THE LEIN COORDINATES AND NAMESPACE HAVE CHANGED (it is no
longer a single segment namespace).

ClojureScript micro-library with an implementation of a type 4, random UUID generator 
compatible with RFC-4122 and cljs.core/UUID (make-random-uuid), 
a getter function to obtain the uuid string representation from a UUID-instance 
(uuid-string), a uuid-string conformance validating predicate (valid-uuid?), 
and a UUID factory from uuid-string with conformance validation (make-uuid-from). 
An implementation of a squuid (semi-sequential uuid) generator is also included (make-random-squuid).

## Installation

Add the following to your `project.clj` dependencies:

```clojure
[com/lucasbradstreet/cljs-uuid-utils "1.0.1"]
```

## Usage

Require cljs-uuid-utils.core namespace:

```clojure
(ns myapp
  (:require [cljs-uuid-utils.core :as uuid]))
```

REPL examples:

```clojure

ClojureScript:cljs.user> (def r (uuid/make-random-uuid))
#uuid "ec9b1b11-74b0-48a4-989c-7e939fd37dec"
ClojureScript:cljs.user> (type r)
cljs.core/UUID

ClojureScript:cljs.user> (uuid/uuid-string r)
"ec9b1b11-74b0-48a4-989c-7e939fd37dec"

ClojureScript:cljs.user> (uuid/valid-uuid? "NO-WAY")
nil
ClojureScript:cljs.user> (uuid/valid-uuid? "ec9b1b11-74b0-48a4-989c-7e939fd37dec")
"ec9b1b11-74b0-48a4-989c-7e939fd37dec"
ClojureScript:cljs.user> (uuid/valid-uuid? r)
"ec9b1b11-74b0-48a4-989c-7e939fd37dec"

ClojureScript:cljs.user> (uuid/make-uuid-from "ec9b1b11-74b0-48a4-989c-7e939fd37dec")
#uuid "ec9b1b11-74b0-48a4-989c-7e939fd37dec"
ClojureScript:cljs.user> (uuid/make-uuid-from "NO-WAY")
nil
ClojureScript:cljs.user> (uuid/make-uuid-from r)
#uuid "ec9b1b11-74b0-48a4-989c-7e939fd37dec"
ClojureScript:cljs.user> (uuid/make-uuid-from (UUID. "NO-WAY"))
nil
ClojureScript:cljs.user> (uuid/make-uuid-from (UUID. "ec9b1b11-74b0-48a4-989c-7e939fd37dec"))
#uuid "ec9b1b11-74b0-48a4-989c-7e939fd37dec"

ClojureScript:cljs.user> (uuid/make-random-squuid)
#uuid "53c5d080-6b6f-4c58-bf42-cebddef27890"
ClojureScript:cljs.user> (uuid/make-random-squuid)
#uuid "53c5d084-bc2b-47ec-add4-c1d667c8ea11"

```


## License

Copyright (C) 2012 Frank Siebenlist and Lucas Bradstreet

Distributed under the Eclipse Public License, the same as Clojure.
