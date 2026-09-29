# INC-004 — Indicators and Observables

## Process Observables
* **Process Name:** `svchost.exe`
* **Image Path:** `C:\SOC-LAB\svchost.exe`
* **Original File Name:** `NOTEPAD.EXE`
* **Description:** `Notepad`
* **Command Line:** `"C:\SOC-LAB\svchost.exe"`
* **Process ID:** `8936`
* **Parent Process ID:** `7812`
* **Parent Image:** `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

### Detalle de Ejecución

| Atributo | Valor |
| :--- | :--- |
| **Process Name** | `svchost.exe` |
| **Image Path** | `C:\SOC-LAB\svchost.exe` |
| **Original File Name** | `NOTEPAD.EXE` |
| **Command Line** | `"C:\SOC-LAB\svchost.exe"` |
| **Parent Image** | `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` |

## User Context
* **Account:** `DESKTOP-O678CDM\victorr`
* **Privileges:** Alta integridad (conforme al análisis previo)

## File Hash
* **SHA256:** `BAEFAFD4C558E8EC66A5772B8AC8DC18D51789CCAF97BE5FC66CD63A71CAF75C`

## Host Information
* **Hostname:** `DESKTOP-O678CDM`
* **Wazuh Agent:** `SOC-Windows`
* **Agent ID:** `001`
* **Agent IP:** `192.168.56.102`

## Event Metadata
* **Sysmon Event ID:** `1` (Process creation)
* **Event Record ID:** `22329`
* **Channel:** `Microsoft-Windows-Sysmon/Operational`
* **Wazuh Rule:** `61618`
* **Wazuh Alert Level:** `12`

## Timestamp
* **Event Time (UTC):** `2026-09-29T14:16:00.248Z`

