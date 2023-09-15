# The Road Warrior

Submission repo of DevexSolar team for the [O'Reilly Architectural Katas 2023](https://learning.oreilly.com/live-events/architectural-katas/0636920097101/) challenge.

![](road-warrior-logo.png "The Road Warrior logo")

## Problem

### Requirements

A new startup wants to build the next generation online trip management dashboard to allow travelers to see all of their existing reservations organized by trips. The users should be able to use the application either through Web or through their mobile devices.

The platform will collect reservations data by parsing users' emails or by interfacing with external systems. Users will be able to manually add, modify or remove reservations. They will see a dashboard with their upcoming trips, will post trip details to social media sites or will share directly with targeted people. 

The startup expects 15M registered users in the platform, having 2M of them be active active on a weekly basis. The startup also has a strict technical requirements for unplanned downtime (<5 mins per month), integration time (5 minutes), and response time (0.8s for Web and 1.4s for mobile).

### Assumptions

Based on the limited available requirements, we had to make a number of assumptions about the product scope:

- The startup has a limited budget and time to produce a MVP.
- We must design an architecture for a greenfield product.
- The startup is not affiliated with any given travel agency. Therefore, there will be multiple sources of reservations data and new sources can be plugged-in at any time in the future.
- Reservations data can be retrieved in 3 ways - email parsing, APIs of travel companies (airlines, hotels, car rentals) and APIs of global distribution systems (such as SABRE and APOLLO).
- Retrieved data will be "read-only" and the platform will not initiate any updates on the reservations.

## Approach

We followed an architecture design approach with the steps below:

1) Acknowledge requirements
2) Define required assumptions to clarify the scope
3) Identify product capabilities and high-level components using the Actor/Action approach
4) Analyze architecture characteristics
5) Define the most appropriate architecture style
6) Restructure the components
7) Prepare an overall component diagram
8) Prepare additional (TODO - type) supporting diagrams
9) Prepare a deployment diagram
10) Document as ADRs the decisions we made throughout the entire process

We had 5 days to design the architecture, so we conducted a multiple brainstorming sessions, as well as daily sync-up meetings.

The deliverables of our architecture design are presented in the next section.

## Solution

### Capabilities

TODO - Actor/Action diagram(s)

### Architecture Characteristics

TODO - List and justify top priority characteristics

### Architecture Style

TODO - Describe and justify the selected architecture style

### Components
The diagram below gives a high-level overview of how the logical components interact with each other as well as with 
external service providers.

![](diagrams/high-level-architecture.png "High level architecture diagram")


### Deployment

TODO - Deployment diagram here

## Architecture Decision Records

* TODO - ADR.1 Architecture Characteristics 
* ADR.2 [E-mail Processing](./ADRs/email-processing.md)
* TODO - ADR for local caching & distributed cache
* TODO - ADR for blue-green deployment

## References

TODO - List of references
