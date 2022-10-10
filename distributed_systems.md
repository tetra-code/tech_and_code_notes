# Actor model
The **actor model** is a conceptual model of concurrent computation. 

**Actor** is like a node with following properties:
- lightwight (can create millions of them)
- isolated from other actors
- can only communicate via messages iff address of other actor is known
- has its own private state
- each have own separate memory
- each have own separate mailbox to store messages
- can only change its state via messages (transactions)
- can process only one message at a time
- actors can be in the same host (same server) or different host (different server)

Messages are FIFO.

Address != identity. Two actors may hjave same identity but doesn't mean same address.

Actors are arranged hierarchically with the following roles:
- regular actor
- supervisor
- top level supervisor

![Image](images/actor_hierarchy.png)

If actor creates another actor, it becomes its supervisor. A supervisor can decide what to do if one of its child actor fails 

Pros to actor model
- async
- fault tolerant
- self-healing system
- easy to scale
- geographical distribution
- no shared state

Cons to actor model:
- actors susceptible to deadlocks
- actors mailbox overflowing

The actor model is only conceptual. Real life implementations of the actor model is:
- **Akka**
- **elixir**

## Akka
Akka is a toolkit that simplifies the construction of concurrent distributed applications on the JVM. It can support other concurrency models such as **futures** and **agents** but it emphasizes mostly on **actor** concurrency. 

It is intended for both Java and Scala. 

The key points distinguishing applications based on Akka actors are:

- Concurrency is message-based and asynchronous: typically no mutable data are shared and no synchronization primitives are used
- Akka enforces parental supervision, which means that each actor is created and supervised by its parent actor. An actor failure is treated as events to be handled by an actor's supervisor 
- The way actors interact is the same whether they are on the same host or separate hosts, communicating directly or through routing facilities, running on a few threads or many threads, etc. Such details may be altered at deployment time through a configuration mechanism, allowing a program to be scaled up (to make use of more powerful servers) and out (to make use of more servers) without modification.


Akka has a modular structure, with a core module providing actors. Other modules are available to add features such as network distribution of actors, cluster support, Command and Event Sourcing, integration with various third-party systems (e.g. Apache Camel, ZeroMQ)
