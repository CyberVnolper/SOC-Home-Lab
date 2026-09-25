# INC-001 — Brute Force

## Incident Summary

A controlled series of failed authentication attempts was generated against the Windows endpoint `SOC-Windows`.

The activity was performed inside the isolated SOC Home Lab using Kali Linux as the source system and Windows as the monitored endpoint.

The authentication failures generated Windows Security Event ID `4625` events and were subsequently collected and analyzed by Wazuh.

Wazuh identified the individual failed logons and correlated the repeated activity using rule `60204 — Multiple Windows Logon Failures`.

## Affected Asset

| Field | Value |
| :--- | :--- |
| **Host** | `SOC-Windows` |
| **IP** | `192.168.56.102` |
| **Operating System** | Windows 10 Pro |
| **Log Source** | Windows Security Event Log |
| **Event ID** | `4625` |
| **Target Account** | `victorr` |

## Detection

The investigation identified five matching authentication-failure events.

Four events were associated with rule `60122` and one correlated event was associated with rule `60204`.

### Correlated Alert

| Field | Value |
| :--- | :--- |
| **Rule ID** | `60204` |
| **Description** | Multiple Windows Logon Failures |
| **Level** | `10` |

### Supporting Events

| Rule ID | Description | Level | Event ID | Events |
| :--- | :--- | :---: | :---: | :---: |
| `60122` | Logon Failure - Unknown user... | 5 | `4625` | 4 |
| `60204` | Multiple Windows Logon Failures | 10 | `4625` | 1 |

## Source

The authentication attempts originated from the Kali Linux host inside the isolated laboratory network.

## Status

**Investigated — Laboratory Simulation**

## Investigation

The incident investigation is documented in:

* `timeline.md`
* `iocs.md`
* `analysis.md`

## Evidence

Evidence collected during the investigation is stored under:

`evidence/`

## Final Report

The final incident report is available at:

`../../reports/incident-report-INC-001.md`

