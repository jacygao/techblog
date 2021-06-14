# Research - Demystifying Event Sourcing

# Preface

There are a lot of opinions about event sourcing. However, this article focuses on fact through a form of research to explore what event sourcing is, where it came from and what can we do with it, as well as make some logical assumpltions based on the outcome of these learnings.

# Definition

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

One common misconceptions is that Event Sourcing is associated with an Event Streaming or Event Driven Architecture. There are certainly many things you can achieve with Event Sourcing. Nevertheless, conceptually, Event Sourcing is no more than a pattern to store your data in a form of a serials of events as opposed to 

# Inspiration




# everthing else
SQL Migration script

"acounting only appends"

"banking balance is made of a number of transactions"

"accountants dont work in pencils, they work in pen"

"used for smoke test when pushing new features"

"prevent super user attack"

"lawyer adding addendum"

"doctors append thing to file"


# issues

Versioning

People