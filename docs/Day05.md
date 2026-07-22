# Day 05 – Investigating Wazuh FIM Alerts

## Objective

Learn how to investigate File Integrity Monitoring (FIM) alerts using the Wazuh dashboard and understand why different Rule IDs are generated for different file events.

---

## Activities Completed

### 1. Investigated File Creation Alert

Rule ID: 554

Description:
- File added to the system

Verified:
- Agent information
- File path
- Timestamp
- Decoder
- Event details

---

### 2. Investigated File Modification Alert

Rule ID: 550

Description:
- Integrity checksum changed

Verified:
- MD5 hash
- SHA1 hash
- SHA256 hash
- File size change
- Modification timestamp

---

### 3. Investigated File Deletion Alert

Rule ID: 553

Description:
- File deleted

Verified:
- Deleted file path
- Event timestamp
- Agent information

---

### 4. Learned JSON Investigation

Opened the JSON view for FIM alerts.

Observed important fields:

- agent.name
- agent.id
- manager.name
- rule.id
- rule.level
- rule.description
- syscheck.path
- syscheck.event
- syscheck.md5_after
- syscheck.sha1_after
- syscheck.sha256_after

---

### 5. Compared All FIM Events

Created a comparison report showing:

- File Added
- File Modified
- File Deleted

Compared:

- Timestamp
- Agent
- Decoder
- Rule ID
- Rule Description
- Event Type
- Detection Mode
- File Path
- Hash Changes

---

## Skills Learned

- FIM Investigation
- Wazuh Rule Analysis
- JSON Event Investigation
- Threat Hunting
- Event Correlation
- Security Alert Investigation

---

## Key Learning

Different Rule IDs represent different security events.

Rule 554 → File Added

Rule 550 → File Modified

Rule 553 → File Deleted

The same monitored file can generate different alerts depending on the action performed.

Hashes (MD5, SHA1, SHA256) help verify whether a file's contents have changed.

---

## Outcome

Successfully investigated the complete lifecycle of a monitored file using Wazuh:

File Created → File Modified → File Deleted

This demonstrates that Wazuh File Integrity Monitoring is functioning correctly and provides real-time visibility into file system activity.