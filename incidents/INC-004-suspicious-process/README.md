# INC-004 — Suspicious Process

## Incident Summary
A controlled suspicious-process simulation was performed on the Windows endpoint `SOC-Windows` inside the isolated SOC Home Lab.
Sysmon recorded the creation of a process named `svchost.exe` from `C:\SOC-LAB\svchost.exe`.
Wazuh detected the activity using rule `61618 — Sysmon - Suspicious Process - svchost.exe`.

## Affected Asset

| Field | Value |
| :--- | :--- |
| **Host** | `SOC-Windows` |
| **IP** | `192.168.56.102` |
| **Operating System** | Windows 10 Pro |
| **Log Source** | Sysmon |
| **Event ID** | `1` |
| **Wazuh Rule** | `61618` |

## Detection
Wazuh generated a level `12` alert for:

```text
Sysmon - Suspicious Process - svchost.exe
```

## Source
The process was executed locally on the monitored Windows endpoint.

## Status
**Investigated — Laboratory Simulation**

## Investigation
Detailed investigation information is documented in:
*   `timeline.md`
*   `iocs.md`
*   `analysis.md`

## Evidence
```text
evidence/
├── events/
│   └── event-61618.json
├── logs/
│   └── wazuh-61618.txt
└── screenshots/
    ├── 01-suspicious-process.png
    └── 02-wazuh-suspicious-process.png
```

### Event Data
[`event-61618.json`](evidence/events/event-61618.json)

### Log Data
[`wazuh-61618.txt`](evidence/logs/wazuh-61618.txt)

## Final Report
[`incident-report-INC-004.md`](../../reports/incident-report-INC-004.md)

