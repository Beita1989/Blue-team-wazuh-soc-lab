# MITRE ATT&CK Mapping (Portfolio)

This mapping documents how the lab detections relate to ATT&CK techniques. It is intentionally minimal and focused on what is validated with reproducible telemetry.

---

## D-001 — Suspicious PowerShell (EncodedCommand / download cradle)

| Detection ID | Technique | Name | Why it fits | Primary telemetry |
|---|---|---|---|---|
| D-001 | T1059.001 | PowerShell | Encoded PowerShell execution is a common malicious execution pattern | Sysmon EID 1 (Process Create) |
| D-001 | T1105 | Ingress Tool Transfer | Download cradles typically retrieve payloads from a remote host | Sysmon EID 3 (Network Connect) |
| D-001 | (supporting) | File drop | Dropped scripts/binaries often follow execution + network activity | Sysmon EID 11 (File Create) |

**Evidence links**
- Detection doc: `/docs/03-detections/detections.md`
- Validation queries: `/docs/05-evidence/queries.md`
- Runbook: `/docs/incident-runbooks/IR-001-suspicious-powershell.md`
- Log samples: `/docs/05-evidence/log-samples/`
