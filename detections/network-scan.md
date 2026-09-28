# Detection — Network Scan

## Objective
Detect and investigate network scanning activity against a Windows endpoint.

## Log Source
* **Platform:** Windows
* **Log source:** Windows Security Event Log
* **Event ID:** `5157`
* **Endpoint:** `SOC-Windows`
* **Wazuh rule:** `60104`
* **Rule description:** `Windows audit failure event`
* **Rule level:** `5`

## Detection Logic
Windows Event ID `5157` records a network connection blocked by Windows Filtering Platform.

The event contains network information such as:
* Source address
* Source port
* Destination address
* Destination port
* Protocol

> **Note:** Repeated blocked connections can provide useful telemetry when investigating possible network scanning activity.

## Observed Activity
A controlled **Nmap scan** was performed from Kali Linux against the Windows endpoint `192.168.56.102`. The scan targeted TCP ports `1-1000`.

## Observed Results
The scan returned the following output:

```text
All 1000 scanned ports on 192.168.56.102 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
```

A collected Windows Event ID `5157` processed by Wazuh records a blocked TCP connection from `192.168.56.104` to `192.168.56.102` on destination port `445`.

## Relevant Fields
* Source address
* Source port
* Destination address
* Destination port
* Protocol
* Event ID
* Wazuh rule ID
* Timestamp

## MITRE ATT&CK
* **T1046** — Network Service Scanning

## False Positives
Blocked network connections may have legitimate causes such as:
* Normal network communication.
* Administrative activity.
* Network discovery.
* Applications attempting to access unavailable services.

> ⚠️ The source, destination, ports, and surrounding activity should therefore be reviewed before classifying the activity.

## Validation
The detection scenario was validated in the **SOC Home Lab** by performing a TCP SYN scan from Kali Linux against the Windows endpoint with the Windows Firewall active.

## Result
* **Detection scenario successfully validated.**

