---
title: Common Principles
date: 2020-10-10
categories:
  - system-design
markup: mmark
math: true
tags:
    - system-design
---

## Contents
 * [Vertical scaling](#vertical-scaling)
 * [Horizontal scaling](#horizontal-scaling)
 * [Caching](#caching)
 * [Load balancing](#load-balancing)
 * [Database replication](#database-replication)
 * [Database partitioning](#database-partitioning)
 * [CAP theorem](#cap-theorem)

### Vertical scaling

**Vertical scaling** means add more new resources in the existing system to meet the expectation.
In other words that you scale by adding more power (CPU, RAM) to an existing machine.

Good example of vertical scaling is *The cloud version of MySQL*

### Horizontal scaling

**Horizontal scaling** means that you scale by adding more machines.
When added new resources to the existing system can't meet the expectation,we need to add completely new servers 
and distraction our services to these machines.

Good examples of horizontal scaling are *Cassandra, MongoDB*

### Caching

**Caching** means temporary storage location,usually store in RAM.So that they can be accessed more quickly.  

#### Cached Database Queries

    That’s still the most commonly used caching pattern. Whenever you do a query to your database, you store the result dataset in cache. A hashed version of your query is the cache key. The next time you run the query, you first check if it is already in the cache. The next time you run the query, you check at first the cache if there is already a result. This pattern has several issues. The main issue is the expiration. It is hard to delete a cached result when you cache a complex query (who has not?). When one piece of data changes (for example a table cell) you need to delete all cached queries who may include that table cell. You get the point?

### Load balancing

    In computing, **load balancing** refers to the process of distributing a set of tasks over a set of resources (computing units), with the aim of making their overall processing more efficient. Load balancing techniques can optimize the response time for each task, avoiding unevenly overloading compute nodes while other compute nodes are left idle.

[more](https://en.wikipedia.org/wiki/Load_balancing_(computing))

### Database replication

    Database replication can be used on many database management systems (DBMS), usually with a master-slave relationship between the original and the copies. The master logs the updates, which then ripple through to the slaves. Each slave outputs a message stating that it has received the update successfully, thus allowing the sending of subsequent updates.
    
[more](https://en.wikipedia.org/wiki/Replication_(computing)#DATABASE)

keywords: *master-slave relationship*,*multi-master replication*,*distributed transaction*

    Database replication becomes more complex when it scales up horizontally and vertically. Horizontal scale-up has more data replicas, while vertical scale-up has data replicas located at greater physical distances. Problems raised by horizontal scale-up can be alleviated by a multi-layer, multi-view access protocol. The early problems of vertical scale-up have largely been addressed by improving Internet reliability and performance.

### Database partitioning
      
    A partition is a division of a logical database or its constituent elements into distinct independent parts. Database partitioning is normally done for manageability, performance or availability[1] reasons, or for load balancing. It is popular in distributed database management systems, where each partition may be spread over multiple nodes, with users at the node performing local transactions on the partition. This increases performance for sites that have regular transactions involving certain views of data, whilst maintaining availability and security.
   
[more](https://en.wikipedia.org/wiki/Partition_(database))
eg: *ElasticSearch*

### CAP theorem

    Dr. Eric Brewer gave a keynote speech at the Principles of Distributed Computing conference in 2000 called 'Towards Robust Distributed Systems' [1]. In it he posed his 'CAP Theorem' - at the time unproven - which illustrated the tensions between being correct and being always available in distributed systems.
    
    Two years later, Seth Gilbert and Professor Nancy Lynch - researchers in distributed systems at MIT - formalised and proved the conjecture in their paper “Brewer's conjecture and the feasibility of consistent, available, partition-tolerant web services” [2].

  * Consistency - Every read receives the most recent write or an error
  * Availability - Every request receives a response, without guarantee that it contains the most recent version of the information
  * Partition Tolerance - The system continues to operate despite arbitrary partitioning due to network failures

#### CP - consistency and partition tolerance
    Waiting for a response from the partitioned node might result in a timeout error. CP is a good choice if your business needs require atomic reads and writes.

#### AP - availability and partition tolerance
    Responses return the most readily available version of the data available on any node, which might not be the latest. Writes might take some time to propagate when the partition is resolved.
    
    AP is a good choice if the business needs allow for eventual consistency or when the system needs to continue working despite external errors.
    
    
### Materials

 - [Paxos算法](https://zh.wikipedia.org/wiki/Paxos%E7%AE%97%E6%B3%95)
 - [拜占庭将军问题](https://zh.wikipedia.org/wiki/%E6%8B%9C%E5%8D%A0%E5%BA%AD%E5%B0%86%E5%86%9B%E9%97%AE%E9%A2%98)