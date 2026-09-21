# Azure Architecture Study Notes

A visual architecture notebook for Azure integration, identity, networking, security, and platform concepts.

## 🌐 Live Study Site

**[Open Azure Architecture Study Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/)**

### OAuth2 & Azure Identity

- **[OAuth2 & Azure Identity — All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/oauth/)**
- **[OAuth2, App Service & AKS Identity — Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/oauth/oauth2-app-service-aks-identity-reference/)**
- **[OAuth2, App Service & AKS Identity — Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/oauth/oauth2-app-service-aks-identity-feynman/)**

### Azure Networking

- **[Azure Networking — All Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/networking/)**
- **[Azure Networking Concepts — Reference Notes](https://ksashoukathali.github.io/azure-architecture-study-notes/networking/azure-networking-concepts-reference/)**
- **[Azure Networking Concepts — Feynman Way of Understanding](https://ksashoukathali.github.io/azure-architecture-study-notes/networking/azure-networking-concepts-feynman/)**

## Repository Structure

```text
azure-architecture-study-notes/
├── index.html
├── .nojekyll
├── README.md
├── oauth/
│   ├── index.html
│   ├── oauth2-app-service-aks-identity-reference/
│   │   └── index.html
│   └── oauth2-app-service-aks-identity-feynman/
│       └── index.html
├── networking/
│   ├── index.html
│   ├── azure-networking-concepts-reference/
│   │   └── index.html
│   └── azure-networking-concepts-feynman/
│       └── index.html
├── private-endpoint/
│   └── index.html
├── apim/
│   └── index.html
├── logic-apps/
│   └── index.html
├── aks-identity/
│   └── index.html
└── terraform/
    └── index.html
```

## GitHub Pages

This repository is published from the `main` branch at the repository root.

**Rendered site**  
https://ksashoukathali.github.io/azure-architecture-study-notes/

**GitHub repository**  
https://github.com/KSAShoukathAli/azure-architecture-study-notes

## Adding a New Study Note

Use a descriptive topic-based folder name and place the finished self-contained HTML inside it as `index.html`.

Example:

```text
private-endpoint/
└── private-endpoint-feynman/
    └── index.html
```

That page would render at:

```text
https://ksashoukathali.github.io/azure-architecture-study-notes/private-endpoint/private-endpoint-feynman/
```

For topics with multiple documents, use the topic folder as a landing page:

```text
oauth/
├── index.html
├── oauth2-app-service-aks-identity-reference/
│   └── index.html
└── oauth2-app-service-aks-identity-feynman/
    └── index.html
```

## Recommended Learning-Note Structure

For deeper Feynman-style notes, use this pattern:

```text
Problem
  ↓
Fundamental facts
  ↓
Rebuild the mechanism
  ↓
Smallest useful diagram
  ↓
What if I remove/change something?
  ↓
Boundary / where the statement stops being true
  ↓
Blank-page explanation
```

Reference notes can stay more concise and focus on the final architecture, workflow, terminology, and diagrams.

## Updating the Site

After adding or editing notes:

```powershell
git add .
git commit -m "Update study notes"
git push
```

GitHub Pages will republish the site from the latest commit on `main`.

## Privacy

GitHub Pages is public for this repository. Do not publish employer-confidential architecture, credentials, internal URLs, customer data, or proprietary diagrams here.
