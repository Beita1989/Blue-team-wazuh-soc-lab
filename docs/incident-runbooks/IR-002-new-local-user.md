# IR-002 — New Local User Created (Windows)

## Goal
Investigate and respond to creation of a new local user on a Windows endpoint.

## Data sources
- Windows Security logs (Event ID 4720)
- Sysmon (optional correlation): Process Create (EID 1), Registry (EID 13/14)
- Wazuh alerts (rule mapping for user creation events)

## Triage checklist
- Identify host, user creating the account, timestamp, and new username
- Was the action approved? (expected admin change vs suspicious)
- Is the new user added to privileged groups?

## Key evidence
- Security Event ID **4720** (user account created)
- Security Event ID **4728/4732** (added to privileged groups, if applicable)
- Related logon events: **4624** (successful logon), **4672** (special privileges)

## Scoping
- Search for additional user creations in the last 24h
- Check for new local admins
- Check for remote access indicators (RDP, VPN, unusual source IP)

## Containment
- Disable the new account (if unapproved)
- Reset affected admin passwords
- Block suspicious source IPs (if identified)

## Eradication & recovery
- Remove persistence (scheduled tasks, services, startup entries)
- Patch and validate endpoint hardening
- Confirm no further account creations occur

## MITRE ATT&CK (suggested)
- T1136.001 Create Account: Local Account
- T1098 Account Manipulation
