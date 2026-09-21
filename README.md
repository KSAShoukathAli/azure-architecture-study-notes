# Azure Architecture Study Notes

A visual architecture notebook for Azure integration, identity, networking, security, messaging, and platform concepts.

The notes are organized in two complementary styles:

- **Reference Notes** - concise architecture reference for quick lookup.
- **Feynman Way of Understanding** - first-principles explanations focused on mechanisms, tradeoffs, failure modes, and rebuilding the concept from fundamentals.

---

## 🌐 Live Study Site

**[Open Azure Architecture Study Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/)**

---

## OAuth2 & Azure Identity

- **[OAuth2 & Azure Identity - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/oauth/)**
- **[OAuth2, App Service & AKS Identity - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/oauth/oauth2-app-service-aks-identity-reference/)**
- **[OAuth2, App Service & AKS Identity - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/oauth/oauth2-app-service-aks-identity-feynman/)**

Topics include OAuth2 flows, Entra ID, access tokens, managed identities, App Service authentication, AKS workload identity, and identity boundaries.

---

## Azure Networking

- **[Azure Networking - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/networking/)**
- **[Azure Networking Concepts - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/networking/azure-networking-concepts-reference/)**
- **[Azure Networking Concepts - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/networking/azure-networking-concepts-feynman/)**

Core mental model:

> **Name -> Address -> Route -> Allow**

Topics include VNets, CIDR, subnets, routing, NSGs, VNet peering, service endpoints, private endpoints, Private Link, private DNS, DNS Private Resolver, APIM networking modes, hybrid DNS, network policies, UDRs, and troubleshooting.

---

## Azure Logic Apps

- **[Azure Logic Apps - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/logic-apps/)**
- **[Azure Logic Apps - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/logic-apps/azure-logic-apps-reference/)**
- **[Azure Logic Apps - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/logic-apps/azure-logic-apps-feynman/)**

The Logic Apps material covers:

- Consumption vs Standard
- triggers and actions
- stateful vs stateless workflows
- built-in vs managed connectors
- managed identity and authentication
- Private Endpoint and VNet Integration
- Standard storage dependencies
- retries, `runAfter`, scopes, and idempotency
- B2B / EDI with X12, EDIFACT, AS2, schemas, maps, agreements, and Integration Accounts
- concurrency, `splitOn`, ordering, and parallel vs sequential processing
- Liquid, XSLT, Flat File, XML, and Data Mapper transformations
- long-running workflows, delays, Until loops, and webhook callbacks
- Application Insights, run history, correlation IDs, and observability
- architecture limits and Consumption vs Standard cost considerations

---

## Azure API Management

- **[Azure API Management - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/apim/)**
- **[Azure API Management - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/apim/azure-api-management-reference/)**
- **[Azure API Management - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/apim/azure-api-management-feynman/)**

The APIM material covers:

- gateway, management plane, developer portal, and self-hosted gateway
- APIs, operations, products, subscriptions, and subscription keys
- caller authentication vs APIM-to-backend authentication
- OAuth2 / OpenID Connect / JWT validation
- managed identity for backend access
- policy execution: inbound, backend, outbound, and on-error
- policy scopes, `<base />`, fragments, expressions, and `context.*`
- routing, backend URLs, `rewrite-uri`, and `set-backend-service`
- rate limiting vs quotas
- backend pools and circuit breakers
- caching and external Redis-compatible cache
- versions vs revisions
- named values and Key Vault integration
- Application Insights, diagnostics, correlation, and tracing
- Private Endpoint, VNet Integration, and VNet Injection
- classic vs v2 tier architecture
- internal-mode DNS, NSGs, UDRs, forced tunneling, and self-call behavior
- OpenAPI onboarding and Terraform/IaC considerations
- workspaces and delegated API governance
- boundaries between APIM and B2B / messaging integration workloads

---

## Azure Messaging

- **[Azure Messaging - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/messaging/)**
- **[Azure Messaging - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/messaging/azure-messaging-reference/)**
- **[Azure Messaging - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/messaging/azure-messaging-feynman/)**

Core decision model:

> **Durable command/work -> Service Bus**  
> **Discrete event notification -> Event Grid**  
> **High-volume replayable stream -> Event Hubs**

The Messaging material covers:

- Service Bus queues vs topics/subscriptions
- competing consumers
- Peek-Lock vs Receive-and-Delete
- lock duration, renewal, lock loss, and prefetch implications
- at-least-once delivery and idempotent consumers
- sessions and per-key FIFO ordering
- duplicate detection and its limits
- dead-letter queues and poison-message handling
- forwarding, deferral, scheduling, TTL, filters, and transactions
- Standard vs Premium Service Bus architecture
- message-size limits and the claim-check pattern
- Service Bus vs Azure Storage Queues
- Geo-DR vs Geo-Replication
- Managed Identity, RBAC, Private Link, and networking
- Event Grid classic resource model vs Event Grid Namespaces
- Event Grid push vs pull delivery
- Event Grid retry, dead-lettering, and no-order guarantee
- Event Hubs partitions, partition keys, offsets, and consumer groups
- checkpointing and replay
- Event Hubs Capture
- Event Hubs tiers and Kafka compatibility
- why a retained stream is not automatically a work queue
- current Azure SDK guidance and legacy Service Bus SDK/SBMP retirement

