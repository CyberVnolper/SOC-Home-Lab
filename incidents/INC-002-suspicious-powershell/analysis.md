# INC-002 — Analysis

## Detection Chain

The observed activity followed this detection chain:

```text
PowerShell Execution
        ↓
Script Block Logging
        ↓
Windows Event ID 4104
        ↓
Wazuh Agent
        ↓
Rule 91843
        ↓
SOC Investigation
```

## Observed Activity

The PowerShell command used the `New-ItemProperty` cmdlet to create a registry value named `NoofAlerts` under:

```text
HKLM:\Software\Microsoft\ADs
```

The operation completed successfully and returned the created registry property with value `2`.

## Wazuh Detection

Wazuh received the PowerShell Script Block Logging event and generated rule `91843`.

The rule description was:

```text
Powershell executed "New-ItemProperty -Path".
Possible addition of new item to registry
```

The rule classified the activity under:

* `T1059.001 — PowerShell`
* `T1112 — Modify Registry`

## Assessment

The activity is consistent with a PowerShell-based registry modification.

The event itself does not establish malicious intent. In this case, the activity was intentionally generated as a controlled laboratory simulation to validate detection and investigation capabilities.

The event was successfully collected by Wazuh, correlated with the appropriate detection rule and preserved as investigation evidence.

No additional suspicious activity associated with the test was observed.
