# INC-004 — Analysis

## Objective
* **Propósito:** Analizar el evento de creación de un proceso sospechoso detectado en el endpoint de Windows.

## Observed Process
* **Ruta del Proceso:** `C:\SOC-LAB\svchost.exe`
* **Línea de Comandos:** `"C:\SOC-LAB\svchost.exe"`
* **Nombre Original del Archivo:** `NOTEPAD.EXE`
* **Descripción:** Notepad
* **Proceso Padre:** `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

### Detalle del Evento (Sysmon)
```text
Image:            C:\SOC-LAB\svchost.exe
CommandLine:      "C:\SOC-LAB\svchost.exe"
OriginalFileName: NOTEPAD.EXE
Description:      Notepad
ParentImage:      C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
```

## Process Information
* **Process ID:** 8936
* **Parent Process ID:** 7812
* **Integrity Level:** High
* **User:** DESKTOP-O678CDM\victorr

## File Information
* **Company:** Microsoft Corporation
* **Product:** Microsoft® Windows® Operating System
* **File Version:** 10.0.19041.3636
* **SHA256:** `BAEFAFD4C558E8EC66A5772B8AC8DC18D51789CCAF97BE5FC66CD63A71CAF75C`

## Wazuh Detection
* **Regla Generada:** `61618 — Sysmon - Suspicious Process - svchost.exe`
* **Nivel de Alerta:** `12`

## Assessment
* **Hallazgo Principal:** El evento muestra un proceso llamado `svchost.exe` ejecutándose desde `C:\SOC-LAB\`, mientras que el nombre original de su archivo es `NOTEPAD.EXE` (lo que indica un posible enmascaramiento o *masquerading*).
* **Contexto:** La actividad fue generada intencionadamente como una simulación controlada en entorno de laboratorio.
* **Limitaciones:** El evento suministrado no contiene telemetría adicional que demuestre una inyección de procesos, más allá del mapeo de MITRE ATT&CK asignado por defecto a la regla de Wazuh `61618`.

## Result
* **Conclusión:** La detección del proceso sospechoso se activó correctamente y Wazuh recolectó con éxito la telemetría de creación de procesos de Sysmon correspondiente.

