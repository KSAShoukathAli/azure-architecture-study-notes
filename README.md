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
├── observability/
├── biztalk-to-azure/
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

1. **Azure Functions + Durable Functions**
   - triggers and bindings
   - Flex Consumption
   - scaling and cold starts
   - Service Bus triggers
   - Durable orchestration
   - fan-out / fan-in
   - saga / compensation
   - async HTTP and human-interaction patterns

2. **End-to-End Observability**
   - Application Insights
   - Log Analytics
   - KQL
   - distributed correlation
   - trace APIM -> Logic Apps -> Service Bus -> Function

3. **BizTalk to Azure Mapping**
   - receive locations and ports
   - pipelines
   - maps
   - orchestrations
   - send ports
   - correlation
   - suspended messages
   - where there is no one-to-one Azure replacement

4. **Reliability & Idempotency Patterns**
   - retry / backoff / jitter
   - poison-message handling
   - outbox
   - saga / compensation
   - idempotency
   - exactly-once misconceptions

### Then

5. **Private Connectivity & DNS**
6. **Workload Identity**
7. **Terraform + CI/CD + APIOps**
8. **Integration Security Architecture**
9. **AI Gateway + MCP**
10. **Healthcare Integration**

---

## Updating the Site

After changing or adding study pages:

```powershell
git status
git add .
git commit -m "Update Azure architecture study notes"
git push
```

GitHub Pages publishes from the `main` branch.

Live site:

**https://ksashoukathali.github.io/azure-architecture-study-notes/**
