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

![](img/modular_monolith/c4.png)

There are many ways to interpret this. a big componentized Java Codebase, groups of microservices. They are not quite what I’m talking about in this blog.

What is a microservice?
The answer is anything. A system, a container, a component or even a class (serverless essentially makes a single function a microservice)

## A big Java Application
- it looks great but it is very difficult when you have dozens of engineers

## A threaded monolith

6 years ago, I was working with an exGoogle Techlead Daniel on a busy calendar subscription system that synchronises over 3 million user’s calendars everyday. Daniel and his “Silicon Valley” team came up with an architecture I had never seen before at the time. Today I would call it a “Modular Monolith”. Before I can clearly explain how it was designed, I need to firstly explain some fundamental concepts.

### Green Thread
“In computer programming, green threads or virtual threads are threads that are scheduled by a runtime library or virtual machine (VM) instead of natively by the underlying operating system (OS).”

![](img/modular_monolith/green_thread.png)

Concurrency is a form of implementation leveraging the green thread concept where each "thread" is essentially an application process on an OS thread. A Scheduler is managing the execution and blocking of potentially thousands of green threads. All green threads can talk to each other or run independently.

### The modular monolith

You might start to get the idea what this has to do with what we are talking about in this blog. Imagine each component runs on an independent green thread. Each component is developed with its own interface. Communication between two components are throug "network calls" in memory. We now have a loosely coupled modular monolith container running on a single instance.

![](img/modular_monolith/threaded.png)

This is exactly what the team built and deployed. The application ended up written in Go due to its concurreny design.

The question you might have now is "can we call this application a modular monolith?". Let us go back to the definition we agreed on at the start of this blog:

- A system that has exactly one deployment unit? Yes.
- Module must be independent and interchangeable? Yes.
- Modules can be worked on independently? Yes.
- Each module packaged together into a signle process? Yes.

## A containerised monolith

Back in 2016, Docker was not as popular as it today and Kubernetes was not a event thing. How could we execute this concept differently today?

A Kubernetes pod can have many containers. Each pod can be deployed as a signle unit. This sounds surprisingly familiar. What if we build each component into an independent container, then deploy a number of components in a single pod. Something like this:

![](img/modular_monolith/containerised.png)

Now you can create a single deployment file that deploys the 3 components as a single unit. 
Components are talking to each other locally through network calls. can we call this application a modular monolith?

- A system that has exactly one deployment unit? Yes.
- Module must be independent and interchangeable? Yes.
- Modules can be worked on independently? Yes.
- Each module packaged together into a signle process? Yes.

## The tradeoff

- Operational and monitoring complexity


## The perks

- getting some benifit from both Monilith and Microservices architectures

## Notes

- Abstration should reflect the code
- The code structure should reflect the architecture intent
- A good architecture enables agility