# INC-001 — Brute Force

## Incident Summary

A controlled brute-force authentication simulation was performed inside the isolated SOC Home Lab against the Windows endpoint `SOC-Windows`.

The activity generated repeated Windows Security Event ID `4625` failures. Wazuh detected individual failures with rule `60122` and correlated the repeated activity with rule `60204 — Multiple Windows Logon Failures`.

The incident was investigated as a laboratory exercise and documented using the collected Wazuh event data, logs and screenshots.

## Affected Asset

| Field                | Value                      |
|:---------------------|:---------------------------|
| **Host**             | `SOC-Windows`              |
| **IP**               | `192.168.56.102`           |
| **Operating System** | Windows 10 Pro             |
| **Log Source**       | Windows Security Event Log |
| **Windows Event ID** | `4625`                     |
| **Target Account**   | `victorr`                  |

## Detection

The detection chain was:

```text
Failed Authentication
        ↓
Windows Event ID 4625
        ↓
Wazuh Agent
        ↓
Rule 60122
        ↓
Rule 60204
        ↓
SOC Investigation
```

The correlated Wazuh alert was:

| Field            | Value                           |
|:-----------------|:--------------------------------|
| **Rule ID**      | `60204`                         |
| **Description**  | Multiple Windows Logon Failures |
| **Level**        | `10`                            |
| **Frequency**    | `8`                             |
| **MITRE ATT&CK** | `T1110 — Brute Force`           |

## Source

The activity originated from the Kali Linux host used in the isolated laboratory network.

Observed source:

* IP: `192.168.56.104`
* Workstation: `SOCKALI`

## Status

**Investigated — Laboratory Simulation**

## Investigation

The detailed investigation and technical analysis are documented in:

* `timeline.md`
* `iocs.md`
* `analysis.md`

## Evidence

All collected evidence is stored under:

```text
evidence/
├── events/
│   ├── event-60122.json
│   └── event-60204.json
├── logs/
│   ├── wazuh-60122.txt
│   └── wazuh-60204.txt
└── screenshots/
    ├── 01-windows-4625.png
    ├── 02-wazuh-4625-alert.png
    └── 03-wazuh-4625-timeline.png
```

## Final Report

The complete incident report is available at: [incident-report-INC-001.md](../../reports/incident-report-INC-001.md)



