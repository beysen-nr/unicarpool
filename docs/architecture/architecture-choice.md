 Architecture Choice and Alternatives

1. Selected Architecture

The University Carpooling System will use a **layered modular monolith**. The backend will be deployed as one application and divided into modules: Identity, Trips, Reservations, Notifications, and Moderation. Each module will separate API controllers, application services, domain logic, and data access.

This approach fits the project because the team has limited development time and the system requires consistent reservation management. A single PostgreSQL database allows seat reservations to be handled through database transactions, reducing the risk of double booking.

2. Quality Attributes

Security

The backend will authenticate users and check authorization before providing protected information. Centralizing these checks makes access-control rules easier to review and maintain.

Usability and Performance

Trip searches will use indexed database fields, including start point, destination, and date. Avoiding unnecessary communication between backend services helps keep search response times low.

3. Alternative Considered

The team considered a microservices architecture, where Trips, Reservations, and Identity would run as separate services.

Microservices can support independent deployment and scaling, but they also introduce network communication, deployment complexity, and additional consistency challenges during reservations.

4. Final Decision

A layered modular monolith was selected because it provides a simpler initial implementation while maintaining clear module boundaries. If the system grows, individual modules can be extracted into separate services when there is a demonstrated need.
