# Research - Demystifying Event Sourcing

## Preface

I recently worked with ThoughtWorks at PEXA and had a number of great conversation on Event Sourcing and if it is a good fit for our new GreenField project. After reading many articles and watching many videos about event sourcing, I feel it is worthwhile to write my own. Mainly because this is a very simple concept many people seem to overcomplicate.

Let's start by looking at the definitions.

## Definition

Martin Fowler and Greg Young have both written great definitions of Event Sourcing:

Martin Fowler, 2005:

    "Event Sourcing ensures that all changes to application state are stored as a sequence of events."

Greg Young, 2014:

    "Event Sourcing says all state is transient and you only store facts."

Another good definition i came cross is from this [Microsoft's article]((https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)):

    "Instead of storing just the current state of the data in a domain, use an append-only store to record the full series of actions taken on that data."

It is worth to note that the word state appeared in all 3 definitions. This concludes that Event Sourcing is about state which has everything to do with events.

## Domain Events vs Event Sourcing Events

When talking about events, people ofte associate it with Domain Events from Domain Driven Design(DDD). Fowler wrote an article on Domain Events way back in 2005. In short, Domain Events are described as something that happens in the domain and is important to domain experts. Such events typically occur regardless of whether or to what extent the domain is implemented in a software system.
Examples of Domain Events can be:

- User Registered
- Order Placed
- Payment deadline expired

Domain events are typically used for communication between domains, either used as a notification that something has happened, or transfering state from one domain to another by caryying necessary information as part of the event payload.

Events for event sourcing are usually within a specific domain and create a state of domain objects as event. This is also call an aggregate. For example, UserRegistration aggregate could have the following events:
- emailAddressEntered (email@example.com)
- verificationCodeGenerated (123456)
- EmailAddressValidated
- UserDetailsSubmitted (John, Doe, male, +12345678)

By playing the series of events, we have the current state of the user.

In contrast, Event Sourcing Events can be seen as detailed events. These events live within a specific domain where Domain Events are high level events that move across domains.
(https://www.innoq.com/en/blog/domain-events-versus-event-sourcing/)

## State as Event vs State from Event

The explaination above described Event Sourcing as state as Event. However, it is not necessarily the only intepretation of Event Sourcing.

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