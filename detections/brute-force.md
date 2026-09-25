# Detection — Brute Force / Multiple Windows Logon Failures

## Objective

Detect repeated failed authentication attempts against a Windows endpoint.

## Log Source

- Platform: Windows
- Log source: Windows Security Event Log
- Event ID: `4625`
- Endpoint: `SOC-Windows`
- Wazuh rule: `60204`
- Rule description: `Multiple Windows Logon Failures`
- Rule level: `10`

## Supporting Detection

The individual authentication failures were identified by Wazuh using:

- Rule: `60122`
- Description: `Logon Failure - Unknown user...`
- Rule level: `5`
- Windows Event ID: `4625`

## Detection Logic

The detection is based on repeated failed authentication attempts against a Windows endpoint.

Windows Event ID `4625` represents a failed logon attempt.

When multiple failed authentication events occur, Wazuh can correlate them and generate a higher-level alert indicating multiple Windows logon failures.

## Observed Activity

A controlled authentication attack simulation was performed from the Kali Linux system against the Windows endpoint inside the SOC Home Lab.

The activity generated multiple Windows Security Event ID `4625` events.

Wazuh detected the individual failures and correlated the activity using rule `60204`.

## Observed Results

During the investigation, the Wazuh dashboard showed:

- `5` matching events.
- `4` events associated with rule `60122`.
- `1` correlated event associated with rule `60204`.
- All observed events corresponded to Windows Event ID `4625`.
- Endpoint: `SOC-Windows`.
- Correlation rule level: `10`.

## Relevant Fields

The investigation focuses on:

- Timestamp
- Source IP address
- Target username
- Workstation name
- Logon type
- Authentication package
- Status
- Substatus
- Wazuh rule ID
- Wazuh alert level

## Target Account

The account observed in the collected event data was:

`victorr`

## MITRE ATT&CK

**T1110 — Brute Force**

## False Positives

Repeated failed authentication attempts may have legitimate causes, including:

- Incorrect credentials entered by a user.
- Applications using outdated credentials.
- Services configured with invalid credentials.
- Scheduled tasks using old credentials.

The surrounding context must therefore be investigated before determining whether the activity represents malicious behavior.

## Validation

The detection was validated in the SOC Home Lab by generating controlled failed authentication attempts from Kali Linux against the Windows endpoint.

The resulting Windows Event ID `4625` events were successfully collected by Wazuh and correlated into rule `60204`.

## Result

**Detection successfully validated.**
