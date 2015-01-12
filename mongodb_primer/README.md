# MongoDB Primer

This chapter will focus primarily on giving readers a quick [introduction](http://www.mongodb.org/about/introduction/) to the [MongoDB database](http://www.mongodb.org/) concepts, along with some examples of query formulation and command-line usage.

1. For more detailed understanding of this topic, refer to the [MongoDB Manual](http://docs.mongodb.org/manual/core/introduction/).

2. For a quick review of MongoDB commands and API, see [MongoDB Reference](http://docs.mongodb.org/manual/reference/)

MongoDB is currently the default database used by the Meteor platform and as such, is intrisic to understanding (and influencing) both client and server side behaviors.

*The current MongoDB version (Jan 2014) is 2.6*

## What is MongoDB?

Relational databases stored *structured* data in tables with rows/columns. A document database stores *unstructured* data as objects (documents) grouped into *collections*.

MongoDB is a JSON-like data store consisting.

* A MongoDB deployment can have multiple databases hosted - each database has a unique name.

* A MongoDB database can host multiple *collections* - each with a unique name in that database -- where a collection contains documents of the same 'type'.

* A MongoDB document is a simple object containing attribute *name-value* pairs, where each document has a mandatory and unique *_id* attribute as a default  identifier. Attributes can store strings, integers, arrays and even * other objects* as values. This allows a document to *embed* another document -- where 'embedding' refers to the fact that the enclosed document is directly indexable by MongoDB.

* A MongoDB deployment can be [replicated](http://docs.mongodb.org/manual/core/replication/?_ga=1.198915695.1331282921.1420977016) for reliability, availability and scalability.Two deployment architecture options exist: *replica sets* and *sharded clusters*. Replica sets are about vertical scaling and fault tolerance; sharded clusters are about horizontal scaling and load balancing.

* A MongoDB [*replica set*](http://docs.mongodb.org/manual/core/replica-set-architectures/?_ga=1.236710281.940107857.1420977034) provides high-performance protection from server failures with *automated failover* mechanisms. Replica sets are all about **redundancy** and **fault tolerance**, not load balancing.

* A MongoDB [*sharded cluster*](http://docs.mongodb.org/manual/core/sharding-introduction/) provides scalable operation and high availability by *partitioning the data set across machines*. Sharding is all about **load balancing**. Think of a shard as a mini-database, with the shard *cluster* effectively constituting the single 'logical' database.

A word on document-oriented databases.

* Documents map neatly onto programming data types (i.e., objects from DB map cleanly onto data objects in code)

* Dynamic schema (or *schemaless*) support make polymorphism easier. (Caution: there are tradeoffs in performance, so choose your data model wisely)

* Documents can contain embedded documents or arrays, which can be indexed directly - reduces the need for joins when making queries.

