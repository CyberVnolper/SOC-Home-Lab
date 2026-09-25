# INC-001 — Technical Analysis

## 1. Initial Detection

The incident was identified through repeated failed authentication attempts against the Windows endpoint `SOC-Windows`.

Windows generated Security Event ID `4625` for the failed authentication attempts.

The Wazuh Agent collected the events and forwarded them to the Wazuh platform.

## 2. Event Analysis

The Wazuh investigation identified five matching events.

Four events were associated with rule `60122`:

`Logon Failure - Unknown user...`

The repeated failures were subsequently correlated by Wazuh into:

`60204 — Multiple Windows Logon Failures`

with level `10`.

## 3. Source Analysis

The activity originated from the Kali Linux host within the isolated laboratory network.

The source system was therefore part of the controlled attack simulation.

## 4. Target Analysis

The affected endpoint was:

- Host: `SOC-Windows`
- IP: `192.168.56.102`
- Operating System: Windows 10 Pro
- Target Account: `victorr`
- Authentication Event: `4625`

## 5. Detection Correlation

The observed detection chain was:

```text
Kali Linux
     |
     v
Authentication Attempts
     |
     v
Windows Event ID 4625
     |
     v
Wazuh Agent
     |
     v
Rule 60122
     |
     v
Repeated Authentication Failures
     |
     v
Rule 60204
     |
     v
Multiple Windows Logon Failures
```

