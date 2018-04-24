---
title: "Unit Testing vs Design by Contract"
date: 2018-04-22T21:43:59+03:00
draft: false
---

In the first half of [The Pragmatic Programmer](https://pragprog.com/book/tpp/the-pragmatic-programmer) Andrew Hunt and David Thomas introduce concept of Design by Contract (DBC, for short).[^1]

In order to determine correctness of the program three questions must be answered:

1. What does routine expect?
2. What does routine guarantee?
3. What does routine maintain?

For example, Python can support this via [`assert`](https://docs.python.org/3/reference/simple_stmts.html#assert) statements and [`invariant`](https://en.wikipedia.org/wiki/Invariant_(computer_science)) methods. But there is no native support in it as in Eiffel.

In second half of the book the concept of Unit Testing is explained. Writing tests can ensure to a first approximation previous three questions.

Let's imagine if just only one of this concepts is practiced. For example, a Design by Contract?

For now I want to emphasize just two points:

* Bad customer experience. Assertions and invariants tends to be happen not in development environment but somewhere next in continuous delivery pipeline.
* From technical perspective refactoring is hardly possible. Getting feedback about changes made to the system tends to be happen not in development environment also.

On the contrary, I want to know about how changes affect system in the Work-In-Progress stage.

I think these both concepts - Unit Testing and DBC - should complement each other. Unit testing should be practiced and implemented in tests. DBC should be practiced and implemented as a mental model. Something that engineer should always have in the background during his work.


[^1]: Design by Contract was developed by Bertrand Meyer in 1986 when he was working on Eiffel programming language.

