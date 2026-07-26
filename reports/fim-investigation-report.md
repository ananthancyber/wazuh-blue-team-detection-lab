# 📑 File Integrity Monitoring (FIM) Investigation Report

## Overview

This report documents the implementation, validation, and investigation of File Integrity Monitoring (FIM) using Wazuh 4.14.6. The objective was to verify that Wazuh could detect file creation, modification, and deletion events in real time on the monitored Ubuntu endpoint.

The exercise demonstrates one of the core capabilities of a Security Information and Event Management (SIEM) platform by monitoring critical files for unauthorized changes and generating security alerts for analyst investigation.

---

# Objectives

The objectives of this investigation were to:

- Configure File Integrity Monitoring (FIM) in Wazuh.
- Monitor a dedicated test directory.
- Generate file system events.
- Verify alert generation in the Wazuh Dashboard.
- Investigate the generated alerts and validate the recorded metadata.

---

# Lab Environment

| Component | Description |
|-----------|-------------|
| Host OS | Windows 11 |
| Virtualization | VMware Workstation |
| SIEM | Wazuh 4.14.6 (Docker Single Node) |
| Endpoint | Ubuntu 26.04 LTS |
| Attack/Test Machine | Ubuntu Endpoint |
| Detection Module | Wazuh Syscheck (File Integrity Monitoring) |

---

# Configuration

A dedicated directory was created for testing.

```

mkdir -p ~/fim-test

```

The Wazuh agent configuration (`ossec.conf`) was updated to include the directory under the `<syscheck>` section.

After applying the configuration, the Wazuh agent was restarted to enable monitoring of the new directory.

---

# Attack Simulation

Three common file system activities were performed inside the monitored directory.

### Test 1 – File Creation

A new file (`test.txt`) was created inside the monitored directory.

Expected Result:

- Wazuh should detect the newly created file.
- A Syscheck alert should be generated.

---

### Test 2 – File Modification

The contents of the file were modified.

Expected Result:

- Wazuh should detect changes to the file integrity.
- A checksum comparison should identify the modification.

---

### Test 3 – File Deletion

The monitored file was deleted.

Expected Result:

- Wazuh should generate an alert indicating that the monitored file had been removed.

---

# Investigation Results

## Event 1 – File Created

| Field | Value |
|------|------|
| Rule ID | **554** |
| Severity | **5** |
| Description | File added to the system |
| Decoder | syscheck_new_entry |
| Location | syscheck |

The generated alert confirmed that Wazuh detected the creation of the monitored file in real time.

The alert included:

- monitored file path
- agent information
- timestamp
- rule description
- decoder information

---

## Event 2 – File Modified

| Field | Value |
|------|------|
| Rule ID | **550** |
| Severity | **7** |
| Description | Integrity checksum changed |
| Decoder | syscheck_integrity_changed |
| Location | syscheck |

Wazuh detected changes to the monitored file and compared multiple integrity attributes including:

- MD5
- SHA1
- SHA256
- file size
- modification time

The alert confirmed that the integrity values changed after editing the file.

---

## Event 3 – File Deleted

| Field | Value |
|------|------|
| Rule ID | **553** |
| Severity | **7** |
| Description | File deleted |
| Decoder | syscheck_deleted |
| Location | syscheck |

After deleting the monitored file, Wazuh immediately generated an alert indicating that the file had been removed from the monitored directory.

---

# Evidence

The following screenshots document the complete investigation:

1. Wazuh agent running
2. FIM test directory creation
3. Syscheck configuration
4. Wazuh agent restart
5. File creation alert (Rule 554)
6. File modification alert (Rule 550)
7. File deletion alert (Rule 553)
8. Alert detail view
9. Integrity checksum change details
10. File deletion event details

---

# Analysis

The investigation confirmed that File Integrity Monitoring was operating correctly after configuration.

Each file system action generated the expected Wazuh alert, allowing an analyst to identify:

- the affected file
- event timestamp
- monitored endpoint
- rule identifier
- alert severity
- integrity changes

The checksum comparison provided additional forensic information by showing exactly which integrity attributes changed after the file modification.

---

# SOC Relevance

File Integrity Monitoring is commonly used to detect:

- Unauthorized file modifications
- Malware persistence
- Web shell deployment
- Configuration tampering
- Insider threats
- Critical system file changes

These detections enable SOC analysts to investigate suspicious file activity before it escalates into a larger security incident.

---

# Key Learning Outcomes

Through this investigation I learned how to:

- Configure File Integrity Monitoring using Wazuh Syscheck.
- Monitor custom directories on a Linux endpoint.
- Restart and validate the Wazuh agent after configuration changes.
- Investigate file creation, modification, and deletion alerts.
- Interpret rule IDs, decoders, alert severity, and integrity metadata.
- Document security events using a structured incident investigation process.

---

# Conclusion

The File Integrity Monitoring implementation successfully detected all tested file operations. The generated alerts demonstrated that Wazuh can provide timely visibility into changes occurring on monitored endpoints, making FIM an important capability for endpoint monitoring and security operations.