# SOC Home Lab: Threat Detection & Incident Response Using Wazuh SIEM

## Overview

This project demonstrates the design, deployment, and operation of a Security Operations Center (SOC) Home Lab using Wazuh SIEM, Sysmon, Windows 10, Ubuntu Server, and Kali Linux.

The objective was to simulate real-world cyber attack scenarios, collect endpoint telemetry, generate security alerts, perform threat hunting, and investigate incidents using industry-standard defensive security tools.

The lab replicates a practical enterprise SOC environment where security analysts monitor endpoints, detect suspicious activity, investigate alerts, and map adversary behavior to the MITRE ATT&CK Framework.

---

## Project Objectives

* Build a fully functional SOC Home Lab
* Deploy and configure Wazuh SIEM
* Install and onboard Windows endpoints
* Configure Sysmon for advanced telemetry collection
* Simulate attacker activity using Kali Linux
* Generate and analyze security events
* Investigate alerts through Threat Hunting
* Map detections to MITRE ATT&CK techniques
* Practice real-world SOC Analyst workflows

---

# Lab Architecture

```text
                    ┌─────────────────┐
                    │   Kali Linux    │
                    │   Attacker VM   │
                    └────────┬────────┘
                             │
                             │
                             ▼
┌───────────────────────────────────────────────┐
│           Windows 10 Endpoint                 │
│                                                │
│ • Sysmon Installed                             │
│ • Wazuh Agent Installed                        │
│ • Security Event Logs                          │
└─────────────────┬─────────────────────────────┘
                  │
                  │ Log Collection
                  ▼
┌───────────────────────────────────────────────┐
│            Ubuntu Server                       │
│                                                │
│ • Wazuh Manager                                │
│ • Wazuh Indexer                                │
│ • Wazuh Dashboard                              │
│ • Threat Hunting Module                        │
└───────────────────────────────────────────────┘
```

---

# Technologies Used

| Category            | Technology            |
| ------------------- | --------------------- |
| SIEM                | Wazuh                 |
| Endpoint Monitoring | Sysmon                |
| Operating System    | Ubuntu Server         |
| Endpoint            | Windows 10            |
| Attacker Machine    | Kali Linux            |
| Threat Intelligence | MITRE ATT&CK          |
| Log Collection      | Wazuh Agent           |
| Network Analysis    | ICMP, TCP, Event Logs |
| Virtualization      | VMware Workstation    |

---

# Environment Configuration

| Machine       | IP Address      | Role               |
| ------------- | --------------- | ------------------ |
| Ubuntu Server | 192.168.207.128 | Wazuh Manager      |
| Windows 10    | 192.168.207.130 | Monitored Endpoint |
| Kali Linux    | 192.168.207.129 | Attack Simulation  |

---

# Project Walkthrough

## Step 1: Verify Network Connectivity

Validated communication between all systems within the SOC environment.

### Kali Linux Network Configuration

![Kali Configuration](screenshots/01-Kali-IP.png)

### Ubuntu Server Network Configuration

![Ubuntu Configuration](screenshots/02-Wazuh-IP.png)

### Windows 10 Network Configuration

![Windows Configuration](screenshots/03-Windows-IP.png)

### Kali to Windows Connectivity Test

![Ping Windows](screenshots/04-Kali-to-Windows-Ping.png)

### Kali to Wazuh Connectivity Test

![Ping Wazuh](screenshots/05-Kali-to-Ubuntu-Ping.png)

---

## Step 2: Deploy Wazuh SIEM

Installed and configured:

* Wazuh Manager
* Wazuh Dashboard
* Wazuh Indexer

### Wazuh Dashboard Access

![Dashboard](screenshots/06-Wazuh-Dashboard.png)

---

## Step 3: Endpoint Onboarding

Installed the Wazuh Agent on Windows 10 and successfully connected it to the Wazuh Manager.

### Connected Endpoint

![Agent Connected](screenshots/07-Agent-Active.png)

---

## Step 4: Sysmon Deployment

Installed Microsoft Sysmon to capture advanced endpoint telemetry.

Monitored events included:

* Process Creation
* PowerShell Activity
* Network Connections
* Registry Changes
* File Creation
* DLL Loading

### Sysmon Service Running

![Sysmon](screenshots/08-Sysmon-Running.png)

### Sysmon Log Collection Configuration

![Sysmon Config](screenshots/09-Sysmon-Log-Forwarding-Configured.png)

---

## Step 5: Security Event Collection

Verified that endpoint logs were successfully ingested into Wazuh.

### Sysmon Events in Wazuh

![Sysmon Events](screenshots/10-Sysmon-Events-Detected-in-Wazuh.png)

---

## Step 6: Detection Engineering

Generated security-relevant activities to trigger Wazuh detections.

