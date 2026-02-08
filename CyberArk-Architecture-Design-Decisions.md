# CyberArk Architecture Design Decisions – SME / Architect Level

## Purpose

This document explains real-world architecture decisions taken when designing, scaling, and securing a CyberArk PAM environment in enterprise deployments.

Focus:
- HA & DR strategy
- Vault placement
- PSM sizing
- CPM scaling
- Tier-0 protection model
- Network segmentation
- Privileged access isolation

---

# 1. Vault Placement Strategy (Most Critical Decision)

## Why Vault Is Tier-0

The Vault stores:

- Domain Admin passwords
- Local Administrator credentials
- Service account secrets
- Root account credentials

If Vault is compromised → Entire infrastructure is compromised.

## SME Design Principles

- Place Vault in most secure network zone
- Isolate from production network
- Restrict inbound access strictly

Access allowed only from:

- PVWA
- CPM
- PSM

---

# 2. High Availability (HA) Design

Enterprise environments cannot tolerate Vault downtime.

## HA Strategy

Deploy:

- Primary Vault
- DR Vault (Disaster Recovery)

Replication:

- Real-time replication
- Secure encrypted sync

## Design Decision Points

When to implement DR?

- Large enterprise
- Tier-0 dependency
- 24/7 operations

---

# 3. CPM Scaling Strategy

CPM handles:

- Password rotation
- Verification
- Reconciliation

## Scaling Challenge

Large environments may have:

- 20,000+ privileged accounts
- Frequent rotation cycles

## SME Decision

Deploy multiple CPMs when:

- Rotation queue delay increases
- Platform diversity grows
- Network segmentation requires distributed CPMs

---

# 4. PSM Sizing & Placement Strategy

PSM is resource-heavy because it:

- Proxies RDP sessions
- Records video
- Logs keystrokes

## SME Design Approach

Deploy multiple PSMs when:

- High concurrent session load
- Multiple data centers
- Remote region access required

---

# 5. Tier-0 Privileged Access Isolation Model

SME-level concept:

Protect accounts in layers:

Tier-0:
- Domain Admin
- Enterprise Admin
- Vault Admin

Tier-1:
- Server Admin

Tier-2:
- Application Admin

## Design Principle

Tier-0 accounts:

- Accessed only via PSM
- No direct RDP allowed
- Heavily monitored

---

# 6. Network Segmentation Strategy

CyberArk components should NOT be flat deployed.

## Secure Zoning Example

Zone 1:
Vault network (Highly restricted)

Zone 2:
PSM / CPM zone

Zone 3:
PVWA access layer

Zone 4:
Target servers

This limits lateral movement risk.

---

# 7. Session Isolation Strategy

PSM acts as:

- Security gateway
- Credential shield
- Activity recorder

Design decisions:

- Enforce PSM-only access for admins
- Disable direct login using passwords

---

# 8. Credential Exposure Risk Reduction Model

SME focus:

Passwords must never be:

- Known to users
- Stored locally
- Shared manually

CyberArk ensures:

- Automatic rotation
- Vaulted secrets
- Controlled retrieval

---

# 9. Performance vs Security Tradeoffs

Architect decisions balance:

Security vs Usability

Examples:

- Short rotation cycles = Higher security
- But increases CPM load

- More PSM recordings = Better visibility
- But higher storage usage

---

# 10. Enterprise Maturity Model

Level 1:
Manual admin password control

Level 2:
CyberArk vaulting implemented

Level 3:
Session monitoring enforced

Level 4:
Full SIEM integration

Level 5:
Behavior analytics + Zero Trust PAM

---

# 11. Real-World Attack Mapping

CyberArk architecture protects against:

- Credential dumping
- Pass-the-Hash attacks
- Lateral movement
- Insider admin misuse

---

# 12. SME-Level Responsibilities in Architecture Planning

CyberArk SME participates in:

- Capacity planning
- Platform onboarding strategy
- Security policy design
- DR testing
- Risk assessments
- PAM maturity roadmap
