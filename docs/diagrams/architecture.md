## Product Choice
Name: Yandex Go

Website: go.yandex

Description: Ride-hailing and food delivery service from Yandex.


## Main components
https://../../../docs/diagrams/out/yandex-go/component-diagram/Component%2520Diagram.svg

Diagram code

Selected components:

API Gateway - Entry point for all client requests

Dispatch Service - Matches riders with drivers

Pricing Service - Calculates ride prices

Maps & Routing Service - Provides navigation and routes

Payment Service - Handles payments

## Data flow
https://../../../docs/diagrams/out/yandex-go/sequence-diagram/Sequence%2520Diagram.svg

Diagram code

Group: "3. Booking & Async Dispatch"

When user books a ride:

App → Gateway → Dispatch Service: Order request

Dispatch Service → User Service: Check payment method

Dispatch Service → Database: Save order

Dispatch Service → Cache: Find nearby drivers

Dispatch Service → Kafka: Send "RideAssigned" event


## Deployment
https://../../../docs/diagrams/out/yandex-go/deployment-diagram/Deployment%2520Diagram.svg

Diagram code

Deployment:

Apps connect via Load Balancer

Services run in Kubernetes

Data stored in YDB and ClickHouse

Redis for caching

Kafka for messaging


## Assumptions
Session validation uses JWT tokens

Driver matching considers proximity and ratings

Redis stores driver locations for fast search

Notifications are sent via Kafka events


## Open questions
How does it handle Maps API failures?

How are driver locations updated in real-time?

How does A/B testing work?