### PowerShell Activity Detection

Detected PowerShell execution and associated MITRE ATT&CK mapping.

![PowerShell Detection](screenshots/11-Process-Creation-Detection.png)

### Failed Login Monitoring

Detected authentication failures from Windows Security Logs.

![Failed Login](screenshots/12-Failed-Login-Detection.png)

### New User Account Creation Detection

Detected administrative account creation activity.

![User Creation](screenshots/13-New-User-Creation-Detection.png)

---

## Step 7: Attack Simulation

Performed reconnaissance activities from Kali Linux to generate alerts.

### Nmap SYN Scan

![Nmap SYN Scan](screenshots/14-Nmap-SYN-Scan.png)

### Nmap Aggressive Scan

![Nmap Aggressive Scan](screenshots/15-Nmap-Aggressive-Scan.png)

---

## Step 8: Threat Hunting Investigation

Performed event analysis using Wazuh Threat Hunting.

Investigation included:

* Event review
* Rule analysis
* Alert severity validation
* Endpoint telemetry review
* Log correlation

### Threat Hunting Investigation

![Threat Hunting](screenshots/16-Threat-Hunting-Investigation.png)

---

## Step 9: MITRE ATT&CK Mapping

Mapped observed attacker behavior to MITRE ATT&CK techniques.

Example detection:

| Technique | Description               |
| --------- | ------------------------- |
| T1059.001 | PowerShell Execution      |
| T1046     | Network Service Discovery |
| T1087     | Account Discovery         |
| T1057     | Process Discovery         |

### MITRE ATT&CK Correlation

![MITRE ATT\&CK](screenshots/17-MITRE-ATTACK-Mapping.png)

---

# SOC Analyst Investigation Process

1. Receive Alert
2. Validate Alert
3. Investigate Related Events
4. Determine Severity
5. Identify Impact
6. Correlate Telemetry
7. Map to MITRE ATT&CK
8. Document Findings
9. Recommend Remediation

---

# Key Skills Demonstrated

### Security Monitoring

* SIEM Administration
* Log Collection
* Event Correlation
* Alert Analysis

### Threat Detection

* Sysmon Monitoring
* Windows Event Analysis
* PowerShell Detection
* Attack Surface Visibility

### Incident Response

* Triage
* Investigation
* Root Cause Analysis
* Evidence Collection

### Threat Hunting

* IOC Investigation
* Event Correlation
* Log Analysis
* MITRE ATT&CK Mapping

### Blue Team Operations

* Endpoint Monitoring
* Detection Engineering
* Security Operations
* SOC Workflows

---
## 📚 Project Documentation

This repository contains detailed technical documentation covering the complete SOC investigation lifecycle, from lab deployment and detection engineering to threat hunting and incident response.

### Documentation Overview

| Document                          | Description                                                                                                                                                           |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Project-Overview.md**           | High-level overview of the SOC Home Lab, objectives, technologies used, and project scope.                                                                            |
| **Lab-Architecture.md**           | Detailed architecture of the environment including Kali Linux, Windows 10, Ubuntu Server, Wazuh SIEM, Sysmon, and network design.                                     |
| **Detection-Use-Cases.md**        | Security detection scenarios developed and tested during the project, including PowerShell execution, account creation, failed logins, and reconnaissance activities. |
| **Incident-Response-Report.md**   | Formal incident response investigation documenting alert analysis, findings, root cause assessment, MITRE ATT&CK mapping, and remediation recommendations.            |
| **Lessons-Learned.md**            | Key technical and operational lessons learned while building and operating the SOC Home Lab.                                                                          |
| **wazuh-sysmon-configuration.md** | Configuration details for Wazuh Agent and Sysmon used to collect and analyze Windows security telemetry.                                                              |
| **SOC-Home-Lab-Final-Report.pdf** | Executive-level SOC analyst report summarizing architecture, detections, investigations, findings, MITRE ATT&CK mapping, and recommendations.                         |

---

# Results

Successfully built and operated a functional SOC environment capable of:

* Monitoring Windows endpoints
* Collecting Sysmon telemetry
* Detecting suspicious activities
* Investigating security events
* Performing threat hunting
* Mapping detections to MITRE ATT&CK
* Demonstrating real-world SOC Analyst capabilities

---

# Future Enhancements

* Integrate Suricata IDS
* Deploy Active Directory
* Configure Sigma Rules
* Integrate Threat Intelligence Feeds
* Deploy Multi-Endpoint Monitoring
* Implement Automated Response Playbooks

---

## Author

**Nitin Sukthe**

Future Cloud Security Engineer | SOC Analyst | Blue Team Enthusiast

Focused on Security Operations, Threat Detection, Incident Response, Cloud Security, and SIEM Engineering.
