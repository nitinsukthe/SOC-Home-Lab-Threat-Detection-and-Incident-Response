# Detection Use Cases

## Overview

This document outlines the primary security detection scenarios implemented and validated during the SOC Home Lab project.

---

# Use Case 1: PowerShell Execution Detection

## Objective

Detect PowerShell execution activity commonly used by attackers for command execution and post-exploitation.

## Detection Source

* Sysmon Event ID 1
* Process Creation Events

## MITRE ATT&CK

Technique: T1059.001

Tactic:

* Execution

## Security Value

PowerShell is frequently abused during malware infections, ransomware attacks, and lateral movement activities.

---

# Use Case 2: Service Configuration Modification

## Objective

Detect unauthorized modifications to Windows services.

## Detection Source

Windows Event Logs

## MITRE ATT&CK

Technique: T1543

Tactic:

* Persistence

## Security Value

Attackers often modify services to maintain persistence after compromise.

---

# Use Case 3: DNS Query Monitoring

## Objective

Identify suspicious domain resolution activity.

## Detection Source

Sysmon Event ID 22

## MITRE ATT&CK

Technique: T1071

Tactic:

* Command and Control

## Security Value

DNS traffic can reveal malware communications and attacker infrastructure.

---

# Use Case 4: Executable File Creation

## Objective

Detect executable files being dropped into suspicious directories.

## Detection Source

Sysmon File Creation Events

## MITRE ATT&CK

Technique: T1105

Tactic:

* Command and Control

## Security Value

Executable drops often indicate malware delivery or payload staging.

---

# Use Case 5: Network Reconnaissance

## Objective

Detect scanning and enumeration activities.

## Detection Source

Network Events

## MITRE ATT&CK

Technique: T1046

Tactic:

* Discovery

## Security Value

Reconnaissance activity frequently represents the earliest phase of an attack.
