# work-experience
Work Experience

You are acting as a Principal Software Architect, Staff Backend Engineer, Distributed Systems Engineer, Payments Architect, Production/SRE Engineer, and technical interviewer.
I am preparing a comprehensive technical understanding of the payment platform/project documented in our Confluence.
Your task is NOT to simply summarize the first few Confluence pages you find.
I want you to perform a DEEP ARCHITECTURAL INVESTIGATION across all Confluence documentation available to you and reconstruct the CURRENT EXISTING SYSTEM as completely as possible.
The final output can be extremely long. Completeness is more important than brevity.
Build a detailed technical knowledge base explaining:
What the entire platform does.
Why it exists.
Who/what uses it.
The complete end-to-end architecture.
Every important service/component and its responsibility.
How services communicate.
How requests/events/data travel through the platform.
How payment transactions move through the system.
How data is persisted.
How failures, retries, replay, recovery and reconciliation work.
How the system achieves scalability, reliability, consistency, observability, security and performance.
How it is deployed and operated.
Historical architectural decisions and migrations where documented.
Known limitations, bottlenecks, incidents, failure modes and improvements.
The engineering reasoning behind the architecture.
Do not restrict the investigation only to components I personally worked on.
I want to understand the ENTIRE PLATFORM well enough that I could explain its architecture confidently in a senior software engineering / system design interview.
Do not stop at the first search result.
Start from the most relevant high-level pages and recursively investigate:
linked Confluence pages
child pages
parent pages
architecture documents
HLDs
LLDs
design proposals
RFCs
ADRs
sequence diagrams
flow diagrams
API documentation
service documentation
onboarding documentation
database documentation
event/message documentation
operational runbooks
production support documentation
incident/postmortem documents
release documentation
migration documents
performance documents
capacity/scalability documents
security documentation
resilience documentation
deployment documentation
CI/CD documentation
Kubernetes documentation
monitoring documentation
troubleshooting documentation
integration documentation
reconciliation documentation
batch/job documentation
replay/recovery documentation
payment lifecycle documentation
Whenever a page references another component, service, flow, event, database, API, queue, topic or design document, investigate that reference too.
Continue traversing until you can reconstruct the architecture rather than merely summarize individual documents.
Search using alternative terminology where useful.
For example, search concepts such as:
payment
transaction
payment processing
payment orchestration
authorization
capture
clearing
settlement
reconciliation
payment status
exception
replay
retry
recovery
persistence
database
event
Kafka
queue
topic
scheduler
job
executor
batch
API
gateway
integration
downstream
upstream
Kubernetes
deployment
performance
latency
throughput
resilience
failover
HA
DR
monitoring
alerting
incident
timeout
duplicate
idempotency
consistency
Also search using actual service names discovered during investigation.
VERY IMPORTANT:
Never invent architecture.
For every conclusion classify it as one of:
[DOCUMENTED FACT]
[STRONG INFERENCE]
[UNCERTAIN / NEEDS VERIFICATION]
[OUTDATED / HISTORICAL]
If documents conflict, do not silently select one version.
Instead explain:
Document A says X.
Document B says Y.
Their update dates are X and Y.
The likely current architecture appears to be Z.
Confidence: High / Medium / Low.
Prefer newer architecture documentation when there is evidence that it superseded older documentation.
Explicitly identify documentation that appears historical or obsolete.
Explain the platform first at three levels.
LEVEL 1 — 60 SECOND EXPLANATION
Explain the entire platform as if answering:
“Tell me about the system you worked on.”
LEVEL 2 — 5 MINUTE ARCHITECTURE EXPLANATION
Explain:
business problem
users/clients
major components
transaction lifecycle
databases
messaging
external systems
failure handling
scale
deployment
LEVEL 3 — 30 MINUTE DEEP DIVE
Give the detailed technical explanation that a Staff/Principal engineer could discuss.
Explain:
business purpose
payment domain/problem being solved
transaction types
supported workflows
upstream systems
downstream systems
external integrations
internal consumers
major business entities
transaction states
payment lifecycle
important domain terminology
Create a glossary of every important domain term found in the documentation.
Reconstruct the architecture layer by layer.
Include where applicable:
Client / Consumer
↓
API Gateway / Entry Layer
↓
Orchestration
↓
Business Services
↓
Event / Messaging Infrastructure
↓
Persistence
↓
External Systems
↓
Settlement / Reconciliation / Reporting
Do not assume this structure exists. Reconstruct the actual one from documentation.
Provide both:
A. Logical architecture
B. Runtime architecture
For every component identify:
component/service name
responsibility
why it exists
inputs
outputs
upstream dependencies
downstream dependencies
APIs consumed
APIs exposed
events consumed
events produced
databases/tables used
caches used
external systems
synchronous/asynchronous behavior
failure behavior
retry behavior
scalability characteristics
deployment characteristics
Build a complete service catalog.
For EVERY discovered microservice/component provide:
SERVICE: <name>
Purpose:
Why required:
Responsibilities:
Does NOT own:
Upstream services:
Downstream services:
API endpoints:
Incoming events:
Outgoing events:
Kafka topics/queues:
Database:
Important tables/entities:
Caching:
Configuration:
Scheduling:
Retry:
Timeout:
Error handling:
Idempotency:
Concurrency model:
Deployment:
Horizontal scaling:
Observability:
Known bottlenecks:
Known incidents:
Related documentation:
Confidence:
If the information is unavailable, explicitly write “Not found in current documentation”.
Do not silently omit fields.
Reconstruct every major payment flow.
For each flow provide a textual sequence diagram:
Actor
|
v
Service A
|
| request/event
v
Service B
|
v
Database
|
v
Event Bus
|
v
Service C
|
v
External System
For EVERY step explain:
What happens?
Which service performs it?
What data enters?
What validation happens?
What transformation happens?
What database operation happens?
What event is generated?
What happens next?
What happens if this step fails?
Can this operation safely be retried?
What prevents duplicate processing?
Investigate multiple flows where they exist:
happy path
failure path
timeout path
technical exception
business exception
retry
replay
recovery
cancellation/reversal
reconciliation
scheduled/batch processing
asynchronous processing
If Kafka/message queues/event streaming are present, deeply investigate them.
Build:
PRODUCER → TOPIC/EVENT → CONSUMER
For every event/topic determine:
event purpose
producer
consumer(s)
schema/payload where documented
partitioning
ordering requirements
consumer groups
retry strategy
acknowledgment strategy
duplicate handling
dead-letter handling
replay behavior
retention
failure handling
backpressure
delivery semantics where documented
idempotency
monitoring
Explain WHY asynchronous communication was chosen where the documentation provides evidence.
Investigate persistence deeply.
Identify:
database technologies
schema ownership
major schemas
important tables
relationships
transaction boundaries
writes
reads
indexes
configuration-driven persistence
mappings
JSON → database mappings
audit/history data
status tables
transaction tables
reconciliation data
database failure handling
duplicate protection
locking/concurrency
performance optimizations
archival/purge strategy
connection pooling
database scaling
Where config-driven persistence exists, explain:
Payload
↓
Configuration
↓
JSON tag / field mapping
↓
Table
↓
Column
↓
Persistence logic
Explain advantages, disadvantages and failure modes of such architecture.
Create a failure taxonomy.
Identify:
business failures
technical failures
transient failures
permanent failures
timeout
downstream outage
DB outage
Kafka outage
malformed event
partial processing
duplicate processing
out-of-order events
service crash
network issue
configuration issue
Then explain how each category is handled.
Build tables:
Failure
Detection
Retry?
Replay?
DLQ?
Manual Intervention?
Data Consistency Impact
Recovery Mechanism
Investigate this especially deeply.
Find every document related to:
event replay
exception processing
retry
recovery
job scheduler
job executor
failed event processing
priority processing
CRITICAL/HIGH/MEDIUM/LOW priority if present
dead-letter processing
manual replay
automated replay
Explain:
Event failure
↓
Failure classification
↓
Persistence / queue
↓
Priority
↓
Scheduler
↓
Executor
↓
Target service
↓
Replay
↓
Success / retry / escalation
Identify exactly how scheduling, prioritization and retries work according to documentation.
Payments systems cannot blindly execute operations twice.
Investigate:
idempotency keys
transaction IDs
request IDs
correlation IDs
uniqueness constraints
processed event tables
duplicate detection
consumer idempotency
exactly-once assumptions
at-least-once processing
reconciliation safeguards
Explain how duplicate financial processing is prevented.
If this isn't documented, explicitly identify it as an architectural question rather than making assumptions.
Determine where possible:
ACID transactions
distributed transactions
eventual consistency
transaction boundaries
saga-like flows
compensation
rollback
asynchronous state propagation
state machines
reconciliation
Explain scenarios where:
Service A succeeds
Service B fails
and how system consistency is restored.
Investigate architecture related to scale.
Identify:
stateless/stateful services
horizontal scaling
Kubernetes replicas
autoscaling
partitions
parallel consumers
thread pools
worker pools
batch sizes
database bottlenecks
queue bottlenecks
caching
connection pools
throughput limitations
backpressure
Include actual numbers ONLY if safely documented and appropriate for internal use.
Otherwise use X TPS / Y million transactions / Z ms placeholders.
Explain likely scaling boundaries separately from documented facts.
Find documents related to:
latency
CPU
memory
profiling
GC
load testing
performance testing
throughput
regression
benchmarking
response time
Explain:
important latency paths
expensive operations
synchronous bottlenecks
async optimizations
DB optimizations
serialization/deserialization
networking
concurrency
JVM/runtime tuning if relevant
CPU optimizations
memory optimizations
Identify known performance improvements and why they helped.
Explain:
namespaces
deployments
pods
replicas
services
ingress
config maps
secrets conceptually
resource requests/limits
HPA
readiness probes
liveness probes
rolling deployments
service discovery
environment configuration
production/staging differences
resilience
failure recovery
DO NOT expose actual credentials or secret values.
Investigate:
Code
↓
Build
↓
Unit Test
↓
Integration Test
↓
Artifact
↓
Container
↓
Registry
↓
Deployment
↓
Validation
↓
Production
Explain tools and gates where documented.
Investigate:
logging
metrics
dashboards
tracing
correlation IDs
alerts
health checks
transaction monitoring
production diagnostics
Explain:
“When a payment fails in production, how would an engineer investigate it?”
Produce the complete debugging path.
At an architectural level explain documented controls including:
authentication
authorization
service-to-service authentication
encryption
secrets management
audit logging
PII handling
payment-data handling
tokenization
access controls
relevant compliance requirements
Do NOT display secret values, credentials, private keys, access tokens or confidential customer information.
Investigate:
HA
failover
graceful degradation
retries
circuit breakers
timeouts
bulkheads
redundant services
disaster recovery
multi-region / multi-zone architecture
RTO/RPO where documented
database recovery
messaging recovery
Explain what happens when each critical dependency becomes unavailable.
If applicable investigate:
clearing
settlement
reconciliation
transaction matching
mismatch detection
adjustment
end-of-day processing
batch processing
reports
external reconciliation
Explain how the system knows:
“We believe transaction X succeeded, but the downstream/provider believes otherwise.”
Find RFCs/ADRs/design discussions.
For each major decision:
Problem:
Previous architecture:
Options considered:
Chosen design:
Why:
Trade-offs:
Migration strategy:
Current state:
Outcome:
Examples could include:
sync → async
monolith → microservices
DB polling → event streaming
hard-coded persistence → config-driven persistence
manual retry → event replay
single worker → parallel workers
Only include these if supported by documentation.
Construct a timeline:
Original architecture
↓
Problem encountered
↓
Architecture change
↓
Migration
↓
Current architecture
Use document dates/version history wherever available.
Search for incidents/postmortems related to this platform.
Do NOT expose sensitive operational details unnecessarily.
Summarize technically:
Incident:
Architecture involved:
Trigger:
Failure propagation:
Root cause:
Detection:
Impact category:
Immediate mitigation:
Permanent fix:
Architectural lesson:
Use this to explain why certain current architectural patterns exist.
Produce:
Service A
├── calls Service B
├── publishes Event X
├── writes Database Y
└── consumes Event Z
Do this recursively for every significant service.
Then generate a complete dependency matrix:
Service | Calls | Called By | Produces | Consumes | Database | External Dependency
For every major business entity answer:
Who creates it?
Who owns it?
Who modifies it?
Where is it persisted?
Which services consume it?
What is its lifecycle?
Generate multiple Mermaid diagrams where enough information exists:
System context diagram
Container/service architecture
Payment sequence diagram
Event-driven flow
Persistence architecture
Failure/replay flow
Deployment architecture
Data lifecycle
Service dependency graph
If Mermaid is unsuitable, use ASCII diagrams.
After understanding the system, act as interviewers from:
Google / Google Pay
Amazon / Amazon Pay
PayPal
JPMorgan Chase
Goldman Sachs
Razorpay
Paytm
Stripe-like payment engineering teams
Generate difficult questions they could ask about this architecture.
For EVERY question provide:
Question:
Strong Answer:
Architecture Evidence:
Potential Follow-up:
Strong Follow-up Answer:
Questions should cover:
distributed systems
payments
microservices
databases
Kafka
consistency
idempotency
scalability
reliability
performance
security
Kubernetes
production debugging
system design
For every major design choice repeatedly ask:
WHY?
Why Kafka?
Why asynchronous?
Why this DB?
Why microservices?
Why replay?
Why scheduler + executor?
Why priority queues?
Why config-driven persistence?
Why not synchronous calls?
Why not direct DB writes?
Why not exactly-once?
Why not a distributed transaction?
Why this consistency model?
Only state documented answers as facts.
Where the documentation doesn't answer WHY, give a clearly labelled architectural inference.
For major patterns provide:
Pattern:
Benefit:
Cost:
Alternative:
Why chosen:
Where it can fail:
How it could evolve:
Without fabricating personal ownership, classify the knowledge into:
A. Things an engineer working on this platform should understand.
B. Components someone could reasonably discuss as platform architecture knowledge.
C. Components requiring direct implementation experience before claiming ownership.
D. Architecture concepts transferable to another large-scale payment company.
Map the architecture to competencies relevant to:
Software Engineer
Backend Engineer
Senior Backend Engineer
Distributed Systems Engineer
Payments Engineer
Platform Engineer
Full Stack Engineer
Backend + AI Engineer
Forward Deployed Engineer
SRE / Production Engineer
DO NOT falsely claim that I implemented components merely because they exist in the architecture.
Instead create an evidence bank with fields:
Architecture Area:
What the platform does:
Engineering complexity:
Technical concepts demonstrated:
Possible interview discussion angle:
What requires confirmation of my personal contribution:
Metrics that would strengthen the story:
Missing information to investigate:
Use placeholders such as:
X TPS
Y million transactions/day
Z ms latency
A% improvement
B services
C Kafka partitions
rather than inventing numbers.
Extract reusable principles from this architecture.
For example:
handling at-least-once delivery
ensuring payment idempotency
replay architecture
event-driven processing
database reliability
asynchronous workflows
reconciliation
partial failure recovery
observability
high availability
Explain how each pattern could apply to a generic payment system.
After completing the investigation create:
TOP ARCHITECTURE QUESTIONS STILL UNANSWERED
Rank them:
P0 — essential
P1 — important
P2 — useful
For every unanswered question suggest exact Confluence searches that should be performed next.
At the end maintain a documentation/source map.
For each architectural conclusion list:
Topic:
Source page(s):
Page date/update date:
Confidence:
Current/Historical:
Important notes:
This lets me verify conclusions manually.
Produce ONE extremely comprehensive technical notebook with these chapters:
Executive Summary
Business Context
Domain Terminology
Platform Context
Current High-Level Architecture
Service Catalog
Service Dependency Graph
End-to-End Payment Lifecycle
API Architecture
Event-Driven Architecture
Kafka / Messaging
Database Architecture
Persistence Framework
State Management
Distributed Transactions
Consistency Model
Idempotency
Retry Architecture
Event Replay
Exception Processing
Job Scheduler / Job Executor
Failure Handling
Reconciliation
Performance
Scalability
Reliability / Resilience
Kubernetes / Infrastructure
CI/CD
Observability
Production Debugging
Security
Architectural Evolution
Important Design Decisions
Incident Learnings
Known Bottlenecks
Architectural Trade-offs
Current Technical Debt
System Design Lessons
Interview Questions + Answers
Career/Role Mapping
Resume Evidence Bank
Missing Information
Architecture Questions To Verify
Architecture Diagrams
Source / Documentation Map
DO NOT give me a shallow summary.
Think like you have joined this team as a Staff Engineer and tomorrow you must own the platform.
The goal is that after studying your output I should be able to answer questions such as:
“What happens from the moment a payment request enters the platform until completion?”
“What happens when an intermediate service crashes?”
“How do you prevent the same payment from being processed twice?”
“How do Kafka consumers recover after failure?”
“How does replay work?”
“How does database persistence work?”
“How do services scale?”
“What happens when downstream services are unavailable?”
“How do you investigate a failed payment?”
“How is consistency achieved across microservices?”
“What architectural bottlenecks exist?”
“Why was this architecture chosen?”
“What would you redesign if transaction volume increased by 10x?”
Do multiple rounds of Confluence investigation where necessary before concluding that information is unavailable.
Accuracy and architectural depth are more important than speed or response length.

