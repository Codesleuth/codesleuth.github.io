---
layout: stackedit
title: CQRS – but different
date: 2015-06-15 13:40
permalink: /notes/ndcoslo2015/CQRS-but-different.html
---

# NDC Oslo 2015
## CQRS – but different
*by Udi Dahan*

**2015-06-15 13:40** (https://vimeo.com/131199089)

#### Background
* Why do they need it?
	* Scalability
	* Simpler Code
	* Everyone's doing it (hypecurve)

* Scalability
	* DB Master/Slave
	* Partitioning
	* Sharding
		* Like partitioning but with a natural key

#### Architecture

* Don't get caught up in layers

* DDD
	* Value objects
	* Anti-corruption components
	* Sub-domains and bounded contexts
		* One to one relationship
			* Bounded context => sub-domain

* Beyond Layers
	* Service buses

* Concurrency begins to choke
  e.g. transactions on *count* then *update*
	* Connection pool dries up
	* Terrible wait for other users

* Regular CQRS may fall behind too
	* Eventually consistent - how long?

#### Approaches

* Event Driven Architecture
	* Event Sourcing
		* Non-blocking
		* Append only

* The business needs to be more flexible
	* Asking to scale will eventually require eventual consistency
	* Non-blocking and non-consistent frees contention

* Append only
	* Delta rows, +1, -1, +250 etc
	* No consistency, *Sum(Delta)*
	* Data volume becomes insane proportional to requests & commands, not inventory
	
	* Add snapshotting occasionally aggregating and truncating history

* CQRS as an approach, not cookie cutter