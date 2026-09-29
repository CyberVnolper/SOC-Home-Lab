# INC-004 — Timeline

## Chronological Events
* **14:16:00.248 UTC:** Generación del evento de creación de proceso para `C:\SOC-LAB\svchost.exe` (Sysmon).
* **14:16:00.251 UTC:** Registro definitivo del evento con ID `1` en el log operativo de Sysmon (Windows).
* **14:16:01.779 UTC:** Disparo de la alerta de proceso sospechoso bajo la regla `61618` (Wazuh).

### Tabla de Tiempos

| Time (UTC) | Source | Event |
| :--- | :--- | :--- |
| `2026-09-29 14:16:00.248` | Sysmon | Process creation event generated for `C:\SOC-LAB\svchost.exe`. |
| `2026-09-29 14:16:00.251` | Windows | Sysmon Event ID `1` recorded the process creation. |
| `2026-09-29 14:16:01.779` | Wazuh | Rule `61618` generated the suspicious-process alert. |

## Process Chain
* **Origen:** `powershell.exe` (Proceso Padre)
* **Acción:** Ejecución de binario renombrado (`svchost.exe` actuando como `NOTEPAD.EXE`)
* **Auditoría:** Registro del evento por Sysmon (Event ID 1)
* **Monitoreo:** Generación de alerta crítica en el SIEM (Wazuh Rule 61618)

```text
PowerShell (PID 7812)
    ↓
C:\SOC-LAB\svchost.exe (PID 8936)
    ↓
Sysmon Event ID 1 (Log local)
    ↓
Wazuh Rule 61618 (Alerta SIEM)
```

## Key Event
* **Binario Ejecutado:** `C:\SOC-LAB\svchost.exe`
* **Nombre Real:** `NOTEPAD.EXE` (Masquerading)
* **Iniciador:** `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

