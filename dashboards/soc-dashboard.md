# SOC Dashboard

## Overview

The Splunk SOC dashboard provides visibility into Windows authentication and process activity.

## Dashboard Components

### Failed Login Monitoring
Monitors Windows Event ID 4625 to identify repeated authentication failures.

### Successful Login Monitoring
Monitors Windows Event ID 4624 to identify successful authentication activity.

### Process Creation Monitoring
Monitors Windows Event ID 4688 for newly created processes.

### Brute Force Detection
Identifies 3 or more failed login attempts within a 5-minute window.

### Risk-Based Prioritization
Assigns risk scores to failed-login activity:

- HIGH: 80+
- MEDIUM: 50–79
- LOW: below 50

## Data Source

- Splunk Enterprise
- Windows Security Event Logs

## Important Event IDs

| Event ID | Activity |
|---|---|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4688 | Process Creation |
