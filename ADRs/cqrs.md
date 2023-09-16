# ADR.8 CQRS and scalability
This ADR describes the approach to segregate the services for reading and writing data about trips and reservations,
so that they may be scaled separately.

## Status `ACCEPTED`

## Rationale
Storage of data following different pattern compared to reading:
- Storage is processing data in bulk, as parsers may provide bulk data (but don't have to)
- Storage has to be scaled according to amount of data parsers and the load will increase
not only because of the user growth, but with more agencies being connected to the platform.
- For storage, we may be able to start with several server instances, and scale with growth.
- On other other hand side, reading data is needed for all the active users,which may mean up to 2 Million users per week.

That is why services, providing data for UI display, has to be massively scalable to hundreds of nodes.

At the same time, the rare occasions, when user is modifying the data about reservations directly,
do not need to be separated into separate service, as it's assumed to be a rare operation.

## Decision
We will apply **CQRS principle** (http://www.eventstore.com/cqrs-pattern) - we will separate backend API
services to those storing data (component, called ReservationPersister), and the one mostly used for reading reservation data 
for display in UI and (rare) update operations (component called Reservation CRUD API).

This will allow separately scalable services.

## Consequences

Positive:

* Scalability of reading and writing components can be achieved separately, saving CPU and hardware costs; also it will
allow to modify them separately (e.g. adding a cache to CRUD API for optimizing the responsiveness).

Negative:

* We have to create two physical components, create a separate load balancing pools for them, and ensure realtime updates are being
propagated from persister to CRUD API via some other means, not just in-memory communication.

