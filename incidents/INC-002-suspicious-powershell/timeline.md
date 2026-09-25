# INC-002 — Timeline

| Time (UTC)                     | Source             | Event                                                                                         |
|:-------------------------------|:-------------------|:----------------------------------------------------------------------------------------------|
| `2026-09-25T12:14:55.2037836Z` | Windows PowerShell | PowerShell generated Event ID `4104` containing the executed `New-ItemProperty` script block. |
| `2026-09-25T12:14:55.2037836Z` | Windows PowerShell | Script block identified by ID `f72b33ce-2f30-43d6-ac4c-30d4bbf8ed82`.                         |
| `2026-09-25T12:15:13.742Z`     | Wazuh              | Alert `91843` generated for the PowerShell registry modification activity.                    |
| `2026-09-25T12:15:13.742Z`     | Wazuh              | Rule `91843` classified the activity as a possible addition of a new registry item.           |

## Activity

The executed PowerShell command was:

```powershell
New-ItemProperty -Path "HKLM:\Software\Microsoft\ADs" -Name "NoofAlerts" -Value 2 -PropertyType DWord
```

The command completed successfully and returned:

```text
NoofAlerts   : 2
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\ADs
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft
PSChildName  : ADs
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core
```

The activity was intentionally generated as part of the laboratory simulation.

No additional suspicious activity related to this test was observed.

