# Threat Model (Mini)

## Assets
- Windows endpoint telemetry (Sysmon events)
- Wazuh alerts and indexed events
- Detection logic and validation artifacts

## Adversary goals
- Execute PowerShell payloads (encoded commands / download cradles)
- Establish persistence (local user creation, scheduled tasks)
- Exfiltrate or stage data via outbound connections

## Detection surfaces (lab)
- Sysmon EID 1: Process creation (PowerShell + suspicious flags)
- Sysmon EID 3: Network connections (outbound from PowerShell)
- Sysmon EID 11: File creation (dropped payload artifacts)

## Assumptions
- Lab uses sanitized values and mock screenshots for illustration.
- Real validation is provided via configs, queries, and reproducible steps.
