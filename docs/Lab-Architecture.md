# Lab Architecture

## Architecture Overview

The SOC Home Lab consists of three virtual machines deployed within VMware Workstation.

```text
                    Kali Linux
                  (Attacker System)
                          |
                          |
                          ▼

      ┌─────────────────────────────┐
      │      Windows 10 Endpoint    │
      │                             │
      │  Sysmon                     │
      │  Wazuh Agent                │
      └──────────────┬──────────────┘
                     │
                     │ Event Logs
                     ▼

      ┌─────────────────────────────┐
      │      Ubuntu Server          │
      │                             │
      │ Wazuh Manager               │
      │ Wazuh Dashboard             │
      │ Wazuh Indexer               │
      └─────────────────────────────┘
```

---

## Components

### Ubuntu Server

Role:

* SIEM Platform
* Event Correlation Engine
* Log Storage
* Threat Hunting Dashboard

Services:

* Wazuh Manager
* Wazuh Dashboard
* Wazuh Indexer

IP Address:

192.168.207.128

---

### Windows 10 Endpoint

Role:

* Monitored Asset

Installed Components:

* Wazuh Agent
* Sysmon

Collected Data:

* Process Creation Events
* DNS Queries
* PowerShell Activity
* User Account Events
* Service Modifications

IP Address:

192.168.207.130

---

### Kali Linux

Role:

* Attack Simulation Platform

Activities:

* Reconnaissance
* Nmap Scanning
* Connectivity Testing
* Threat Simulation

IP Address:

192.168.207.129

---

## Security Monitoring Workflow

1. Endpoint activity occurs.
2. Sysmon records telemetry.
3. Wazuh Agent collects logs.
4. Events are forwarded to Wazuh Manager.
5. Wazuh applies detection rules.
6. Alerts are generated.
7. Analysts investigate through Threat Hunting.
8. Events are mapped to MITRE ATT&CK techniques.
