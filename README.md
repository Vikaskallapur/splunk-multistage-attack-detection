# Multi-Stage Attack Detection & Risk-Based Incident Prioritization using Splunk

![Splunk](https://img.shields.io/badge/Splunk-Enterprise-black?logo=splunk)
![SIEM](https://img.shields.io/badge/Technology-SIEM-blue)
![Windows](https://img.shields.io/badge/Logs-Windows%20Security-lightgrey)
![SPL](https://img.shields.io/badge/Language-SPL-orange)

## Overview

A Splunk-based Security Operations Center (SOC) monitoring and detection project designed to identify suspicious authentication activity and Windows process execution.

The project uses Windows Security Event Logs and custom Splunk Search Processing Language (SPL) queries to detect brute-force activity, repeated authentication failures, successful logins following failures, suspicious process execution, and prioritize incidents using risk scoring.

## Objectives

- Detect brute-force authentication activity
- Identify multiple failed login attempts
- Detect successful authentication following repeated failures
- Monitor Windows process creation activity
- Prioritize suspicious activity using risk scores
- Provide a structured SOC investigation workflow
- Create scheduled Splunk alerts for security detections

## Technologies

- Splunk Enterprise
- SPL (Search Processing Language)
- Windows Security Event Logs
- SIEM
- SOC Detection & Investigation
- MITRE ATT&CK concepts

## Windows Event IDs

| Event ID | Description | Security Use |
|---|---|---|
| 4624 | Successful Logon | Authentication monitoring |
| 4625 | Failed Logon | Brute-force detection |
| 4688 | Process Creation | Process execution monitoring |

## Detection Engineering

### 1. Brute Force Detection

Detects repeated failed authentication attempts within a 5-minute window.

**Threshold:** 3+ failed logins.

### 2. Multiple Failed Login Detection

Identifies accounts experiencing repeated authentication failures.

### 3. Successful Login After Multiple Failures

Correlates failed and successful authentication events to identify potentially compromised accounts.

### 4. Suspicious Process Detection

Monitors Event ID 4688 for potentially suspicious scripting interpreters:

- PowerShell
- CMD
- WScript
- CScript

### 5. Risk-Based Prioritization

Assigns risk scores based on failed-login volume.

| Failed Logins | Risk Score | Risk Level |
|---:|---:|---|
| 5+ | 90 | HIGH |
| 3–4 | 60 | MEDIUM |
| 1–2 | 30 | LOW |

## SOC Dashboard

The project includes a Splunk SOC dashboard for monitoring:

- Failed authentication activity
- Successful authentication activity
- Process creation
- Brute-force indicators
- Risk-prioritized authentication activity

Dashboard documentation:

`dashboards/soc-dashboard.md`

## Alerting

Scheduled Splunk alerts were configured for security monitoring and detection.

Alert logic includes:

- Brute-force activity
- Multiple failed logins
- Successful login after failures
- High-volume failed logins
- Unusual authentication activity
- Suspicious process execution
- Risk-based failed-login activity

Alert documentation:

`alerts/alert-rules.md`

## Investigation Workflow

The investigation process follows a SOC analyst workflow:

1. Review the triggered alert
2. Determine severity/risk
3. Identify affected account
4. Identify affected host
5. Review timestamp
6. Examine source network information
7. Analyze authentication details
8. Correlate failed and successful logins
9. Investigate process creation events
10. Determine whether activity is suspicious
11. Document findings and recommended response

Investigation documentation:

`investigation/investigation-workflow.md`

## Repository Structure

```text
splunk-multistage-attack-detection/
│
├── README.md
│
├── alerts/
│   └── alert-rules.md
│
├── dashboards/
│   └── soc-dashboard.md
│
├── detections/
│   ├── brute-force.spl
│   ├── multiple-failed-logins.spl
│   ├── successful-login-after-failures.spl
│   ├── suspicious-process.spl
│   └── risk-based-prioritization.spl
│
└── investigation/
    └── investigation-workflow.md
