# MITRE ATT&CK Mapping

This project maps its detection logic to relevant MITRE ATT&CK techniques.

| Detection | MITRE ATT&CK Technique | ID | Purpose |
|---|---|---|---|
| Brute Force Login Detection | Brute Force | T1110 | Detect repeated authentication failures |
| Multiple Failed Logins | Brute Force | T1110 | Identify repeated credential attempts |
| Successful Login After Failures | Valid Accounts | T1078 | Investigate potentially suspicious use of valid credentials |
| Suspicious Process Detection | Command and Scripting Interpreter | T1059 | Detect potentially suspicious command/scripting activity |
| Process Creation Monitoring | Process Discovery / Execution Telemetry | — | Provides process-creation telemetry for investigation |

## Detection Context

The MITRE ATT&CK mappings provide a framework for relating the Splunk detections to common adversary behaviors.

The project primarily focuses on:

- Credential access and authentication attacks
- Suspicious use of accounts
- Command and scripting activity
- Windows process execution

> Note: ATT&CK mappings describe the behavior the detection is intended to identify; they do not imply that the corresponding attack occurred in the lab dataset.
