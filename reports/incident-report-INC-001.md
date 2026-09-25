# Incident Report — INC-001

## Executive Summary

A controlled authentication attack simulation was performed against the Windows endpoint `SOC-Windows` inside the SOC Home Lab.

The activity generated multiple Windows Security Event ID `4625` events.

Wazuh identified the individual authentication failures and correlated the repeated activity using rule `60204 — Multiple Windows Logon Failures`, generating a level `10` alert.

The activity originated from the Kali Linux system within the isolated laboratory network.

No production systems were involved.

## Incident Details

| Field            | Value                                 |
|:-----------------|:--------------------------------------|
| Incident ID      | `INC-001`                             |
| Incident Type    | Brute Force / Repeated Failed Logons  |
| Affected Host    | `SOC-Windows`                         |
| Target IP        | `192.168.56.102`                      |
| Target Account   | `victorr`                             |
| Windows Event ID | `4625`                                |
| Supporting Rule  | `60122`                               |
| Correlation Rule | `60204`                               |
| Correlation Level| `10`                                  |
| Status           | Investigated                          |
| Environment      | SOC Home Lab                          |

## Detection

The investigation identified five matching Windows Event ID `4625` events.

Four events were associated with rule `60122`.

The repeated failures were correlated by Wazuh using rule `60204 — Multiple Windows Logon Failures`.

## Evidence

The investigation was supported by:

- Windows Security Event ID `4625`.
- Wazuh alerts associated with rule `60122`.
- Wazuh correlation alert `60204`.
- Endpoint information for `SOC-Windows`.
- Source host information from the laboratory network.
- Event timestamps.

## Timeline

The dashboard evidence places the observed activity at approximately:

`2026-09-24 17:04:23`

The exact timestamps of individual events can be obtained from the original Wazuh/Windows event records.

## Analysis

The observed activity consisted of repeated failed authentication attempts against the Windows endpoint.

The events were collected by the Wazuh Agent and analyzed by Wazuh.

Wazuh first identified the individual failed authentication events and then correlated the repeated activity into the `60204` alert.

## MITRE ATT&CK

**T1110 — Brute Force**

## Impact

The activity was restricted to the isolated SOC Home Lab.

No production systems were involved.

No evidence of successful authentication or compromise was identified during the controlled simulation.

## Response

The activity was validated as an intentional laboratory simulation.

The analyst:

1. Reviewed the Wazuh alert.
2. Identified the affected endpoint.
3. Reviewed the associated Event ID `4625` events.
4. Identified the source laboratory system.
5. Validated the repeated authentication pattern.
6. Documented the investigation.

## Mitigation

For a real environment, recommended defensive measures could include:

- Monitoring repeated authentication failures.
- Investigating originating systems.
- Applying appropriate account lockout controls.
- Enforcing strong authentication policies.
- Enabling multi-factor authentication where applicable.
- Correlating authentication failures with other security events.

## Conclusion

The SOC Home Lab successfully demonstrated the detection and investigation of repeated failed Windows authentication attempts.

The validated detection chain was:

```text
Authentication Attempt
        ↓
Windows Event ID 4625
        ↓
Wazuh Agent
        ↓
Rule 60122
        ↓
Rule 60204
        ↓
SOC Investigation
```

