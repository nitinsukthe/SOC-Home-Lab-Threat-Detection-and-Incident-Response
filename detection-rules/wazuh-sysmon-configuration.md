# Wazuh Sysmon Configuration

## Overview

This document describes the integration of Microsoft Sysmon with Wazuh SIEM to enhance endpoint visibility and improve threat detection capabilities.

Sysmon provides detailed telemetry about system activity, while Wazuh collects, correlates, and analyzes those events to generate actionable security alerts.

This integration significantly improves detection coverage for attacker behaviors commonly observed during real-world cyber incidents.

---

# Objective

The primary goals of this configuration are:

* Monitor process creation activity
* Capture PowerShell execution
* Track DNS queries
* Detect file creation events
* Monitor network connections
* Identify persistence mechanisms
* Improve threat hunting capabilities
* Support MITRE ATT&CK-based detections

---

# Components

## Wazuh Agent

Installed on:

* Windows 10 Endpoint

Responsibilities:

* Collect Sysmon logs
* Forward events to Wazuh Manager
* Maintain secure communication with SIEM

---

## Sysmon

Installed on:

* Windows 10 Endpoint

Responsibilities:

* Generate advanced endpoint telemetry
* Capture attacker behaviors
* Provide forensic visibility

---

## Wazuh Manager

Installed on:

* Ubuntu Server

Responsibilities:

* Receive endpoint logs
* Correlate events
* Apply detection rules
* Generate alerts

---

# Sysmon Event Sources Monitored

## Event ID 1

### Process Creation

Purpose:

Detect process execution activity.

Examples:

* powershell.exe
* cmd.exe
* whoami.exe
* net.exe
* tasklist.exe

Security Value:

Provides visibility into attacker command execution.

MITRE ATT&CK:

* T1059 Command and Scripting Interpreter

---

## Event ID 3

### Network Connection

Purpose:

Monitor outbound and inbound network communications.

Examples:

* PowerShell web requests
* Reverse shells
* Suspicious external connections

Security Value:

Identifies command-and-control communications.

MITRE ATT&CK:

* T1071 Application Layer Protocol

---

## Event ID 7

### Image Load

Purpose:

Track DLL loading activity.

Security Value:

Detect DLL hijacking attempts and malicious module loading.

MITRE ATT&CK:

* T1574 Hijack Execution Flow

---

## Event ID 11

### File Creation

Purpose:

Monitor creation of files and executables.

Examples:

* Malware payloads
* Dropped executables
* Temporary attack tools

Security Value:

Detects malware staging activity.

MITRE ATT&CK:

* T1105 Ingress Tool Transfer

---

## Event ID 13

### Registry Modification

Purpose:

Detect changes to Windows Registry keys.

Security Value:

Identify persistence and configuration modifications.

MITRE ATT&CK:

* T1112 Modify Registry

---

## Event ID 22

### DNS Query

Purpose:

Monitor domain resolution requests.

Examples:

* Malicious domains
* Command-and-control infrastructure
* Suspicious external services

Security Value:

Supports threat hunting and IOC detection.

MITRE ATT&CK:

* T1071.004 DNS

---

# Wazuh Configuration Validation

The following validations were successfully performed:

✅ Wazuh Agent connected to Manager

✅ Sysmon service operational

✅ Windows Event Logs collected

✅ Sysmon events forwarded

✅ Threat Hunting visibility confirmed

✅ MITRE ATT&CK mappings generated

---

# Sample Alerts Observed

## PowerShell Execution

Rule Description:

PowerShell process spawned PowerShell instance

Severity:

Medium

MITRE ATT&CK:

T1059.001 – PowerShell

---

## Executable File Creation

Rule Description:

Executable file dropped in folder commonly used by malware

Severity:

High

MITRE ATT&CK:

T1105 – Ingress Tool Transfer

---

## Service Modification

Rule Description:

Service startup type was changed

Severity:

Medium

MITRE ATT&CK:

T1543 – Create or Modify System Process

---

## DNS Query Monitoring

Rule Description:

DNS query activity observed

Severity:

Informational

MITRE ATT&CK:

T1071.004 – DNS

---

# Threat Hunting Benefits

Integrating Sysmon with Wazuh provides:

* Enhanced endpoint visibility
* Faster threat detection
* Improved incident investigations
* Better forensic analysis
* Reduced attacker dwell time
* ATT&CK-based threat mapping

---

# Security Outcome

The Wazuh-Sysmon integration successfully transformed a standard Windows endpoint into a monitored security asset capable of generating detailed telemetry for detection engineering, threat hunting, and incident response operations.

This configuration closely resembles monitoring practices used by modern enterprise Security Operations Centers (SOCs).
