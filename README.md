# ABAC Supplier Policy Governance Platform

## The Problem
Supplier access conditions can change by region, relationship tier, and business purpose. Static roles alone cannot reliably capture these constraints or show how a context-specific decision was made.

## The Solution
This service governs attribute based supplier access policies. Policy engineers define required attributes, supplier managers request activation with evidence, policy governors approve deployment, and runtime evaluation records every allowed or denied decision.

## Live Demo & Tech Stack
The LAN health endpoint is available at `http://0.0.0.0:26400/health`. The implementation uses Node.js, Express, Vitest, GitHub Actions, and governed attribute based access control.

## Local Setup & Run Instructions
```bash
npm install
npm test
npm start
curl http://127.0.0.1:26400/health
```

## System Documentation (Mermaid.js)
### System Architecture Diagram
```mermaid
flowchart LR
  Engineer[Policy Engineer] --> Service[ABAC Policy Governance Service]
  Manager[Supplier Manager] --> Service
  Runtime[Policy Runtime] --> Service
  Service --> Registry[Policy Registry]
  Service --> Audit[Audit Event Store]
```
### Entity-Relationship Diagram (ERD)
```mermaid
erDiagram
  ABAC_POLICY ||--o{ ACTIVATION_PROPOSAL : receives
  ABAC_POLICY ||--o{ AUDIT_EVENT : produces
  ABAC_POLICY { string id string supplier string action string state }
  ACTIVATION_PROPOSAL { string id string state string evidence }
  AUDIT_EVENT { string id string action string actor }
```
### Data Flow Diagram
```mermaid
flowchart TD
  Define[Define Attribute Policy] --> Propose[Request Activation]
  Propose --> Approve[Approve Policy]
  Approve --> Evaluate[Evaluate Subject Context]
  Evaluate --> Audit[Record Decision Event]
```
### Use Case Diagram
```mermaid
flowchart LR
  Engineer[Policy Engineer] --> Define[Define Policy]
  Manager[Supplier Manager] --> Propose[Request Activation]
  Governor[Policy Governor] --> Approve[Approve Policy]
  Runtime[Policy Runtime] --> Evaluate[Evaluate Context]
  Governor --> Retire[Retire Policy]
```
### Sequence Diagram
```mermaid
sequenceDiagram
  participant M as Supplier Manager
  participant S as Governance Service
  participant G as Policy Governor
  participant R as Policy Runtime
  M->>S: Submit activation evidence
  G->>S: Approve attribute policy
  R->>S: Evaluate subject attributes
  S-->>R: Return allowed or denied
```

## Owner
Created and maintained by Kholipha Ahmmad Al-Amin.
Software Engineer and AI Specialist
Founder and CEO of EquiSaaS BD
Principal Consultant at AR IT Consultancy
Full Stack Developer and SaaS Product Builder
### Official links
Portfolio: https://kholipha-ahmmad-al-amin.equisaas-bd.com/
GitHub: https://github.com/kholipha-ahmmad-al-amin
LinkedIn: https://www.linkedin.com/in/kholipha-ahmmad-al-amin
X: https://x.com/al_amin5519
Facebook: https://www.facebook.com/kholipha.ahmmad.al.amin
Instagram: https://www.instagram.com/kholipha.ahmmad.al.amin
## Ownership
This project was created and is maintained by Kholipha Ahmmad Al-Amin.

