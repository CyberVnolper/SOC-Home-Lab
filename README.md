# SOC Home Lab

Laboratorio práctico de ciberseguridad orientado a la monitorización, detección, investigación y respuesta ante incidentes de seguridad.

## Objetivo

Desarrollar y documentar investigaciones de seguridad en un entorno controlado, siguiendo un flujo de trabajo similar al de un equipo SOC.

El proyecto busca demostrar de forma práctica:

- Análisis de eventos de seguridad.
- Detección de actividad sospechosa.
- Investigación de incidentes.
- Identificación de indicadores de compromiso (IOC).
- Análisis de evidencias.
- Mapeo con MITRE ATT&CK.
- Respuesta y mitigación.
- Documentación técnica.

## Herramientas

- Wazuh
- Sysmon
- Windows
- Ubuntu Server
- Kali Linux
- Nmap
- Wireshark
- PowerShell
- Bash
- Python
- MITRE ATT&CK

## Incidentes

### INC-001 — Brute Force

Investigación de múltiples intentos de autenticación fallidos.

[Ver incidente](incidents/INC-001-brute-force/README.md)

### INC-002 — Suspicious PowerShell

Investigación de actividad sospechosa relacionada con PowerShell.

[Ver incidente](incidents/INC-002-suspicious-powershell/README.md)

### INC-003 — Network Scan

Investigación de actividad de reconocimiento y escaneo de red.

[Ver incidente](incidents/INC-003-network-scan/README.md)

### INC-004 — Suspicious Process Execution

Investigación de una ejecución y cadena de procesos potencialmente sospechosa.

[Ver incidente](incidents/INC-004-suspicious-process/README.md)

## Documentación

La documentación del proyecto se organiza en:

- `architecture/` — documentación de la infraestructura.
- `detections/` — documentación de las detecciones.
- `incidents/` — investigaciones completas de los incidentes.
- `reports/` — informes finales.
- `screenshots/` — evidencias visuales.
- `scripts/` — scripts utilizados durante el laboratorio.

## Estado

En desarrollo.

## Disclaimer

Todo el contenido de este repositorio se realiza exclusivamente en entornos de laboratorio controlados y con fines educativos.

Las pruebas de seguridad se realizan únicamente sobre sistemas pertenecientes al laboratorio y bajo condiciones controladas.
