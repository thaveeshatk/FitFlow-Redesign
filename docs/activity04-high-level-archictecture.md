Activity 4 – High-Level Architecture Design
Architecture Overview
The proposed FitFlow architecture builds on the technology choices from the earlier activities, with an emphasis on cross-platform reach, performance, scalability, security, real-time communication and AI-driven fitness features.
Chosen Stack
•	Frontend: Flutter
•	Backend: Node.js with NestJS
•	Database: PostgreSQL
•	Authentication: Supabase Auth
•	AI Microservice: Python with FastAPI
•	Caching: Redis
•	Real-time Communication: WebSockets / Firebase
•	External Integrations: Health APIs, payment services and notification services
Core Components
1. Flutter Frontend – delivers the mobile and web interfaces, letting users manage workouts, track nutrition, view progress and use social features.
2. NestJS Backend – serves as the main API layer, covering users, workouts, nutrition, social features, notifications and core business logic.
3. PostgreSQL Database – holds structured data such as user profiles, workout records, progress, nutrition and social information.
4. Python/FastAPI AI Microservice – runs AI/ML features such as personalised workout recommendations, fitness analysis and nutrition suggestions.
5. Redis Cache – caches frequently used data such as workout plans, sessions and popular content to lighten database load and speed up responses.
6. Real-Time Layer – WebSockets or Firebase drive live notifications, workout updates and social interactions.
Data Flow for Key Features
A. Personalised Workout Plans
11.	User submits fitness goals, level and preferences via the Flutter app.
12.	The request goes to the NestJS backend.
13.	NestJS pulls relevant user data from PostgreSQL.
14.	That data is passed to the Python/FastAPI AI service.
15.	The AI service builds a personalised workout plan.
16.	The plan is saved in PostgreSQL, with frequently used results cached in Redis.
17.	The finished plan is sent back to the Flutter app.
Flow: User → Flutter → NestJS → FastAPI AI → PostgreSQL/Redis → Flutter
B. Social Sharing
18.	User creates a workout or progress post in the Flutter app.
19.	The request reaches the NestJS Social Service.
20.	The post is saved in PostgreSQL.
21.	Live notifications go out via WebSockets/Firebase.
22.	Other users can view and interact with the shared post.
Flow: User → Flutter → NestJS → PostgreSQL → WebSockets/Firebase → Other Users
C. Nutrition Tracking
23.	User logs food or meal details through the Flutter app.
24.	Data is sent to the NestJS Nutrition Service.
25.	The nutrition data is stored in PostgreSQL.
26.	The AI service can analyse this data and generate recommendations.
27.	Results are shown back in the Flutter app.
Flow: User → Flutter → NestJS → PostgreSQL → FastAPI AI → Flutter

Security Considerations
FitFlow needs to safeguard sensitive user and health-related data throughout.
Key measures include:
•	HTTPS/TLS for data in transit
•	Encryption for stored sensitive data
•	Supabase Auth for secure authentication
•	Role-based authorisation on protected resources
•	Secure JWT/OAuth2 token handling
•	Input validation and API protection
•	Defences against common OWASP risks
•	Audit logging and monitoring
•	Secure handling of API keys and secrets
•	Privacy controls aligned with GDPR
Where HIPAA applies, meeting it depends on the entire system, its operational processes and controls — no single technology choice makes that compliance automatic.

Scalability Considerations
The architecture can grow to meet future demand by:
•	Deploying backend services in containers
•	Load balancing across multiple backend instances
•	Using Redis to ease database load
•	Applying database indexing and read replicas
•	Running AI functionality as an independent microservice
•	Using cloud infrastructure with auto-scaling
•	Serving static web content via a CDN
•	Monitoring application performance and resource usage
This lets individual pieces scale to their own workload rather than scaling the whole system unnecessarily.



Integration Considerations
FitFlow can connect with external services such as:
•	Apple Health / Google Fit for fitness and activity data
•	Payment gateways, if premium subscriptions are added
•	Firebase for notifications and real-time features
•	AI/ML services for advanced recommendations
•	Email/SMS services for user notifications
APIs should be documented and versioned so future integrations stay straightforward.

Architecture Decision Record (ADR)
ADR-001: FitFlow Technology Stack
Item	Decision
Status	Accepted
Context	FitFlow needs a scalable, secure, cross-platform architecture with AI/ML and real-time capability.
Decision	Flutter for the frontend, NestJS for the backend, PostgreSQL as the database, Supabase Auth for authentication, Python/FastAPI for AI/ML and Redis for caching.
Rationale	This mix delivers solid performance, code reuse, scalability, security, AI/ML support and maintainability for a mid-sized team.
Consequences	More services need to be maintained, but the setup stays flexible and lets AI and other components scale independently.


Summary of the Architecture
The proposed architecture gives the FitFlow redesign a solid base. Flutter delivers a consistent Android, iOS and web experience; NestJS and PostgreSQL handle core functionality and data; FastAPI covers specialised AI/ML work; and Redis with WebSockets/Firebase improve performance and real-time communication.
Overall, the design aims to be secure, scalable, maintainable and ready to support FitFlow's future growth.
