# INC-004 — Analysis

## Objective
Analyze the suspicious process creation event detected on the Windows endpoint.

## Observed Process
The Sysmon event records:

* **Image:** `C:\SOC-LAB\svchost.exe`
* **CommandLine:** `"C:\SOC-LAB\svchost.exe"`
* **OriginalFileName:** `NOTEPAD.EXE`
* **Description:** Notepad

The process was launched by:
`C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

### Process Information
* **Process ID:** 8936
* **Parent Process ID:** 7812
* **Integrity Level:** High
* **User:** `DESKTOP-O678CDM\victorr`

### File Information
* **Company:** Microsoft Corporation
* **Product:** Microsoft® Windows® Operating System
* **File Version:** 10.0.19041.3636
* **SHA256:**  
  `BAEFAFD4C558E8EC66A5772B8AC8DC18D51789CCAF97BE5FC66CD63A71CAF75C`

## Wazuh Detection
Wazuh generated rule:
`61618 — Sysmon - Suspicious Process - svchost.exe` with level 12.

## Assessment
The event shows a process named `svchost.exe` executing from `C:\SOC-LAB` while its original file name is `NOTEPAD.EXE`.
The activity was intentionally generated as a controlled laboratory simulation.
The supplied event does not contain additional telemetry demonstrating process injection beyond the MITRE mapping assigned to Wazuh rule 61618.

## Result
The suspicious-process detection was successfully triggered and the relevant Sysmon process-creation telemetry was collected by Wazuh.

