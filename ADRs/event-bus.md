# ADR.6 Event bus
This ADR describes the approach to events processing (like new reservations, flights delays, etc) and selection of 
event bus to distribute them. The event bus has to be scalable, work across regions in the clouds, and persistent.

## Status `APPROVED`

## Rationale
As we use event-driven architecture we need some way to distribute such events across the system. Standard way to 
address it is to use some message queue. This message queue should be persistent and scalable to meet our requirements
for availability, disaster recovery (5 minutes of unplanned downtime per month) and elasticity (to handle peak load). 
While there are number of available message queues, we will use Kafka. As it suits all our needs and in addition
has great advantage as it is the most popular and widely used one. And we should not use any exotic components for
our startup project, where we should be able to find new developers pretty quick.

## Decision
Use **Kafka** as persistent and scalable event bus to stream reservation events.

## Consequences

Positive:

* We can rely on event bus and be sure events are never lost, even in case of some outages.
* Kafka is commonly used across industry, and it should be easy to find new developer with a knowledge of it 

Negative:

* Increased consumption of disk space to store all events with desired level of redundancy.
