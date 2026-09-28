# INC-003 — Analysis

## Objective

Analyze the network activity observed during a controlled scanning exercise.

## Scan Activity

The scan was performed from Kali Linux against:

```text
192.168.56.102
```

using:

```bash
nmap -Pn -sS -p 1-1000 192.168.56.102
```

The scan reported all 1000 TCP ports as filtered.

## Windows Telemetry

The preserved Windows Event ID `5157` contains:

```text
Source Address:      192.168.56.104
Source Port:         49125
Destination Address: 192.168.56.102
Destination Port:    445
Protocol:            6
Application:         System
```

Wazuh processed the event using rule `60104`.

## Assessment

The Nmap result demonstrates the controlled port-scanning activity.

The Windows event demonstrates a blocked TCP connection from the Kali laboratory address to the Windows endpoint.

The timestamps of the two pieces of evidence are different, so the preserved `5157` event is treated as supporting firewall telemetry rather than as a timestamp-matched record of the Nmap execution.

## MITRE ATT&CK

**T1046 — Network Service Scanning**

## Result

The laboratory demonstrated network scanning activity and collection of Windows firewall telemetry through Wazuh.

