# Alert Rules

## Brute Force Login Detection
- Event ID: 4625
- Detects repeated failed authentication attempts.
- Threshold: 3 or more failures within 5 minutes.
- Severity: Medium/High depending on volume.

## Multiple Failed Login Detection
- Event ID: 4625
- Identifies accounts experiencing repeated authentication failures.
- Used for identifying possible credential attacks.

## Successful Login After Multiple Failures
- Event IDs: 4625 and 4624
- Detects successful authentication occurring after multiple failures.
- Useful for identifying possible account compromise.

## Suspicious Process Execution
- Event ID: 4688
- Monitors process creation activity.
- Focuses on PowerShell, CMD, WScript and CScript.
- Useful for identifying suspicious scripting activity.

## Risk-Based Failed Login Detection
- Event ID: 4625
- Assigns a risk score based on failed-login volume.
- HIGH: 80+
- MEDIUM: 50+
- LOW: below 50
