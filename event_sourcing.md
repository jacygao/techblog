# Research - Demystifying Event Sourcing

## Preface

There are a lot of articles about event sourcing. Despite of all the opinions on the intenet, this article focuses on fact through a form of research to explore what event sourcing is, where it came from and what can we do with it. Armed with these fact, we should be able to make some logical assumpltions.

## Definition

Martin Fowler and Greg Young have both written great definitions of Event Sourcing:

Martin Fowler, 2005:

    "Event Sourcing ensures that all changes to application state are stored as a sequence of events."

Greg Young, 2014:

    "Event Sourcing says all state is transient and you only store facts."

In one of [Microsoft's articles]((https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)) about Event Sourcing, you can also find the following definition:

    "Instead of storing just the current state of the data in a domain, use an append-only store to record the full series of actions taken on that data."

What is worth to note here is that Event Sourcing is about data and state. An event is something already happened in the past which means it becomes immutable. A series of events creates a state of an entity or an application which has been described as "Events as State". This should be differentiated from "State from Events".

## State as Event vs State from Event

The distinction is important. “State from Events” assumes an existing event stream, regardless of how it was produced, and projects state from it. No new events are added to the stream. “Events as State” is about events as the single source of truth. In other words, new events are added to the stream, but they’re constrained by business rules, and these rules depend on previous events as their input (as opposed to state as the input).


One common misconceptions is that Event Sourcing is associated with an Event Streaming or Event Driven Architecture. There are certainly many things you can achieve with Event Sourcing. Nevertheless, conceptually, Event Sourcing is no more than a pattern to store your data in a form of a serials of events. This can be an alternative model to the common CRUD object state management.

### Command Sourcing vs Event Sourcing

what is command sourcing and how it is different from event sourcing.

    "With a command you tell a system to do X. Events, however, just communicate that something happened - with an event you let a system know that Y has happened." - Fowler 2006

With Event Sourcing, events in an event store are being replayed, you essentially recreating the view of the records as opposed to replaying the command in which in that case, it is Command Sourcing. 

## Inspiration

### Event Sourcing in real life

Event Sourcing in real life can be traced all the way back to the Mesopotamia Sumer (Young 2014). The prime example of Event Sourcing is a double-entry accounting ledger where the ledger entrys are a log of all of the events that change the value of an Account, so that an Account is itself an example of Event Sourcin (Fowler 2004). Other examples of event sourcing mentioned by Greg Young include how lawyers add addendum to the contracts and how doctors appending records to files, etc (Young 2014)

As it can be seen that Event Sourcing is inspired by real life examples. There isn't any official publications when and who invented this concept at the first place. it is reasonable to assume Luca Pacioli, a friend of Leonardo da Vinci, who published Summa de Arithmetica(https://en.wikipedia.org/wiki/Summa_de_arithmetica) in which described the concept of double-entry bookkeeping in 1494 was one the first people who invented the idea of event sourcing.

### Event Sourcing and Functional Programming
Bob Martin also wrote about the Event Sourcing in the Functional Programming Chaper of his book Clean Architecture where he discribed how event sourcing enforces immutable data which eliminates the challenges from concurrency and race conditions.

## Misconceptions

Now we understand what Event Sourcing really is about, let's take a look at some common misconceptions about Event Sourcing.

### Git is built with Event Sourcing (Fowler 2004)

Martin Fowler in his Event Sourcing article mentioned that a version control systems like git is an implementation of Event Sourcing. This statement is not technically correct. In fact, Git uses snapshotting technique on `git commit` and the `git diff` simply compare 2 snapshots(git trees) and calculate the difference on demand ((https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Basic-Snapshotting)). Although the technique of snapshotting is commonly used with Event Sourcing to reduce the number of in memory calculation of a large amount of event history (Fowler 2005), Git as an example of Event Sourcing is technically incorrect.

### Event Sourcing needs an event bus

Although this Confluet article demonstrates a great solution design where Kafka can be leveraged as a persistent event store, event bus is not a default solution for implementing Event Sourcing. Greg Young emphasized that a database is also a event queue. What Event Sourcing really needs is a persistent event store, regardless its form.

### Event Sourcing is not enterprisey

Despite the fact that enterprisey sounds like a inresponsible 

### Event Sourcing needs to be used with CQRS

Event Sourcing and CQRS are 2 very different concepts althought CQRS is often applied to an Event Sourced system to provide the query capability. Either technique can be applied individually.

### Event Sourcing is hard

Multiple people have indicated that the total effort it requires to implement an Event Sourcing solution and a typical CRUD solution reuqires roughly the same amount of work. Latter may get up and running quicker, but Event Sourcing requires less work in a long run.

## The benifits for Event Sourcing


### The general benifits


### The overlooked benifits

"avoid having to use a 2pc transaction between the data model and the message queue" - Young 

"Testing with the events that actually happens" - Young

"visualise concurrency violation" - Young

"performance benifits due to only one disk write for both your storage and your durable queue" - Young

## The biggest challenge of Event Sourcing



## Tradeoff



## everthing else
Command Sourcing vs Event Sourcing

- State from event
- State as event

SQL Migration script

"accountants dont work in pencils, they work in pen"

"used for smoke test when pushing new features"

"prevent super user attack"

"lawyer adding addendum"

"doctors append thing to file"

"Event Sourcing is the only way to guarantee you event logs in distributed architecture"

"database commit log is a usecase of event sourcing"

## issues

Versioning

People