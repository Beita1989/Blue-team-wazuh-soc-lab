## Evidence Pack (Reproducible)

This lab is validated by reproducible telemetry + detections.

### Host telemetry (Windows + Sysmon)
- Sysmon Event IDs expected:
  - 1 (Process Create)
  - 3 (Network Connection)
  - 11 (File Create)

### Detection validation
- Suspicious PowerShell (EncodedCommand / download cradle)
  - Runbook: `/docs/incident-runbooks/IR-001-suspicious-powershell.md`
  - Generator: `/scripts/powershell/generate-attack-events.ps1`
  - Expected artifacts:
    - PowerShell process with `-enc` / `EncodedCommand`
    - Outbound network connection (Sysmon EID 3)

### Screenshots (illustrative)
- `/docs/capturas/evidence-wazuh.png`
