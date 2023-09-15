# ADR.3 Approach to responsiveness requirements
This ADR describes how we addresses the responsiveness requiremets (application start time and the time to react to 
new events on reservations).

## Status `APPROVED`

## Rationale
We must meet 2 requirements in terms of responsiveness:
- first screen with some content in 800 ms for web app, 1400 ms for mobile app
- travel updates must be presented in the app within 5 minutes of generation by the source

### Application content load time
To address requirements for application content load time we can use caching, both on server side and on client side.
On server side caching (keeping in memory) everything will require too much resources taking into account total amount 
of users. So we will cache just most actual data, which is travel details related to nearest or ongoing trip. We will 
keep this data for each user in some in memory data grid.
On client side we will store all user trips in mobile application memory and refresh them periodically. For web app
we will use localStorage or indexedDB. This also allows to use offline mode for both Mobile and Web apps when there's 
no internet (e.g. on the airplane).

### Time to get travel updates processed
We will use batch loading of updates from GDS/agencies APIs to keep 5 minutes processing time even for spikes in the 
number of new events.

## Decision
- Use caching (server side and client side)
- Batch reading and processing events from agencies APIs 

## Consequences

Positive:

* Responsiveness requirements are met without too much impact on the hardware resources

Negative:

* More complex logic to keep cache up to date in comparison to simple DB data retrieval each time it is required
