# Evidence Pack (Portfolio)

This folder contains a minimal, reproducible evidence trail for the detections in this lab.

## What you will find here

- **evidence-index.md**: master index that links detections, MITRE mapping, queries, and log samples
- **queries.md**: Wazuh query/filters used to validate ingestion and detections (sanitized)
- **log-samples/**: sanitized Sysmon event samples (EID 1 / 3 / 11)

## How to use (reviewer flow)

1. Start at: `evidence-index.md`
2. Open the validation queries: `queries.md`
3. Open the corresponding Sysmon samples under: `log-samples/`
4. Cross-check with:
   - Detections: `/docs/03-detections/detections.md`
   - MITRE mapping: `/docs/04-mitre/mitre-mapping.md`
   - Runbook: `/docs/incident-runbooks/IR-001-suspicious-powershell.md`
