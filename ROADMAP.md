# Roadmap

## v1.1 (next)
- Add detection D-002: New Local User Created (persistence)
- Add validation artifacts:
  - Sysmon EID 1 process create (net user / PowerShell)
  - Sysmon EID 13 registry value set (if used)
  - Wazuh query filters + sanitized log samples
- Add runbook IR-002 alignment (containment + cleanup)

## v1.2
- Add D-003: Scheduled Task persistence (schtasks)
- Add evidence bundle for task creation events
- Add MITRE mapping expansion

## Nice-to-have
- Saved searches / dashboards checklist
- Sigma rule references (mapped to fields used)
- Small “lessons learned” section
