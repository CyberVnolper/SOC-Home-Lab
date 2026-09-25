# INC-001 — Timeline

## Timeline

| Timestamp           | Event                                     | Source     | Target      | Rule    | Event ID |
|:--------------------|:------------------------------------------|:-----------|:------------|:-------:|---------:|
| 2026-09-24 17:04:23 | Authentication failure                    | Kali Linux | SOC-Windows | `60122` |   `4625` |
| 2026-09-24 17:04:23 | Authentication failure                    | Kali Linux | SOC-Windows | `60122` |   `4625` |
| 2026-09-24 17:04:23 | Multiple authentication failures detected | Kali Linux | SOC-Windows | `60204` |   `4625` |
| 2026-09-24 17:04:23 | Authentication failure                    | Kali Linux | SOC-Windows | `60122` |   `4625` |
| 2026-09-24 17:04:23 | Authentication failure                    | Kali Linux | SOC-Windows | `60122` |   `4625` |

## Timeline Analysis

The Wazuh dashboard showed five matching events associated with the simulated authentication activity.

Four events were individually detected using rule `60122`.

The repeated authentication failures were subsequently correlated by Wazuh using rule `60204 — Multiple Windows Logon Failures`.

The available dashboard evidence places the observed activity at approximately:

`2026-09-24 17:04:23`

The exact millisecond-level ordering of the individual events should be taken from the original event records when required.

## Detection Sequence

```text
Authentication failure
        ↓
Windows Event ID 4625
        ↓
Wazuh Agent
        ↓
Rule 60122
        ↓
Repeated authentication failures
        ↓
Rule 60204
        ↓
Multiple Windows Logon Failures
```

