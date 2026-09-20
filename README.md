# Azure Architecture Study Notes

A visual, Feynman-style architecture notebook published with GitHub Pages.

## Structure

```text
azure-architecture-study-notes/
├── index.html
├── .nojekyll
├── README.md
├── oauth/
│   └── index.html
├── networking/
│   └── index.html
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

## Publish with GitHub Pages

1. Create a GitHub repository named `azure-architecture-study-notes`.
2. Upload all files and folders from this package to the repository root.
3. Commit to the `main` branch.
4. Open **Settings → Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**.
6. Select **main** and **/ (root)**.
7. Save.

Your site will normally be available at:

```text
https://<your-github-username>.github.io/azure-architecture-study-notes/
```

## Adding a new study note

Each topic folder has its own `index.html`. Replace the placeholder with the finished self-contained HTML and keep the same filename.

Example:

```text
private-endpoint/index.html
```

will render at:

```text
https://<your-github-username>.github.io/azure-architecture-study-notes/private-endpoint/
```

## Recommended note structure

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

## Privacy

GitHub Pages should be treated as public unless you are using a GitHub offering that explicitly supports private Pages for your account/organization. Do not publish employer-confidential architecture, credentials, internal URLs, or proprietary diagrams here.
