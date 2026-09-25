```markdown
# INC-002 — Indicators and Observables

## Network Indicators

No external network indicators were identified for this incident.

The activity was executed locally on the monitored Windows endpoint.

## Host Observables

| Observable           | Value             |
| -------------------- | ----------------- |
| **Hostname**         | `DESKTOP-O678CDM` |
| **Wazuh Agent**      | `SOC-Windows`     |
| **Agent IP**         | `192.168.56.102`  |
| **Windows Event ID** | `4104`            |
| **Wazuh Rule**       | `91843`           |

## PowerShell Observables

| Observable          | Value                                                                                                   |
| ------------------- | ------------------------------------------------------------------------------------------------------- |
| **Command**         | `New-ItemProperty -Path "HKLM:\Software\Microsoft\ADs" -Name "NoofAlerts" -Value 2 -PropertyType DWord` |
| **Cmdlet**          | `New-ItemProperty`                                                                                      |
| **Registry Path**   | `HKLM:\Software\Microsoft\ADs`                                                                          |
| **Registry Value**  | `NoofAlerts`                                                                                            |
| **Value Type**      | `DWord`                                                                                                 |
| **Value**           | `2`                                                                                                     |
| **Script Block ID** | `f72b33ce-2f30-43d6-ac4c-30d4bbf8ed82`                                                                  |

## Event Metadata

| Field               | Value                                      |
| ------------------- | ------------------------------------------ |
| **Event Record ID** | `1017`                                     |
| **Channel**         | `Microsoft-Windows-PowerShell/Operational` |
| **Provider**        | `Microsoft-Windows-PowerShell`             |
| **Severity**        | `VERBOSE`                                  |
| **Process ID**      | `9732`                                     |

No persistent external indicator such as a public IP address, domain, URL or hash was identified in the collected evidence.
```
