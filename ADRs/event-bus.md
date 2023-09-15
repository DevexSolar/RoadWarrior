# ADR Event bus
This ADR describes the approach to events processing (like new reservations, flights delays, etc) and distrubution 
of them via event bus.

## Status `PROPOSED`

## Rationale


## Decision
Use persistent and scalable event bus like Kafka to stream reservation events.

## Consequences

Positive:

* We can rely on event bus and be sure events are never lost, even in case of some outages.

Negative:

* Increased consumption of disk space to store all events with desired level of redundancy.
