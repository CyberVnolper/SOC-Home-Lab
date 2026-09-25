# INC-002 — Suspicious PowerShell

## Incident Summary

A controlled PowerShell activity was executed locally on the Windows endpoint `SOC-Windows` as part of the SOC Home Lab simulation.

The activity executed `New-ItemProperty` against the Windows Registry and generated Windows PowerShell Operational Event ID `4104`.

Wazuh collected the event and detected the activity using rule `91843`, identifying a possible registry modification performed through PowerShell.

The activity was intentional and limited to the isolated laboratory environment.

## Affected Asset

| Field                | Value                                    |
|:---------------------|:-----------------------------------------|
| **Host**             | `SOC-Windows`                            |
| **IP**               | `192.168.56.102`                         |
| **Operating System** | Windows 10 Pro                           |
| **Log Source**       | Microsoft-Windows-PowerShell/Operational |
| **Windows Event ID** | `4104`                                   |
| **Wazuh Rule**       | `91843`                                  |

## Detection

Wazuh detected the PowerShell script block through rule `91843`:

> Powershell executed "New-ItemProperty -Path". Possible addition of new item to registry

| Field                    | Value                     |
|:-------------------------|:--------------------------|
| **Rule ID**              | `91843`                   |
| **Level**                | `3`                       |
| **Windows Event ID**     | `4104`                    |
| **MITRE ATT&CK**         | `T1059.001 — PowerShell`  |
| **Additional Technique** | `T1112 — Modify Registry` |

## Source

The activity was executed locally on the monitored Windows endpoint.

No external source system was involved in this simulation.

## Status

**Investigated — Laboratory Simulation**

## Investigation

The detailed investigation is documented in:

* `timeline.md`
* `iocs.md`
* `analysis.md`

## Evidence

All evidence is stored under:

```text
evidence/
├── events/
│   └── event-91843.json
├── logs/
│   └── wazuh-91843.txt
└── screenshots/
    ├── 01-wazuh-91843-alert.png
    └── 02-powershell-new-itemproperty.png
```

### Event Data

*   [`event-91843.json`](evidence/events/event-91843.json)

### Log Data

*   [`wazuh-91843.txt`](evidence/logs/wazuh-91843.txt)

### Screenshots

#### 01 - Wazuh Alert
![Wazuh Alert](../screenshots/01-wazuh-91843-alert.png)

#### 02 - PowerShell New-ItemProperty
![PowerShell Command](../screenshots/02-powershell-new-itemproperty.png)

## Final Report

The complete incident report is available at:

[`incident-report-INC-002.md`](../../reports/incident-report-INC-002.md)

