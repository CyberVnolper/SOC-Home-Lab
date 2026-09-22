# SOC Home Lab

Laboratorio doméstico de ciberseguridad orientado a la monitorización, detección, investigación y respuesta ante incidentes de seguridad.

## Objetivo

Construir un entorno controlado que permita practicar tareas propias de un Security Operations Center (SOC):

* Monitorización de endpoints
* Recolección y análisis de logs
* Detección de actividad sospechosa
* Investigación de alertas
* Identificación de indicadores de compromiso (IOC)
* Correlación de eventos
* Mapeo con MITRE ATT&CK
* Respuesta y mitigación
* Documentación de incidentes

## Arquitectura

El laboratorio estará compuesto inicialmente por:

Kali Linux
    |
    | Ataques controlados
    v
Windows Endpoint + Sysmon
    |
    | Logs
    v
Wazuh
    |
    v
SOC Dashboard

## Tecnologías

* Wazuh
* Windows
* Sysmon
* Kali Linux
* Linux
* Wireshark
* Nmap
* PowerShell
* MITRE ATT&CK

## Casos de uso

### 01 - Brute Force

Detección e investigación de múltiples intentos de autenticación fallidos.

### 02 - Suspicious PowerShell

Detección e investigación de ejecución sospechosa de PowerShell.

### 03 - Network Scan

Detección de actividad de reconocimiento y escaneo de puertos.

### 04 - Suspicious User Creation

Detección de creación de cuentas de usuario potencialmente sospechosas.

### 05 - Suspicious Login

Investigación de patrones de autenticación anómalos.

### 06 - Suspicious Process Execution

Investigación de procesos y actividad potencialmente maliciosa.

## Incidentes

Cada incidente incluirá:

1. Descripción
2. Evidencias
3. Timeline
4. Indicadores de compromiso
5. Investigación
6. MITRE ATT&CK
7. Impacto
8. Respuesta
9. Mitigación
10. Conclusiones

## Estado

🟡 Laboratorio en construcción

## Disclaimer

Todo el contenido de este repositorio se realiza exclusivamente en entornos de laboratorio controlados y con fines educativos.
