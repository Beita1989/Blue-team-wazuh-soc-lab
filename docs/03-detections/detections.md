# Detections

This lab contains a minimal set of SOC detections validated with Sysmon telemetry and Wazuh.

## Included detections

### D-001 Suspicious PowerShell (EncodedCommand / download cradle)
**Goal:** Detect suspicious PowerShell execution patterns often used in initial execution and payload retrieval.

**Signals**
- Sysmon EID 1: `powershell.exe` with `-enc` / `EncodedCommand`
- Sysmon EID 3: outbound network connection from PowerShell
- Sysmon EID 11: file creation following download or script execution

**Validation**
- Runbook: `/docs/incident-runbooks/IR-001-suspicious-powershell.md`
- Generator: `/scripts/powershell/generate-attack-events.ps1`
- Evidence: `/docs/05-evidence/evidence-index.md`
- Queries: `/docs/05-evidence/queries.md`

**MITRE mapping:** `/docs/04-mitre/mitre-mapping.md`
