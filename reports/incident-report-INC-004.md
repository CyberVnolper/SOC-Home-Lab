# Incident Report — INC-004

## Executive Summary

A controlled suspicious-process simulation was performed on the Windows endpoint `SOC-Windows` inside the isolated SOC Home Lab.

Sysmon recorded the creation of a process named `svchost.exe` from `C:\SOC-LAB\svchost.exe`.

Wazuh detected the activity using rule `61618 — Sysmon - Suspicious Process - svchost.exe` with alert level `12`.

## Incident Details

| Field | Value |
| :--- | :--- |
| **Incident ID** | `INC-004` |
| **Incident Type** | Suspicious Process |
| **Affected Host** | `SOC-Windows` |
| **Target IP** | `192.168.56.102` |
| **Windows Event ID** | `1` |
| **Wazuh Rule** | `61618` |
| **Alert Level** | `12` |
| **Status** | Investigated |
| **Environment** | SOC Home Lab |

## Detection

The activity was detected through Sysmon Event ID `1` and processed by Wazuh rule `61618`.

The rule description was:

```text
Sysmon - Suspicious Process - svchost.exe
```

## Technical Findings

The event identified:

```text
Image: C:\SOC-LAB\svchost.exe
OriginalFileName: NOTEPAD.EXE
Description: Notepad
ParentImage: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
Process ID: 8936
Parent Process ID: 7812
```

The SHA256 recorded by Sysmon was:

```text
BAEFAFD4C558E8EC66A5772B8AC8DC18D51789CCAF97BE5FC66CD63A71CAF75C
```

## Timeline

The Sysmon process creation occurred at:

`2026-09-29 14:16:00.248 UTC`

Wazuh generated the corresponding alert at:

`2026-09-29 14:16:01.779+0000`

## Analysis

The collected telemetry shows that a file whose original name is `NOTEPAD.EXE` was executed from `C:\SOC-LAB\svchost.exe`.

The parent process was Windows PowerShell.

The activity was intentionally generated as a controlled laboratory simulation to validate suspicious-process detection.

## Impact

The activity was restricted to the isolated SOC Home Lab.

No production systems were involved.

No additional suspicious activity associated with the simulation was identified.

## Response

The analyst:

1. Reviewed the Wazuh alert.
2. Identified the Sysmon process-creation event.
3. Examined the executable path and original file name.
4. Reviewed the parent process.
5. Recorded the file hash and process identifiers.
6. Preserved the event and log data.
7. Documented the investigation.

## Mitigation

For a production environment, appropriate defensive measures could include:

* Monitoring processes executed from unusual directories.
* Reviewing renamed system executables.
* Correlating process creation with parent-process activity.
* Reviewing file hashes against known-good software.
* Applying application-control and least-privilege policies.

## Evidence

### Event Data

[`event-61618.json`](../incidents/INC-004-suspicious-process/evidence/events/event-61618.json)

### Log Data

[`wazuh-61618.txt`](../incidents/INC-004-suspicious-process/evidence/logs/wazuh-61618.txt)

### Screenshots

#### 01 - Suspicious Process

![Suspicious Process](../incidents/INC-004-suspicious-process/evidence/screenshots/01-suspicious-process.png)

#### 02 - Wazuh Suspicious Process Alert

![Wazuh Suspicious Process Alert](../incidents/INC-004-suspicious-process/evidence/screenshots/02-wazuh-suspicious-process.png)

## Conclusion

The SOC Home Lab successfully demonstrated detection of a suspiciously named process executed from a non-standard directory.

Sysmon generated Event ID `1`, and Wazuh successfully detected the activity using rule `61618`.

The activity remained within the isolated laboratory environment and was intentionally generated for detection validation.

## Classification

**Laboratory Simulation — Investigated**

