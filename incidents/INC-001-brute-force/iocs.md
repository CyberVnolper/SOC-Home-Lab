# INC-001 — Indicators of Compromise

## Network Indicators

| Indicator   | Value             | Source                   |
|:------------|:------------------|:-------------------------|
| Source Host | Kali Linux        | Laboratory investigation |
| Target Host | `SOC-Windows`     | Wazuh                    |
| Target IP   | `192.168.56.102`  | Laboratory configuration |
| Source IP   | Kali Linux IP     | Windows Event ID 4625    |

> The exact source IP should be taken directly from the collected Windows/Wazuh event.

## Account

| Indicator       | Value      |
|:----------------|:-----------|
| Target Username | `victorr`  |

## Event Indicators

| Indicator              | Value                             |
|:-----------------------|:----------------------------------|
| Windows Event ID       | `4625`                            |
| Individual Wazuh Rule  | `60122`                           |
| Correlation Wazuh Rule | `60204`                           |
| Correlation Description| `Multiple Windows Logon Failures` |
| Correlation Level      | `10`                              |

## IOC Assessment

The main indicators identified during the investigation are the repeated authentication-failure events, the targeted account and the originating laboratory system.

The activity was generated entirely inside the isolated SOC Home Lab.

No production indicators or external systems were involved.

Only information directly observed or validated during the laboratory investigation is included.

