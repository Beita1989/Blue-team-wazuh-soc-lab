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

## Log samples (sanitized)

- Sysmon EID 1 (Process Create): `/docs/05-evidence/log-samples/sysmon-eid1-process-create.sample.json`
- Sysmon EID 3 (Network Connect): `/docs/05-evidence/log-samples/sysmon-eid3-network-connect.sample.json`
- Sysmon EID 11 (File Create): `/docs/05-evidence/log-samples/sysmon-eid11-file-create.sample.json`


