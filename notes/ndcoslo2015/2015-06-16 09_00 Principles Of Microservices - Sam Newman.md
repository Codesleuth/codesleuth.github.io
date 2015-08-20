---
layout: stackedit
title: Principles Of Microservices
date: 2015-06-18 09:00
permalink: /notes/ndcoslo2015/Principles-Of-Microservices.html
ndcoslo2015: true
---

# NDC Oslo 2015

## Principles Of Microservices
*by {{ page.speaker }}Sam Newman*

**{{ page.date | date: '%A, %B %Y %H:%M' }}**

{% include vimeo.html id="131632250" %}

> _"Small *Autonomous* services that **work together**, modelled around a **business domain**"_ (deployed independently)
  
* More choices than a monolith

* Heroku - _http://12factor.net_
  1. Codebase - One codebase tracked in revision control, many deploys
  2. Dependencies - Explicitly declare and isolate dependencies
  3. Config - Store config in the environment
  4. Backing Services - Treat backing services as attached resources
  5. Build, release, run - Strictly separate build and run stages
  6. Processes - Execute the app as one or more stateless processes
  7. Port binding - Export services via port binding
  8. Concurrency - Scale out via the process model
  9. Disposability - Maximize robustness with fast startup and graceful shutdown
  10. Dev/prod parity - Keep development, staging, and production as similar as possible
  11. Logs - Treat logs as event streams
  12. Admin processes - Run admin/management tasks as one-off processes
  
# Principles

1. Modelled around business domain
   * Achieve stability of API
   * Easy to be reused
2. Culture of automation
   * Manage the emergent complexity
3. Hide implementation details
   * Allow services to evolve independently
4. Decentralise all the things
   * Also in architectural decision making
5. Deploy independently
6. Consumer first
   * Invert our thinking
7. Isolate failure
   * Make sure your system is resilient
8. Highly observable
   * Old monitoring patterns won't stack up in a distributed systems environment


## 1. Business domain
* Business domain boundaries are more stable

## 2. Automation
* Infrastructure automation
  * Can I provision machines on demand?
* Automating testing
* Continuous Delivery
  * Get software out quickly and know it's production ready

## 3. Hide implementation details
* Database coupling between services makes change hard
* Integrate with API calls or events
* _Hide your database!_

## 4. Decentralisation of power
* What is autonomy?
  * Giving people as much **freedom** as possible to do the job at hand
  * Self service - provision machines and test environments?
* Governance
  * Push decision making into teams
* Architecture
  * Dumb pipes, smart endpoints
  * Use MoM but keep it dumb

## 5. Deploy independently
* Deploy only the service
  * Having to change more than one service to deploy is a problem
  * "Lock-step released" are bad
* Eventually, you should adopt a 1:1 Host/Container to Service ratio
* Multiple services per host are hard to verify
* Consumer-driven contracts
  * Meet expectations with tests to verify contracts
  * Run upstream expectation tests during the build of downstream services
  * End-to-end integration tests can be costly and brittle
  * Upgrade APIs with co-existing endpoints used for communication
    * Give consumers time to migrate over
    * Similar to the expand/contract pattern
    * Put the power in the hands of the consumer
    * Understand the cost of change of APIs
    * APIs within a single team are much easier to change

## 6. Consumer first
* Documentation
  * Tooling, like Swagger or HAL
* Service discovery
  * [Zookeeper](https://zookeeper.apache.org/)
  * [etcd](https://github.com/coreos/etcd)
  * [Consul](https://www.consul.io/) - implements DNS
  * Standard DNS (TXT)
* Martin Fowler: HumaneRegistry
  * A simple wiki page to show information from our services
  * Pull in information from other sources

## 7. Isolate Failure
* Distributed systems are not more resilient or reliable
  * Systems are likely to become more unreliable, than reliable
  * Resiliency does not come for free

* Strangler Pattern
  * Redirect requests from old code to to new code
  * Allows incrementally improving services
  * Beware of downstream applications failing slowly, tying up resources
  * Slow components add latency - timeouts too high?
  * **Bulkheading** downstream connections
  * Circuit breaker design pattern
    * Protect you from continuous failure
    * Fast failure is better
    * Automatic and manual?
      * Manual switch to help deploys

## 8. Highly observable
* Not just humans looking at graphs
* Collect information and aggregate
  * Log aggregation - get them off the box!
  * Stats - centralise them and open them up
    * Graphite
    * [Promethius](http://prometheus.io/)
  * Correlations