# IR-001 — Suspicious PowerShell

## Scope
Detect and triage suspicious PowerShell execution such as:
- `-enc` / `EncodedCommand`
- Download cradle patterns (IEX, DownloadString, WebClient)

## Primary signals
- Sysmon Event ID 1 (Process creation)
- (Optional) PowerShell Script Block logging (Event ID 4104)

## Triage steps
1. Identify the host and user
   - hostname, username, logon session if available
2. Review the command line
   - look for `-enc`, `EncodedCommand`, `IEX`, `DownloadString`, `FromBase64String`
3. Check parent process
   - common parents: explorer.exe, winword.exe, outlook.exe, wscript.exe
4. Correlate with network activity
   - Sysmon Event ID 3 around the same timestamp
   - destination IP/port + domain (if resolved)
5. Determine intent
   - admin automation vs suspicious execution
   - check if it happened during maintenance window

## Containment (lab-safe)
- Isolate the endpoint VM (disable NIC or quarantine VLAN)
- Stop suspicious process if still running

## Eradication
- Remove scheduled tasks / startup items created around the event
- Check for new services / new local users

## Recovery
- Re-enable network
- Continue monitoring for repeated attempts

## Evidence to capture
- Event IDs: Sysmon 1, Sysmon 3, Security 4624 (if available)
- Command line + hashes (if Wazuh provides)
- Timeline (first seen / last seen)

## MITRE ATT&CK
- T1059.001 PowerShell
- T1105 Ingress Tool Transfer (if downloading)
