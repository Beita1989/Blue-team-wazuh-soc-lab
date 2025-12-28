# MITRE ATT&CK Mapping (Portfolio)

This mapping documents how the lab detections relate to ATT&CK techniques. It is intentionally minimal and focused on what is validated with reproducible telemetry.

---

## D-001 — Suspicious PowerShell (EncodedCommand / download cradle)

| Detection ID | Technique | Name | Why it fits | Primary telemetry |
|---|---|---|---|---|
| D-001 | T1059.001 | PowerShell | Suspicious PowerShell with encoded command is a common execution pattern for scripted payloads | Sysmon EID 1 (Process Create) |
| D-001 | T1105 | Ingress Tool Transfer | Download cradles (e.g., `IEX` / web requests) often retrieve payloads from remote hosts | Sysmon EID 3 (Network Connect) |
| D-001 | (supporting) | File drop | Dropped scripts/binaries often follow execution + network activity | Sysmon EID 11 (File Create) |

**Evidence links**
- Detection doc: `/docs/03-detections/detections.md`
- Validation queries: `/docs/05-evidence/queries.md`
- Runbook: `/docs/incident-runbooks/IR-001-suspicious-powershell.md`
