# Detection — Suspicious Process / svchost.exe

## Objective
Detect suspicious process creation involving `svchost.exe` executed outside its normal Windows system location.

## Log Source
*   **Platform:** Windows
*   **Log source:** `Microsoft-Windows-Sysmon/Operational`
*   **Event ID:** `1`
*   **Endpoint:** `SOC-Windows`
*   **Wazuh rule:** `61618`
*   **Rule description:** `Sysmon - Suspicious Process - svchost.exe`
*   **Rule level:** `12`

## Supporting Detection
The suspicious process was identified through Sysmon using:
*   **Event ID:** `1`
*   **Event type:** `Process Create`
*   **Provider:** `Microsoft-Windows-Sysmon`

## Detection Logic
The detection is based on Sysmon process creation telemetry.
The collected event shows a process named `svchost.exe` running from:

```text
C:\SOC-LAB\svchost.exe
```

Instead of the standard Windows system directory. Wazuh generated rule `61618` for this process activity.

## Observed Activity
A controlled laboratory simulation was performed on the Windows endpoint. 
The process executed was:

```text
C:\SOC-LAB\svchost.exe
```

The event identifies the original file name as:

```text
NOTEPAD.EXE
```

And the description as:

```text
Notepad
```

## Observed Results
During the investigation, Wazuh reported:
*   **Rule:** `61618`
*   **Rule level:** `12`
*   **Sysmon Event ID:** `1`
*   **Image:** `C:\SOC-LAB\svchost.exe`
*   **Original file name:** `NOTEPAD.EXE`
*   **Description:** `Notepad`
*   **Parent process:** `powershell.exe`
*   **User:** `DESKTOP-O678CDM\victorr`

## Relevant Fields
The investigation focuses on:
*   Image
*   Original file name
*   Command line
*   Parent image
*   Parent command line
*   Process ID
*   Parent process ID
*   User
*   Integrity level
*   SHA256 hash
*   Event ID
*   Wazuh rule ID
*   Timestamp

## MITRE ATT&CK
Wazuh rule `61618` is mapped to: **T1055 — Process Injection**

The supplied event itself records process creation and does not contain additional process-injection telemetry.

## False Positives
A process named `svchost.exe` outside the standard Windows directory may have legitimate explanations, including:
*   Administrative testing.
*   Software with non-standard installation paths.
*   Renamed legitimate executables.
*   Security testing activity.

The executable path, original file name, parent process, and hash should be reviewed before determining whether the activity is malicious.

## Validation
The detection was validated in the SOC Home Lab by executing the controlled process from:

```text
C:\SOC-LAB\svchost.exe
```

Sysmon generated Event ID `1`, which was collected by Wazuh and triggered rule `61618`.

## Result
**Detection successfully validated.**

