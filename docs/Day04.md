# Day 04 – File Integrity Monitoring (FIM)

## Objective

Configure Wazuh File Integrity Monitoring (FIM) to monitor a custom directory and detect file creation, modification, and deletion events.

---

## Tasks Completed

- Learned File Integrity Monitoring (FIM)
- Examined the `<syscheck>` configuration
- Added a custom monitored directory
- Enabled real-time monitoring
- Restarted the Wazuh Agent
- Created a test file
- Modified the file
- Deleted the file
- Investigated FIM alerts in Threat Hunting

---

## Commands Used

```bash
mkdir -p ~/fim-test

sudo nano /var/ossec/etc/ossec.conf

sudo systemctl restart wazuh-agent

echo "Hello Wazuh" > ~/fim-test/test.txt

echo "Day 4 FIM Test" >> ~/fim-test/test.txt

rm ~/fim-test/test.txt
```

---

## FIM Rules Observed

### Rule 554

- Level: 5
- Description: File added to the system

### Rule 550

- Level: 7
- Description: Integrity checksum changed

### Rule 553

- Level: 7
- Description: File deleted

---

## Concepts Learned

- File Integrity Monitoring
- Real-time monitoring
- inotify
- Checksums
- Threat Hunting
- Rule IDs
- Rule Levels

---

## Skills Practiced

- Linux Administration
- SIEM Operations
- Threat Hunting
- File Integrity Monitoring
- Event Investigation

---

## Screenshots

- 18-fim-test-directory.png
- 19-ossec-syscheck-config.png
- 20-fim-enabled.png
- 21-file-created-event.png
- 22-file-modified-event.png
- 23-file-deleted-event.png

---

## Result

Successfully configured Wazuh File Integrity Monitoring and verified that file creation, modification, and deletion events were detected and displayed in the Threat Hunting dashboard.