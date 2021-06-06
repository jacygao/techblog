# Modular Monolith

## Definition of a Modular Monolith

### Signle process Monolith
- all code packaged into a singal process
- all data stored in a single database

(Kamil Grzybek - Modular Monolith: A Primer)
- a system that has exactly one deployment unit

### Cons of monolith architecture
- not reusable
- harder to scale
- black box
- all in one place

(https://articles.microservices.com/monolithic-vs-microservices-architecture-5c4848858f59)

- This simple approach has a limitation in size and complexity.

- Application is too large and complex to fully understand and made changes fast and correctly.

- The size of the application can slow down the start-up time.

- You must redeploy the entire application on each update.

- Impact of a change is usually not very well understood which leads to do extensive manual testing.

- Continuous deployment is difficult.

- Monolithic applications can also be difficult to scale when different modules have conflicting resource requirements.

- Another problem with monolithic applications is reliability. Bug in any module (e.g. memory leak) can potentially bring down the entire process. Moreover, since all instances of the application are identical, that bug will impact the availability of the entire application.

- Monolithic applications has a barrier to adopting new technologies. Since changes in frameworks or languages will affect an entire application it is extremely expensive in both time and cost.

### Modularity
(Monolith Decomposition Patterns • Sam Newman • GOTO 2019)
- Code is broken into modules
- Modules can be worked on independently
- Each module packaged together into a signle process
- Decomposited database

(Kamil Grzybek - Modular Monolith: A Primer)
- Module must be independent and interchangeable (Loose Coupling, Strong Cohesion)

num of dependencies, strength of coupling, stability of the modules on which the module depends on

- Module must have everything necessary to provide desired functionality

- Module must have defined interface

- Domain boundries

## The C4 Model

Simon Brown’s C4 diagram divides a software into a number of systems, a system consists of a number of components

//TODO: diagram here

There are many ways to interpret this. a big componentized Java Codebase, groups of microservices. They are not quite what I’m talking about in this blog.

## A "typical" modular monolith
- it looks great but it is very difficult when you have dozens of engineers

## A threaded monolith

6 years ago, I was working with an exGoogle Techlead Daniel on a busy calendar subscription system that synchronises over 3 million user’s calendars everyday. Daniel and his “Silicon Valley” team came up with an architecture I had never seen before at the time. I would call it a “Modular Monolith” if I knew the term at the time. Before I can clearly explain how it was designed, I need to firstly explain some fundamental concepts - Green Threads.

“In computer programming, green threads or virtual threads are threads that are scheduled by a runtime library or virtual machine (VM) instead of natively by the underlying operating system (OS).”

//TODO: diagram here

## A containerised monolith


## Notes

- Abstration should reflect the code
- The code structure should reflect the architecture intent
- A good architecture enables agility



polyglot

operational and monitoring complexity