# Azure Architecture Study Notes

A visual architecture notebook for Azure integration, identity, networking, security, and platform concepts.

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

> **Name → Address → Route → Allow**

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

Feynman questions used throughout the Logic Apps section:

> **What wakes it?**  
> **What must survive?**  
> **Where does the operation run?**  
> **What happens when it fails?**  
> **How much concurrency is safe?**  
> **How does the data change shape?**  
> **What if the process takes hours?**  
> **Can I trace one business transaction end-to-end?**

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
├── private-endpoint/
├── apim/
├── aks-identity/
└── terraform/
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

---

## Planned Topics

Future sections can follow the same Reference + Feynman pattern:

- Azure API Management
- Private Endpoint / Private Link deep dive
- Azure Service Bus
- AKS identity and networking
- Terraform for Azure architecture
- Azure security architecture
- traffic management and load balancing
- outbound connectivity, SNAT, NAT Gateway, and Azure Firewall
- message-level security and enterprise integration patterns
