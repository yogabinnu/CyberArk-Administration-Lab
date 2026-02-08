# CyberArk Administration – SME Level Operational Model

## Overview

This document reflects day-to-day responsibilities of a CyberArk Administrator at enterprise scale, including privileged identity lifecycle management, platform governance, operational stability, and risk reduction.

Scope includes:
- Local admin accounts
- Domain admin accounts
- Service accounts
- Application identities

---

# Privileged Account Lifecycle Management

## Phase 1 – Discovery & Onboarding

Tasks:

- Identify unmanaged privileged accounts:
  - Local Administrator
  - Service accounts
  - Hardcoded credentials

- Classify accounts:
  - Tier-0 (Domain Admin)
  - Tier-1 (Server Admin)
  - Tier-2 (Application Accounts)

- Onboard accounts into CyberArk Vault
- Map correct platform:
  - Windows Local
  - Windows Domain
  - Unix SSH
  - Database

Key Decisions:
- Password rotation frequency
- Reconciliation rules
- Access control model

---

## Phase 2 – Password Management Governance

SME-level responsibilities:

- Monitor CPM health daily
- Track password rotation success rate
- Investigate failed verifications
- Tune platform policies

Common log indicators:

PMError.log:
Password change failed. WinRC=5 Access Denied

PMTrace.log:

Reconcile task initiated for account Administrator

Operational Metrics:
- Rotation success %
- Accounts unmanaged
- Locked accounts

---

## Phase 3 – Access Control Governance

Design controls:

- Role-based Safe permissions
- Segregation of duties
- Time-bound access

SME-level focus:

- Prevent standing privileges
- Enforce least privilege
- Implement dual control

---

## Phase 4 – Session Security Oversight

PSM responsibilities:

- Monitor privileged session launches
- Audit high-risk admin behavior
- Review session recordings

Risk Indicators:

- Midnight admin logins
- Multiple target server access
- High-frequency session launches

---

## Phase 5 – Platform Stability Management

SME monitors:

- CPM service performance
- PSM session stability
- Vault health status

Key checks:

- Service uptime
- Rotation backlog
- Queue delays

---

## Phase 6 – Incident Support Role

CyberArk SME supports SOC in:

- Admin misuse investigations
- Credential theft response
- Privilege escalation tracing

Example investigation flow:

1. SOC detects suspicious admin login
2. CyberArk SME checks:
   - PSM recording
   - Vault access logs
   - CPM activity

---

## Phase 7 – Hardening Strategy Alignment

SME ensures:

- Default admin accounts disabled
- Named admin model enforced
- Credentials never shared
- Passwords rotated frequently

---

## Enterprise Value Delivered

CyberArk SME helps organization achieve:

- Zero standing privilege model
- Credential exposure elimination
- Insider threat visibility
- Privileged identity governance maturity
