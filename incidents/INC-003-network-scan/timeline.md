# INC-003 — Timeline

| Time                           | Source     | Event                                                                                                      |
| ------------------------------ | ---------- | ---------------------------------------------------------------------------------------------------------- |
| `2026-09-28 14:48`             | Kali Linux | Nmap TCP SYN scan executed against `192.168.56.102`, ports `1-1000`.                                       |
| `2026-09-28 14:48–14:49`       | Windows    | Multiple Event ID `5157` records were observed for blocked connections.                                    |
| `2026-09-28T13:09:09.0864532Z` | Windows    | Preserved Event ID `5157` recorded a blocked TCP connection from `192.168.56.104` to `192.168.56.102:445`. |
| `2026-09-28T13:09:15.732+0000` | Wazuh      | The preserved event was processed by rule `60104`.                                                         |

## Nmap Result

```text
Host is up (0.0015s latency).
All 1000 scanned ports on 192.168.56.102 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
```

## Evidence Note

The preserved Wazuh event has an earlier timestamp than the Nmap execution used for the laboratory screenshot.

The original timestamps are retained without modification.

