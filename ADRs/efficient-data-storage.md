# ADR.7 Efficient data storage

## Status `APPROVED`

## Description

Modern databases follow one of the two data structure patterns - relational (SQL) or non-relational (NoSQL). Below is a table that compares the two patterns:

| Characteristic | Relational | Non-Relational |
| --- | --- | --- |
| Structure | Normalized | Denormalized |
| Organization | Tables with columns and rows | Document-based, key-value or graph |
| Schema | Predefined schema | Dynamic schema for unstructured data |
| Scalability | Vertically scalable | Horizontally scalable |

## Rationale

We have the following requirements to the data storage of Road Warrior:

- High performance: must be able to process and store a million reservations per day
- Efficient updates: besides the initial creation, those reservations can have a series of subsequent updates (i.e. append-only structures are not an option).
- Flexible data structure: on the one hand, the reservations will have a variant schema based on their nature (airline, hotels, car rentals, train tickets); and on the other hand each data source can have its own specific fields.

## Decision

We believe that document-based NoSQL database is the best fit for data storage. Moreover, we select **MongoDB** in particular due to its maturity, its efficiency for web applications, its excellent integration with most popular web/mobile programming languages, as well as its ability for high performance and high availability.

## Consequences

### Positive

- flexible data schema
- high performance
- faster development

### Negative

- difficulty in handling complex transactions