# CyberArk Risk & Threat Model – Privileged Access Attack Defense

## Objective

This document maps real-world attack techniques targeting privileged accounts and explains how CyberArk mitigates these risks across the attack lifecycle.

Focus:
- Credential theft
- Privilege escalation
- Lateral movement
- Insider threats
- Persistence mechanisms

This reflects enterprise-level threat modeling thinking used by PAM architects and security SMEs.

---

# 1. Why Privileged Accounts Are the Primary Target

Attackers do NOT target normal users first.

They target:

- Local Administrator accounts
- Domain Admin accounts
- Service accounts
- Backup accounts
- Hardcoded credentials

Because once compromised:

→ Full environment control

---

# 2. Common Attack Path (Without CyberArk)

Typical attacker flow:

Step 1:
Compromise a low-privilege user

Step 2:
Dump credentials from memory

Step 3:
Find admin passwords stored locally

Step 4:
Perform privilege escalation

Step 5:
Move laterally across servers

Step 6:
Gain Domain Admin access

Step 7:
Establish persistence

---

# 3. Credential Theft Techniques

## Technique 1 – Credential Dumping

Tools used by attackers:

- Mimikatz
- LSASS memory extraction

Goal:
Extract cached admin credentials.

Risk:
If local admin password is static:
→ Entire server fleet compromised.

CyberArk Protection:

- Frequent password rotation
- Unique local admin passwords
- No credential reuse

---

## Technique 2 – Pass-the-Hash Attack

Attacker uses:

- NTLM hash instead of password

If admin passwords are same across systems:
→ Instant lateral movement.

CyberArk Defense:

- Different password per server
- Automatic rotation
- No password reuse

---

# 4. Privilege Escalation Risk Model

Attackers attempt to:

- Add users to admin groups
- Modify policies
- Abuse service accounts

CyberArk Defense:

- Session recording via PSM
- Admin activity monitoring
- Full audit trail

---

# 5. Lateral Movement Model

After first server compromise:

Attacker tries:

- RDP into other servers
- Use shared admin credentials

CyberArk Protection:

- No shared passwords
- Vaulted credentials
- Access only via PSM

---

# 6. Insider Threat Model

Threat source:

- Disgruntled employee
- Over-privileged admin
- Contractor misuse

Attack behavior:

- Access sensitive systems
- Create hidden accounts
- Disable logging

CyberArk Mitigation:

- Session monitoring
- Session recording
- Access approvals
- Full traceability

---

# 7. Persistence Techniques Attackers Use

Attackers try to stay hidden by:

- Creating backdoor admin accounts
- Disabling password rotation
- Modifying policies

CyberArk Defense:

- Continuous password rotation
- Policy enforcement
- Audit tracking

---

# 8. Tier-0 Compromise Impact Model

If Domain Admin is compromised:

Attackers can:

- Control AD
- Create unlimited accounts
- Deploy malware
- Disable security tools

CyberArk Protection Strategy:

- Vault Domain Admin accounts
- Restrict access via PSM
- Monitor every session

---

# 9. Attack Chain Break Model (How CyberArk Stops Attacks)

Attack Stage → CyberArk Control

Credential theft → Password rotation  
Lateral movement → Unique credentials  
Privilege escalation → Session recording  
Insider misuse → Access control  
Persistence → Policy enforcement  

---

# 10. Real Enterprise Risk Reduction

With CyberArk implemented:

- No hardcoded credentials
- No shared admin passwords
- Full visibility into admin activity
- Reduced attack surface

---

# 11. SME-Level Threat Thinking

CyberArk is not just a tool.

It is a control layer that protects:

- Identity
- Credentials
- Sessions
- Access pathways

---

# 12. Security Maturity Mapping

Level 1:
Manual password control

Level 2:
Vaulted credentials

Level 3:
Automated rotation

Level 4:
d
