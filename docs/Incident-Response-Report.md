# Incident Response Report

## Incident Summary

During security monitoring operations, multiple endpoint events were collected and analyzed through Wazuh SIEM.

Several alerts indicated potentially suspicious behavior requiring investigation.

---

## Detection Details

### Alert 1

Rule Description:

PowerShell Process Spawned PowerShell Instance

Severity:

Medium

MITRE ATT&CK:

T1059.001 – PowerShell

---

### Alert 2

Rule Description:

Executable File Dropped in Folder Commonly Used by Malware

Severity:

High

MITRE ATT&CK:

T1105 – Ingress Tool Transfer

---

### Alert 3

Rule Description:

Service Startup Type Was Changed

Severity:

Medium

MITRE ATT&CK:

T1543 – Create or Modify System Process

---

## Investigation Process

### Phase 1: Triage

* Verified alert legitimacy
* Confirmed affected endpoint
* Reviewed event timestamps

### Phase 2: Analysis

* Correlated Sysmon logs
* Reviewed Windows Event Logs
* Examined process activity
* Investigated parent-child process relationships

### Phase 3: Threat Hunting

* Searched related events
* Reviewed historical telemetry
* Validated MITRE ATT&CK mappings

---

## Findings

No active compromise was identified during testing.

All generated alerts originated from controlled laboratory activities conducted for validation and learning purposes.

---

## Recommendations

* Continue monitoring PowerShell activity
* Enable enhanced logging
* Review service modification events
* Implement threat intelligence integration
* Develop custom detection rules

---

## Conclusion

The incident response workflow successfully demonstrated the ability to:

* Detect suspicious behavior
* Investigate security events
* Perform threat hunting
* Conduct alert triage
* Map findings to MITRE ATT&CK

These capabilities align closely with real-world SOC Analyst responsibilities.
