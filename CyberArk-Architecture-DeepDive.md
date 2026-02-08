# CyberArk Architecture – Deep Technical Flow

## Core Security Objective

CyberArk protects privileged accounts such as:

- Local Administrator accounts
- Domain Admin accounts
- Service accounts
- Application accounts
- Root accounts (Linux)

These accounts are primary attack targets.

---

## Privileged Account Protection Flow

User → PVWA → Request Access  
PVWA → Vault → Validate Permissions  
Vault → CPM → Manage Password  
User → PSM → Launch Session  
PSM → Target Server → Connect as Local Admin  
PSM → Record Session  
CPM → Rotate Password After Use  

---

## Mermaid Architecture Flow Diagram

```mermaid
flowchart LR
    User --> PVWA
    PVWA --> Vault
    Vault --> CPM
    PVWA --> PSM
    PSM --> TargetServer
    CPM --> TargetServer


