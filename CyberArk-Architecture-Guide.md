# CyberArk Architecture Guide

## Core Components

### Vault
- Secure storage for privileged credentials
- Encrypted password storage
- Central security component

### PVWA (Password Vault Web Access)
- Web interface for accessing CyberArk
- Used by admins and users
- Access control and account management

### CPM (Central Policy Manager)
- Automatically rotates passwords
- Enforces password policies
- Reduces password exposure risk

### PSM (Privileged Session Manager)
- Records admin sessions
- Monitors privileged activity
- Provides secure session access

### PSMP
- Secure proxy for SSH sessions
- Used for Unix/Linux environments

### PTA (Privileged Threat Analytics)
- Detects suspicious privileged behavior
- Identifies anomalies and threats

---

## Security Flow

User → PVWA → Request Access  
PVWA → Vault → Fetch Credentials  
Session via PSM → Activity Recorded  
CPM → Rotates Password Automatically
