# INC-003 — Network Scan

## Incident Summary
A controlled network scanning exercise was performed from Kali Linux against the Windows endpoint `SOC-Windows` inside the isolated **SOC Home Lab**.

* **Target IP:** `192.168.56.102`
* **Target Ports:** TCP `1-1000`

> Windows generated **Event ID 5157** records for blocked network connections, which were collected and processed by Wazuh.

## Affected Asset

| Field | Value |
| :--- | :--- |
| **Host** | `SOC-Windows` |
| **IP** | `192.168.56.102` |
| **Operating System** | Windows 10 Pro |
| **Log Source** | Windows Security Event Log |
| **Event ID** | `5157` |
| **Wazuh Rule** | `60104` |

## Detection
Wazuh processed a Windows Event ID `5157` using rule `60104`:

```text
Windows audit failure event
```

## Source
* **Attacking Host:** Kali Linux
* **Source IP:** `192.168.56.104`

## Status
* 🟢 **Investigated — Laboratory Simulation**

## Investigation
Detailed investigation information is documented in:
* `timeline.md`
* `iocs.md`
* `analysis.md`

## Evidence
El árbol de directorios de las evidencias recolectadas:

```text
evidence/
├── events/
│   └── event-5157.json
├── logs/
│   └── wazuh-5157.txt
└── screenshots/
    ├── 01-nmap-network-scan.png
    ├── 02-windows-5157-network-scan.png
    └── 03-wazuh-network-scan-alert.png
```

## Final Report
* 📄 [`incident-report-INC-003.md`](../../reports/incident-report-INC-003.md)