Feynman questions used throughout the Messaging section:

> **Must the work survive?**  
> **Who owns processing?**  
> **What exactly must stay ordered?**  
> **Can the same message arrive twice?**  
> **Do consumers need to replay history?**

---

## Azure Functions + Durable Functions

- **[Azure Functions + Durable Functions - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/functions/)**
- **[Azure Functions + Durable Functions - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/functions/azure-functions-reference/)**
- **[Azure Functions + Durable Functions - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/functions/azure-functions-feynman/)**

Core mental model:

> **Event -> Function -> small piece of work**  
> **Long-running coordination -> Durable Orchestrator -> persisted history -> replay**

The Functions material covers:

- triggers and input/output bindings
- HTTP, Service Bus, Event Grid, Event Hubs, and Timer triggers
- Flex Consumption, Consumption, Premium, Dedicated, and Container Apps hosting
- cold starts, always-ready instances, scale-out, and concurrency
- per-function scaling behavior in Flex Consumption
- Service Bus settlement, lock renewal, redelivery, poison messages, and DLQ interaction
- Managed Identity, Key Vault references, networking, and host storage dependencies
- VNet integration, Private Endpoint considerations, and private DNS dependencies
- Application Insights and operational troubleshooting
- deployment models, deployment slots, and hosting-plan constraints
- function timeouts, HTTP response limits, and shutdown grace periods
- Durable orchestrators, activities, clients, and entities
- checkpoints, persisted history, deterministic replay, and orchestration state
- durable timers and external events
- function chaining and fan-out / fan-in
- async HTTP API, human interaction, and monitor patterns
- saga / compensation patterns
- Durable retries, failure propagation, and activity idempotency
- orchestration versioning for long-running instances
- Durable storage providers and task-hub migration constraints
- Durable Functions vs Logic Apps vs plain Azure Functions
- conceptual mapping from BizTalk orchestrations to Durable Functions

Key Durable mental model:

> The orchestrator does **not** keep a process or thread alive for hours or days.  
> It persists history, goes idle, and later replays that history to rebuild deterministic state.

---


## End-to-End Observability

- **[End-to-End Observability - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/observability/)**
- **[End-to-End Observability - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/observability/azure-observability-reference/)**
- **[End-to-End Observability - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/observability/azure-observability-feynman/)**

Core mental model:

> **Observability is not "collect logs from everything."**  
> **It is reconstructing what happened to one business transaction across a distributed system.**

The Observability material covers:

- metrics, logs, traces, spans, and causal relationships
- W3C trace context and distributed tracing
- technical trace IDs vs runtime execution IDs vs business correlation IDs
- Application Insights and workspace-based architecture
- Azure Monitor and Log Analytics
- OpenTelemetry and Azure Monitor OpenTelemetry instrumentation
- APIM, Logic Apps, Service Bus, Functions, Event Grid, and Event Hubs telemetry
- Service Bus trace propagation and queue residence time
- cross-service KQL using an opaque business correlation ID
- sampling, cardinality, retention, and telemetry cost
- SLI, SLO, error budgets, burn rate, and alerting
- alert processing rules and maintenance-window suppression
- Standard availability tests and private-endpoint monitoring patterns
- Azure Monitor Private Link Scope (AMPLS)
- PHI-safe telemetry patterns for healthcare integration
- avoiding patient identifiers and payload bodies in telemetry
- DCR/workspace transformations for filtering or redaction before storage

Key observability model:

> **Trace ID = technical causal journey**  
> **Business correlation ID = stable business journey**  
> A retry, redelivery, or asynchronous boundary can change the technical trace without changing the business transaction.

---


## BizTalk to Azure Mapping

- **[BizTalk to Azure Mapping - All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/biztalk-to-azure/)**
- **[BizTalk to Azure Mapping - Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/biztalk-to-azure/biztalk-to-azure-reference/)**
- **[BizTalk to Azure Mapping - Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/biztalk-to-azure/biztalk-to-azure-feynman/)**

Core mental model:

> **Do not migrate the BizTalk product topology. Migrate the responsibilities, guarantees, and behavior.**

The BizTalk migration material covers:

- Logic Apps Standard as the primary BizTalk successor and migration nucleus
- why BizTalk migration is not lift-and-shift
- receive locations, receive ports, adapters, pipelines, maps, orchestrations, and send ports
- why the BizTalk MessageBox has no single Azure replacement
- publish/subscribe routing and subscription behavior
- correlation sets, convoys, Service Bus sessions, workflow state, and external state
- ordered delivery vs sequential-convoy behavior
- suspended instances, workflow failures, DLQs, retry, replay, and compensation
- BizTalk host throttling vs explicit Azure backpressure and concurrency controls
- Business Rules Engine migration and current Azure Rules Engine limits
- B2B migration with Integration Account, X12, EDIFACT, AS2, and RosettaNet
- healthcare migration from BTAHL7 to Logic Apps HL7 encode/decode
- MLLP constraints and Logic Apps Standard Hybrid
- ESB Toolkit itinerary migration and routing-slip patterns
- coexistence and flow-by-flow cutover between BizTalk and Azure
- SB-Messaging adapter migration from SBMP to AMQP
- Azure Logic Apps Migration Agent and GitHub Copilot governance considerations
- where custom BizTalk code fits better as workflow-scoped .NET vs a separate Function App
- observability and operational differences between BizTalk tracking and Azure Monitor

