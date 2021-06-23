# Research - Demystifying Event Sourcing

## Preface

There are a lot of articles about event sourcing. Despite of all the opinions on the intenet, this article focuses on fact through a form of research to explore what event sourcing is, where it came from and what can we do with it. Armed with these fact, we should be able to make some logical assumpltions.

## Definition

Martin fowler first mentioned the concept of Event Sourcing in his article back in December 2005 where he explained event sourcing as 

    "Event Sourcing ensures that all changes to application state are stored as a sequence of events." - Martin Fowler 2005

One of the earliest explanations of Event Sourcing from Greg Young, the creator of CQRS, talked about his event sourced system at QCon SF 2007 

    "make objects responsible for tracking our in-state changes" - Greg Young 2007
    
In the following years, Greg Young gave numerous talks about Event Sourcing and CQRS. in 2014, Greg Young talked about Event Sourcing at the GOTO conference with the definition 

    "Event Sourcing says all state is transient and you only store facts." Greg Young 2014

While Event Sourcing became more popular in the software development in the 2010s, we started to see more and more blog posts writing about event sourcing, even in those big technology firms, including 

    "Instead of storing just the current state of the data in a domain, use an append-only store to record the full series of actions taken on that data." - Microsoft Docs (https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)

AxonIQ is arguablly the most established framework for Event Sourcing and CQRS, you can also find an explaination of Event Sourcing on its website:

    "Event Sourcing is a pattern for data storage, where instead of storing the current state of any entity, all past changes to that state are stored." - AxonIQ (https://axoniq.io/resources/event-sourcing)

One common misconceptions is that Event Sourcing is associated with an Event Streaming or Event Driven Architecture. There are certainly many things you can achieve with Event Sourcing. Nevertheless, conceptually, Event Sourcing is no more than a pattern to store your data in a form of a serials of events. This can be an alternative model to the common CRUD object state management.

## Inspiration

Event Sourcing in practice can be traced all the way back to the Mesopotamia Sumer (Young 2014). The most used comparason is a double-entry accounting ledger where the ledger entrys are a log of all of the events that change the value of an Account, so that an Account is itself an example of Event Sourcing. (Fowler 2004)



Other examples of event sourcing including lawyer adding addendum to the contracts, doctors appending pages to files, etc (Young 2014)


## misconceptions

### Git is built with sourcing (Fowler 2004)
Git leverages snapshotting technique rather than event sourcing.

### Event Sourcing needs an event bus
it needs a persistent event store.

### Event Sourcing is not enterprisey
banks

### Event Sourcing needs to be used with CQRS
these are 2 separate concepts

### Event Sourcing is hard
total effort roughly the same

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
SQL Migration script

"acounting only appends"

"banking balance is made of a number of transactions"

"accountants dont work in pencils, they work in pen"

"used for smoke test when pushing new features"

"prevent super user attack"

"lawyer adding addendum"

"doctors append thing to file"


## issues

Versioning

People