# INC-004 — Timeline

| Time (UTC) | Source | Event |
| :--- | :--- | :--- |
| `2026-09-29 14:16:00.248` | Sysmon | Process creation event generated for `C:\SOC-LAB\svchost.exe`. |
| `2026-09-29 14:16:00.251` | Windows | Sysmon Event ID `1` recorded the process creation. |
| `2026-09-29 14:16:01.779` | Wazuh | Rule `61618` generated the suspicious-process alert. |

## Process Chain

```text
PowerShell
    ↓
C:\SOC-LAB\svchost.exe
    ↓
Sysmon Event ID 1
    ↓
Wazuh Rule 61618
```

## Key Event

The process creation event recorded:

```yaml
Image: C:\SOC-LAB\svchost.exe
OriginalFileName: NOTEPAD.EXE
ParentImage: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
```