Key migration model:

> **BizTalk feature name != Azure service name**  
> First identify what the BizTalk artifact was doing.  
> Then choose the Azure mechanism that preserves the required behavior.

---

## Repository Structure

```text
azure-architecture-study-notes/
│
├── index.html
├── README.md
├── .nojekyll
│
├── oauth/
│   ├── index.html
│   ├── oauth2-app-service-aks-identity-reference/
│   │   └── index.html
│   └── oauth2-app-service-aks-identity-feynman/
│       └── index.html
│
├── networking/
│   ├── index.html
│   ├── azure-networking-concepts-reference/
│   │   └── index.html
│   └── azure-networking-concepts-feynman/
│       └── index.html
│
├── logic-apps/
│   ├── index.html
│   ├── azure-logic-apps-reference/
│   │   └── index.html
│   └── azure-logic-apps-feynman/
│       └── index.html
│
├── apim/
│   ├── index.html
│   ├── azure-api-management-reference/
│   │   └── index.html
│   └── azure-api-management-feynman/
│       └── index.html
│
├── messaging/
│   ├── index.html
│   ├── azure-messaging-reference/
│   │   └── index.html
│   └── azure-messaging-feynman/
│       └── index.html
│
├── functions/
│   ├── index.html
│   ├── azure-functions-reference/
│   │   └── index.html
│   └── azure-functions-feynman/
│       └── index.html
│
├── observability/
│   ├── index.html
│   ├── azure-observability-reference/
│   │   └── index.html
│   └── azure-observability-feynman/
│       └── index.html
│
├── biztalk-to-azure/
│   ├── index.html
│   ├── biztalk-to-azure-reference/
│   │   └── index.html
│   └── biztalk-to-azure-feynman/
│       └── index.html
│
├── reliability-patterns/
├── private-connectivity-dns/
├── workload-identity/
├── terraform-cicd/
├── integration-security/
├── ai-gateway-mcp/
└── healthcare-integration/
```

---

## Learning Approach

These notes are designed around a first-principles / Feynman-style learning loop:

1. Start with the **problem**, not the Azure product name.
2. Identify the few **fundamental facts**.
3. Rebuild the mechanism from those facts.
4. Remove unnecessary jargon.
5. Draw the **smallest useful diagram**.
6. Predict what should happen.
7. Change one thing and predict again.
8. Find where the model breaks.
9. Explain the concept from a blank page.
10. Return to documentation only for the gaps.

The goal is not just to recognize Azure terminology.

The goal is to be able to answer:

> **Why?**  
> **How?**  
> **What if?**  
> **Where does it break?**  
> **Can I rebuild it from first principles?**

---

## Roadmap

### Next

1. **Reliability & Idempotency Patterns**
   - retry / backoff / jitter
   - poison-message handling
   - idempotent consumers
   - duplicate detection
   - outbox / inbox
   - saga / compensation
   - exactly-once misconceptions
   - replay and recovery

### Then

2. **Private Connectivity & DNS**
3. **Workload Identity**
4. **Terraform + CI/CD + APIOps**
5. **Integration Security Architecture**
6. **AI Gateway + MCP**
7. **Healthcare Integration**

---

## Updating the Site

GitHub Pages publishes the files that are actually committed to the configured publishing branch.

For BizTalk to Azure Mapping, verify the files exist locally:

```powershell
Test-Path .\biztalk-to-azure\index.html
Test-Path .\biztalk-to-azure\biztalk-to-azure-reference\index.html
Test-Path .\biztalk-to-azure\biztalk-to-azure-feynman\index.html
```

All three commands should return `True`.

Then stage the README and topic folder explicitly:

```powershell
git status
git add README.md biztalk-to-azure
git status
git diff --cached --name-status
git commit -m "Add BizTalk to Azure migration study notes"
git push origin main
```

After the push, verify Git is tracking the published paths:

```powershell
git ls-tree -r --name-only HEAD | Select-String "^biztalk-to-azure/"
```

Expected published URLs:

- **https://ksashoukathali.github.io/azure-architecture-study-notes/biztalk-to-azure/**
- **https://ksashoukathali.github.io/azure-architecture-study-notes/biztalk-to-azure/biztalk-to-azure-reference/**
- **https://ksashoukathali.github.io/azure-architecture-study-notes/biztalk-to-azure/biztalk-to-azure-feynman/**

Live site:

**https://ksashoukathali.github.io/azure-architecture-study-notes/**
