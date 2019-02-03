---
title: "Right Tools for the Right Moment"
date: 2019-02-03T18:28:28+02:00
draft: false
---

Have you ever realized that the current state of architecture does not meet the current needs? One of the projects I’ve been working on had PostgreSQL and Neo4j databases with data tightly related between them.

There were several reasons of migrating data from graph to relational database.

From engineering side there was little variation in the relationships. Instead there were simple regular structures. Maximum what we had is a recursive structures which can be solved by [Common Table Expressions](https://www.postgresql.org/docs/9.1/queries-with.html) in PostgreSQL. Recursive lookup is not a problem for this case because depth of the path is small.

On the other hand having both relational and graph styles need mental context switching which increases a Cycle time.

Migration was not easy because it is a production system with real customers using it. Big challenge is absence of any tests and having limited amount of time.

Here are the list of techniques we used:

* Making a plan in which order to migrate parts of the system
* Using [feature flag](https://martinfowler.com/articles/feature-toggles.html)
* Creating tests that compared data between results of some core functions with enabled feature flag vs disabled
* Manual testing
* Having one environment with enabled feature flag and another with disabled feature flag to compare behaviour of the system
* Daily communication between engineers

Having all that we were able to successfully migrate data. As a result development of new features became more easier. Initially performance was not a noticeable issue. After migration page response time even decreased. Instead of requesting data from two databases now it is just one.

What lesson should be drawn from this story? Choosing wrong technology can led to significant increase of Cycle time. That Neo4j database hadn't been solving any specific problem but added complexity. Having just PostgreSQL is enough for this system at the time.

Choose right tools for the right moment.
