# Architecture and Engineering Guardrails

## API First

API should be the first user interface and interaction for your application. API comes first, then the implementation.

## Loosely coupled architecture

Strive to build lean microservices with a single responsibility, without many dependencies, allowing teams to work independent, deploy independent, fail and scale independent.

## Design for failure

The design of all credible, fault-tolerant architectures is based on one extremely important principle:
"Anything that can go wrong, will go wrong." - Murphy’s Law.
Consider failures an integral part of any system.

## Isolate Failure

Any single component of the system fails should not cause any impact to overall platform. Avoid Single Point of Failure.

## Platform Agnostic

Products and services should be designed in such a way that they are not tied to a specific platform or system.

## Adopt Containerization

Microservices are built and deployed as containers to achieve portability across difference cloud platforms. They are written once, run anywhere.

## Deployment independence

A single microservice can be deployed to production without having to deploy any other services.

## Encryption Everywhere

All traffic within and outside of the platform should be encrypted. Data to be also encrypted at rest and In-transit.

## Zero Trust Security Model

All users including those inside the organization’s enterprise network are required to be authenticated, authorized, and continuously validating security configuration and posture, before being granted or keeping access to applications and data.

## Embrace Automation

Embrace automation from Provisioning, Compute, Storage, Network Services to Testing, Continuous Integration and Continuous Delivery of the applications and services.

## You Build It You Run It

Delivery team is responsible for its Run activities, including deployments and production support.
