# CyberArk Troubleshooting Scenarios – Deep Technical Guide

## Objective

This document covers real-world CyberArk troubleshooting cases with log-level analysis, root causes, and resolution steps.

Focus:
- CPM password rotation failures
- PSM session issues
- Vault connectivity problems
- Safe permission issues
- Local admin onboarding failures

---

# Scenario 1 – CPM Password Rotation Failure

## Symptoms

- Password not changing
- Account shows:
  "Verification Failed"
  "Change Failed"

## Where to Check Logs

CPM Server:

C:\Program Files (x86)\CyberArk\Password Manager\Logs\

Important logs:
- PMError.log
- PMTrace.log

## Sample Log Entries

Error:
Error: Execution error. Password change failed.
WinRC=1326 The user name or password is incorrect.


CPM is unable to change password for account Administrator on server SRV-01

## Possible Causes

- Wrong current password stored in Vault
- Target server unreachable
- Account locked
- Platform misconfiguration

## Troubleshooting Steps

1. Verify connectivity to target server
2. Check if admin account is locked
3. Perform password reconciliation
4. Validate platform settings

---

# Scenario 2 – CPM Verification Failed

## Symptoms

- Password changes but verification fails

## Log Indicator

Verification failed for account Administrator
Error Code: Access Denied

## Root Cause

- CPM changed password
- But unable to log in with new password

## Fix

- Ensure admin account has login rights
- Validate platform configuration
- Check local security policy on server

---

# Scenario 3 – PSM Session Launch Failure

## Symptoms

- RDP session not opening
- User sees:
  "Connection failed"
  "PSM could not initiate session"

## Where to Check Logs

PSM Server:

C:\Program Files (x86)\CyberArk\PSM\Logs\

Key files:
- PSMConsole.log
- PSMTrace.log

## Sample Log Entry

PSM Error: Failed to initiate RDP connection to target server SRV-02
Reason: Network path not found

## Possible Causes

- Firewall blocking RDP
- Target server unreachable
- PSM service down

## Fix

- Check RDP port 3389 access
- Restart PSM service
- Validate target machine connectivity

---

# Scenario 4 – Vault Connectivity Issue

## Symptoms

- PVWA cannot fetch credentials
- Login delays

## Log Location

Vault Server:

PrivateArk Server logs

## Sample Log Entry

Vault connection lost.
User authentication request timed out.

## Possible Causes

- Vault service stopped
- Network latency
- Firewall issue

## Fix

- Restart Vault service
- Check network connectivity
- Validate firewall rules

---

# Scenario 5 – Safe Permission Issue

## Symptoms

- User cannot see account in PVWA
- Access denied error

## Log Indicator

User does not have permission to access Safe.

## Root Cause

- Missing Safe membership
- Incorrect role assignment

## Fix

- Add user to Safe
- Assign proper permissions:
  - List Accounts
  - Use Accounts

---

# Scenario 6 – Local Administrator Onboarding Failure

## Symptoms

- Account added to CyberArk
- But CPM not rotating password

## Log Entry

Platform not found for account.
Password management disabled.

## Root Cause

- Wrong platform selected
- Missing policy

## Fix

- Assign correct platform
- Enable password management

---

# Scenario 7 – PSM Recording Not Available

## Symptoms

- Session launched
- But recording missing

## Log Indicator

 Session recording service not available.
 
## Possible Causes

- PSM recording service stopped
- Storage path full

## Fix

- Restart PSM recording service
- Check storage availability

---

# Services-Level Troubleshooting Approach

When issue occurs:

Step 1:
Check which component is involved:
- Vault
- CPM
- PSM
- PVWA

Step 2:
Go to component logs

Step 3:
Identify:
- Error string
- Failure code
- Target machine

Step 4:
Fix:
- Connectivity
- Permissions
- Platform configuration

---

# Interview Value

This troubleshooting knowledge demonstrates:

- CyberArk component understanding
- Log analysis capability
- Real-world admin support experience


