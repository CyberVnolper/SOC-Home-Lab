# Incident Report — INC-002

## Executive Summary

INC-002 documents a controlled PowerShell activity performed within the isolated SOC Home Lab.

A PowerShell command modified the Windows Registry by creating the `NoofAlerts` DWORD value under `HKLM:\Software\Microsoft\ADs`.

Windows Script Block Logging recorded the command as Event ID `4104`. Wazuh collected the event and generated rule `91843`, identifying the use of `New-ItemProperty -Path` as a possible registry modification performed through PowerShell.

The activity was intentionally generated for detection and incident-response validation.

## Incident Details

| Field | Value |
| :--- | :--- |
| **Incident ID** | `INC-002` |
| **Incident Type** | Suspicious PowerShell |
| **Affected Host** | `SOC-Windows` |
| **Target IP** | `192.168.56.102` |
| **Windows Event ID** | `4104` |
| **Wazuh Rule** | `91843` |
| **Alert Level** | `3` |
| **Status** | Investigated |
| **Environment** | SOC Home Lab |

## Detection

The activity was detected through Windows PowerShell Script Block Logging.

The resulting Event ID `4104` was collected by the Wazuh Agent and matched rule `91843`:

```text
Powershell executed "New-ItemProperty -Path".
Possible addition of new item to registry
```

The rule is associated with:

* `T1059.001 — PowerShell`
* `T1112 — Modify Registry`

## Technical Analysis

The executed command was:

```powershell
New-ItemProperty -Path "HKLM:\Software\Microsoft\ADs" -Name "NoofAlerts" -Value 2 -PropertyType DWord
```

The command completed successfully and created the following registry value:

| Field | Value |
| :--- | :--- |
| **Registry Path** | `HKLM:\Software\Microsoft\ADs` |
| **Value Name** | `NoofAlerts` |
| **Type** | `DWord` |
| **Value** | `2` |

The Windows event was generated at:

`2026-09-25T12:14:55.2037836Z`

Wazuh generated the corresponding alert at:

`2026-09-25T12:15:13.742Z`

The event was associated with script block ID:

`f72b33ce-2f30-43d6-ac4c-30d4bbf8ed82`

## Impact

The activity was restricted to the isolated SOC Home Lab.

No production systems were involved.

No additional suspicious activity associated with the simulation was observed.

## Response

The analyst:

1. Reviewed the Wazuh PowerShell alert.
2. Identified the affected Windows endpoint.
3. Examined the Windows Event ID `4104` data.
4. Identified the PowerShell command and registry path.
5. Verified that the command executed successfully.
6. Preserved the event and detection data.
7. Documented the investigation.

## Mitigation

For a production environment, appropriate controls for suspicious PowerShell and registry activity could include:

* Maintaining PowerShell Script Block Logging.
* Monitoring unusual PowerShell commands and execution patterns.
* Restricting unnecessary registry modifications.
* Applying least-privilege principles.
* Correlating PowerShell telemetry with process, endpoint and authentication events.
* Reviewing administrative PowerShell activity against expected operational tasks.

## Evidence

### Event Data

* [`event-91843.json`](../incidents/INC-002-suspicious-powershell/evidence/events/event-91843.json)

### Log Data

* [`wazuh-91843.txt`](../incidents/INC-002-suspicious-powershell/evidence/logs/wazuh-91843.txt)

### Screenshots

#### 01 - Wazuh Alert

![Wazuh Alert](../incidents/INC-002-suspicious-powershell/evidence/screenshots/01-wazuh-91843-alert.png)

#### 02 - PowerShell New-ItemProperty

![PowerShell Command](../incidents/INC-002-suspicious-powershell/evidence/screenshots/02-powershell-new-itemproperty.png)

## Conclusion

The SOC Home Lab successfully demonstrated the detection of PowerShell-based registry modification activity.

Windows generated Event ID `4104` through Script Block Logging, and Wazuh successfully collected the event and triggered rule `91843`.

The activity was intentional and performed solely for laboratory detection validation. No additional suspicious activity associated with the simulation was observed.

## Classification

**Laboratory Simulation — Investigated**

