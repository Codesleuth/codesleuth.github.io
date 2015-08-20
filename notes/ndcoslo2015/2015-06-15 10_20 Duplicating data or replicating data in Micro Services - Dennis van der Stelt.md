---
layout: stackedit
title: Duplicating data or replicating data in Micro Services
date: 2015-06-17 10:20
permalink: /notes/ndcoslo2015/Duplicating-data-or-replicating-data-in-Micro-Services.html
ndcoslo2015: true
---

# NDC Oslo 2015

## Duplicating data or replicating data in Micro Services
*by Dennis van der Stelt*

**2015-06-17 10:20** (video not posted yet)

* Agenda
	* Monolithic vs Microservices
	* Service boundaries
	* Replicating vs Duplicating data

#### Monoliths

* Large, powerful, and interactively indivisible
* Built & deployed as a single unit
* A monolith is not badly designed by default

#### Microservices

* Small, independant processes
* Highly decoupled
* Single task
* Explicit boundaries
* Share schema & contract
* Compatibility based on policy

### The Monolith

* What change are you making in a monolith? Is it tested?

* “My First Law of Distributed Object Design: Don't distribute your objects”
	*[Martin Fowler](http://martinfowler.com/bliki/FirstLaw.html), [Patterns of Enterprise Application Architecture](http://martinfowler.com/books/eaa.html)*

* Problems
	* Maintenance
	* Docs
	* Cost for new features
	* Ownership of projects

* Architecture
	* Boundaries
	* Messaging
	* Deployment
	* Monitoring

### The Microservice

* Logical service boundaries
	* Table joins are just DB coupling
	* Can have their own architectural style, not just a top level architecture

* Coupling Aspects
	* Platforms
		* e.g. REST? JSON?

	* Temporal
		* Sequential is normal (e.g. DB unavailable errors)
		* Queues over a service boundary

	* Spatial
		* Sender & receiver are unaware of each other
		* No coupling
		* Services calling each other breaks this

* Messaging
	* Supplement SOA with Event Driven Architecture (EDA)

* Duplicating Data
	* Status Changes
		* What event just took place?
	* Identifiers
		* Who was it?
	* DateTime info
		* When does it expire?

* Replicating Data
	* Memcache for performance
	* View models for optimisation
	* Different machines mean latency
	* Different sites mean network issues

#### My questions
* Taxi Arrived vs. Request Cancelled
	* Multiple consumers?
	* Race condition?
* Republishing to local data replicas? How?
	* See [Udi’s talk on Medicat Scenario](https://vimeo.com/113515335)