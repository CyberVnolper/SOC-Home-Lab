# Incident Report — INC-001

## Executive Summary

INC-001 documents a controlled brute-force authentication simulation carried out within the isolated SOC Home Lab.

The activity was generated from the laboratory Kali Linux system against the monitored Windows endpoint and was detected through Windows Security Event ID `4625` telemetry collected by Wazuh.

The investigation confirmed that Wazuh first identified failed authentication attempts individually and subsequently correlated repeated failures into a level `10` alert through rule `60204 — Multiple Windows Logon Failures`.

The incident was handled entirely within the laboratory environment.

## Incident Details

| Field                 | Value                                |
|:----------------------|:-------------------------------------|
| **Incident ID**       | `INC-001`                            |
| **Incident Type**     | Brute Force / Repeated Failed Logons |
| **Affected Host**     | `SOC-Windows`                        |
| **Target IP**         | `192.168.56.102`                     |
| **Target Account**    | `victorr`                            |
| **Windows Event ID**  | `4625`                               |
| **Supporting Rule**   | `60122`                              |
| **Correlation Rule**  | `60204`                              |
| **Correlation Level** | `10`                                 |
| **Environment**       | SOC Home Lab                         |
| **Status**            | Investigated                         |

## Detection Analysis

Rule `60122` generated individual alerts for failed Windows logons.

The correlated `60204` alert was generated after repeated Event ID `4625` activity reached the configured correlation threshold. Its recorded frequency was `8`, and the alert was associated by Wazuh with MITRE ATT&CK technique `T1110 — Brute Force`.

The investigated event data shows repeated failures associated with the laboratory source `192.168.56.104` and workstation `SOCKALI`.

## Technical Findings

The relevant authentication telemetry contains the following characteristics:

| Field                      | Observed Value                        |
|:---------------------------|:--------------------------------------|
| **Source IP**              | `192.168.56.104`                      |
| **Workstation**            | `SOCKALI`                             |
| **Authentication Package** | `NTLM`                                |
| **Logon Process**          | `NtLmSsp`                             |
| **Logon Type**             | `3`                                   |
| **Status**                 | `0xc000006d`                          |
| **Substatus**              | `0xc000006a`                          |
| **Windows Channel**        | `Security`                            |
| **Provider**               | `Microsoft-Windows-Security-Auditing` |

The event records correspond to failed authentication attempts rather than successful logons.

The collected correlation data contains both `victorr` and `victorrr` as target usernames in different Event ID `4625` records. The values have been preserved exactly as collected from Wazuh.

## Timeline

The correlated Wazuh alert was recorded at:

`2026-09-24T15:04:23.768+0000`

The underlying Windows authentication failures occurred immediately beforehand.

Individual event timestamps and Windows event record identifiers are preserved in the evidence files:

*   [`evidence/events/event-60122.json`](evidence/events/event-60122.json)
*   [`evidence/events/event-60204.json`](evidence/events/event-60204.json)

## Impact Assessment

The activity was restricted to the isolated SOC Home Lab.

No production systems were involved.

Within the evidence collected for this incident, no successful authentication was identified and no additional compromise was observed.

## Response

The incident response consisted of:

1.  Reviewing the Wazuh correlation alert.
2.  Identifying the Windows endpoint involved.
3.  Reviewing the associated Event ID `4625` activity.
4.  Identifying the originating laboratory system.
5.  Confirming the repeated authentication-failure pattern.
6.  Preserving the relevant event and log data.
7.  Recording the investigation results.

## Mitigation

For a production environment, appropriate defensive controls for this type of activity could include:

*   Monitoring repeated authentication failures.
*   Investigating source systems generating abnormal authentication activity.
*   Applying suitable account lockout and rate-limiting controls.
*   Enforcing strong authentication policies.
*   Using multi-factor authentication where appropriate.
*   Correlating authentication failures with additional endpoint and network telemetry.

These measures are listed as general defensive considerations and were not required to remediate a production compromise in this laboratory exercise.

## Evidence Reference

The investigation evidence is maintained separately from this report:

### Event Data
*   [`evidence/events/event-60122.json`](evidence/events/event-60122.json)
*   [`evidence/events/event-60204.json`](evidence/events/event-60204.json)

### Log Data
*   [`evidence/logs/wazuh-60122.txt`](evidence/logs/wazuh-60122.txt)
*   [`evidence/logs/wazuh-60204.txt`](evidence/logs/wazuh-60204.txt)

### Screenshots
*   [`evidence/screenshots/01-windows-4625.png`](evidence/screenshots/01-windows-4625.png)
*   [`evidence/screenshots/02-wazuh-4625-alert.png`](evidence/screenshots/02-wazuh-4625-alert.png)
*   [`evidence/screenshots/03-wazuh-4625-timeline.png`](evidence/screenshots/03-wazuh-4625-timeline.png)

## Conclusion

INC-001 demonstrated a complete detection and investigation workflow for repeated Windows authentication failures within the SOC Home Lab.

Wazuh successfully collected the Windows Security Event ID `4625` telemetry, detected individual failures through rule `60122`, and correlated the repeated activity through rule `60204`.

The investigation remained within the isolated laboratory environment, and the collected evidence did not show a successful authentication or further compromise.

## Classification

**Laboratory Simulation — Investigated**


