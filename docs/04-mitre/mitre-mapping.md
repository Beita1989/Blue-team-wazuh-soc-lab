# MITRE ATT&CK Mapping

This lab validates detections with Windows Sysmon telemetry and Wazuh alerting.
Evidence is provided via:
- Runbook: `/docs/incident-runbooks/IR-001-suspicious-powershell.md`
- Queries: `/docs/05-evidence/queries.md`
- Log samples: `/docs/05-evidence/log-samples/`

## Detection: Suspicious PowerShell (EncodedCommand / download cradle)

| ATT&CK Tactic | Technique | Why it fits | Evidence in this repo |
|---|---|---|---|
| Execution | T1059.001 (PowerShell) | PowerShell used to execute commands | Sysmon EID 1 sample: `/docs/05-evidence/log-samples/sysmon-eid1-process-create.sample.json` |
| Command and Control | T1105 (Ingress Tool Transfer) | Download cradle / remote payload retrieval pattern | Sysmon EID 3 sample: `/docs/05-evidence/log-samples/sysmon-eid3-network-connect.sample.json` |
| Defense Evasion | T1027 (Obfuscated/Encrypted File or Information) | EncodedCommand often used to hide content | Evidence index: `/docs/05-evidence/evidence-index.md` |

### Runbook + validation
- Runbook: `/docs/incident-runbooks/IR-001-suspicious-powershell.md`
- Validation queries: `/docs/05-evidence/queries.md`
- Evidence pack: `/docs/05-evidence/evidence-index.md`
