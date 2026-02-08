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
Component Internal Responsibilities
Vault

Stores all privileged credentials

Encrypted storage

Central trust component

CPM

Handles:

Password rotation

Password reconciliation

Policy enforcement

Targets:

Local admin accounts

Service accounts

Domain accounts

PSM

Session proxy

Session recording

Keystroke logging

Prevents direct credential exposure

PVWA

Access portal

Authorization layer

Request management

Local Administrator Account Lifecycle (Enterprise Flow)

Step 1:
Server built → Local Admin account created

Step 2:
CyberArk Onboarding:

Account added to Safe

CPM starts managing password

Step 3:
User requests access:

Access approved via PVWA

Step 4:
PSM launches session:

No password revealed

Step 5:
Session ends:

CPM rotates password

Security Result:
Password never stays static.


# CyberArk Services Interaction – Internal Deep Flow

## Objective

To explain how CyberArk internal services work together to secure local administrator accounts and privileged credentials.

---

## Core Services Communication Flow

Vault:
- Central credential store
- Secure encrypted storage

CPM:
- Connects to target servers
- Changes local admin passwords
- Verifies password health

PSM:
- Launches RDP/SSH sessions
- Hides credentials from users
- Records admin activity

PVWA:
- Access request portal
- Authorization layer

---

## Local Administrator Protection Flow

1. Local admin account exists on server
2. CyberArk admin onboards account into Safe
3. Vault stores credentials
4. CPM rotates password automatically
5. User requests access via PVWA
6. PSM connects to server
7. Session recorded
8. CPM rotates password again after use

---

## Security Value

Prevents:

- Password sharing
- Credential theft
- Insider misuse
- Privilege escalation


## Mermaid Architecture Flow Diagram

```mermaid
flowchart LR
    User --> PVWA
    PVWA --> Vault
    Vault --> CPM
    PVWA --> PSM
    PSM --> TargetServer
    CPM --> TargetServer


