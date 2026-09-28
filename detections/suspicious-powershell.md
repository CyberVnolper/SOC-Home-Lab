# Detection — Suspicious PowerShell

## Objective

Detect suspicious PowerShell activity involving the `New-ItemProperty` cmdlet and a Windows Registry path.

## Log Source

* **Platform:** Windows
* **Log source:** `Microsoft-Windows-PowerShell/Operational`
* **Event ID:** `4104`
* **Endpoint:** `SOC-Windows`
* **Wazuh rule:** `91843`
* **Rule description:** `Powershell executed "New-ItemProperty -Path". Possible addition of new item to registry`
* **Rule level:** `3`

## Detection Logic

The detection is based on PowerShell Script Block Logging.

Windows Event ID `4104` records the content of executed PowerShell script blocks.

Wazuh rule `91843` detects PowerShell activity containing `New-ItemProperty -Path` and identifies it as possible registry modification activity.

## Observed Activity

A controlled PowerShell command was executed locally on the Windows endpoint inside the SOC Home Lab.

The command was:

```powershell
New-ItemProperty -Path "HKLM:\Software\Microsoft\ADs" -Name "NoofAlerts" -Value 2 -PropertyType DWord
```

The command completed successfully and created the `NoofAlerts` registry value with a value of `2`.

## Observed Results

During the investigation, Wazuh generated:

* **Rule:** `91843`
* **Rule level:** `3`
* **Windows Event ID:** `4104`
* **Endpoint:** `SOC-Windows`
* **Script Block ID:** `f72b33ce-2f30-43d6-ac4c-30d4bbf8ed82`
* **Registry data:**
    * **Path:** `HKLM:\Software\Microsoft\ADs`
    * **Name:** `NoofAlerts`
    * **Type:** `DWord`
    * **Value:** `2`

## Relevant Fields

The investigation focuses on:

* Timestamp
* Script Block Text
* Script Block ID
* Windows Event ID
* Registry path
* Registry value name
* Registry value type
* Wazuh rule ID
* Wazuh alert level
* Endpoint information

## Registry Modification

The observed registry modification was:

```text
Path:  HKLM:\Software\Microsoft\ADs
Name:  NoofAlerts
Type:  DWord
Value: 2
```

## MITRE ATT&CK

* **T1059.001** — PowerShell
* **T1112** — Modify Registry

## False Positives

PowerShell-based registry modifications may have legitimate administrative or software-management purposes.

The surrounding context, executed command, affected registry location and originating process should therefore be reviewed before determining whether the activity is malicious.

## Validation

The detection was validated in the SOC Home Lab by executing a controlled `New-ItemProperty` PowerShell command on the Windows endpoint.

Windows generated Event ID `4104`, which was collected by the Wazuh Agent.

Wazuh subsequently generated rule `91843` for the observed PowerShell activity.

## Result

**Detection successfully validated.**

