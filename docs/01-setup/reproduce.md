# Reproduce the lab (minimal)

This guide explains how to reproduce the telemetry and validate D-001 in a small lab stack:
- 1x Wazuh Manager (Linux)
- 1x Windows endpoint (Sysmon + Wazuh Agent)

> Notes:
> - IPs/hostnames are lab-sanitized. Replace with your environment values.
> - Illustrative screenshots (if present) are mock. Real validation is via logs, configs, and reproducible steps.

## Prerequisites
- Wazuh Manager reachable from the Windows endpoint
- Sysmon installed on Windows
- Wazuh Agent installed and enrolled on Windows

## 1) Configure Sysmon
- Use the Sysmon config: `/configs/sysmon/sysmon-config.xml`
- Install/verify Sysmon (example scripts):
  - `/scripts/powershell/install-sysmon.ps1`
  - `/scripts/powershell/enable-logging.ps1`

Expected telemetry (Sysmon):
- EID 1 (Process Create)
- EID 3 (Network Connect)
- EID 11 (File Create)

## 2) Generate the test activity (D-001)
Run the generator on the Windows endpoint:
- `/scripts/powershell/generate-attack-events.ps1`

Expected artifacts:
- PowerShell execution with `-enc` / `EncodedCommand` (EID 1)
- Outbound network connection from powershell.exe (EID 3)
- Dropped file/script in temp/download-like location (EID 11)

## 3) Validate in Wazuh (queries + evidence)
- Validation queries: `/docs/05-evidence/queries.md`
- Evidence pack index: `/docs/05-evidence/evidence-index.md`
- Sanitized samples:
  - `/docs/05-evidence/log-samples/sysmon-eid1-process-create.sample.json`
  - `/docs/05-evidence/log-samples/sysmon-eid3-network-connect.sample.json`
  - `/docs/05-evidence/log-samples/sysmon-eid11-file-create.sample.json`

## 4) Where to look next
- Detection catalog: `/docs/03-detections/detections.md`
- MITRE mapping: `/docs/04-mitre/mitre-mapping.md`
- Runbooks: `/docs/incident-runbooks/`
