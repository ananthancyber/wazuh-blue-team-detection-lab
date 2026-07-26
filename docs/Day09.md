# Day 9 – Custom Detection Rules & Active Response

## Objective

Learn how Wazuh Active Response works by creating a custom detection rule, monitoring a custom log source, and configuring a custom Active Response script.

---

## Concepts Learned

Today I learned the difference between **Detection** and **Response**.

- Detection identifies suspicious activity.
- Active Response automatically performs an action after a rule is triggered.

I also learned how Wazuh links:

- Custom log sources
- Detection rules
- Active Response commands
- Response scripts

---

# Lab Architecture

```
Custom Log File
        │
        ▼
Wazuh Agent
        │
        ▼
Custom Rule (100003)
        │
        ▼
Alert Generated
        │
        ▼
Active Response Configuration
        │
        ▼
Custom Response Script
```

---

# Tasks Performed

## 1. Configured Custom Log Monitoring

Created a custom log file:

```
/var/log/demo-security.log
```

Configured the Wazuh Agent to monitor the log using **syslog** format.

### Screenshot

**59 – Agent Configured to Monitor Custom Log**

---

## 2. Restarted the Wazuh Agent

Restarted the Ubuntu Wazuh Agent to apply the configuration.

Verified that the agent started successfully.

### Screenshot

**60 – Wazuh Agent Restarted Successfully**

---

## 3. Verified Log Monitoring

Generated test log entries inside:

```
/var/log/demo-security.log
```

Confirmed that the Wazuh Agent was monitoring the file.

### Screenshot

**61 – Agent Monitoring demo-security.log**

---

## 4. Created a Custom Detection Rule

Created a custom rule inside:

```
local_rules.xml
```

Rule ID:

```
100003
```

The rule detects log entries containing:

```
DEMO-SECURITY
```

### Screenshot

**62 – Rule 100003 Added**

---

## 5. Validated the Configuration

Validated the Wazuh Manager configuration using:

```bash
wazuh-analysisd -t
```

Validation completed successfully.

Return code:

```
0
```

### Screenshot

**63 – Wazuh Configuration Validation Successful**

---

## 6. Restarted the Wazuh Manager

Restarted the Wazuh Manager Docker container to load the new configuration.

### Screenshot

**64 – Wazuh Manager Restarted**

---

## 7. Verified Detection

Generated another custom log entry.

Verified that Rule **100003** successfully generated an alert.

Confirmed the alert in:

- alerts.json
- Wazuh Dashboard

### Screenshot

**65 – Custom Rule 100003 Triggered**

---

## 8. Configured Active Response

Created a custom Active Response command.

Registered:

```
demo-active-response.sh
```

Configured Active Response to trigger when Rule **100003** is detected.

### Screenshot

**66 – Active Response Configured for Rule 100003**

---

## 9. Created a Custom Active Response Script

Developed a custom shell script:

```
demo-active-response.sh
```

The script writes execution details into:

```
/var/ossec/logs/demo-active-response.log
```

Manual execution successfully produced log entries.

Example output:

```
Custom Active Response Executed
Date:
User:
Arguments:
```

---

## Results

Successfully completed:

- Custom log monitoring
- Custom detection rule development
- Wazuh configuration validation
- Wazuh manager deployment
- Custom alert generation
- Custom Active Response configuration
- Custom Active Response script development
- Manual Active Response script testing

The complete **Detection Pipeline** was successfully validated.

```
Custom Log
      ↓
Wazuh Agent
      ↓
Rule 100003
      ↓
Alert Generated
```

The custom Active Response script was successfully created and manually tested.

Automatic invocation of the script requires additional investigation. The configuration was completed successfully, but the script was not automatically executed after the alert was generated.

This is a platform-specific integration issue rather than a detection engineering issue.

---

# Skills Learned

- Detection Engineering
- Custom Log Monitoring
- Wazuh Rule Development
- Active Response Fundamentals
- Wazuh Configuration
- Linux Log Monitoring
- Docker-based Wazuh Administration
- SOC Detection Workflow

---

# Commands Used

```bash
sudo systemctl restart wazuh-agent

sudo systemctl status wazuh-agent

sudo docker compose restart wazuh.manager

sudo docker exec single-node-wazuh.manager-1 /var/ossec/bin/wazuh-analysisd -t

echo "DEMO-SECURITY: Active Response Test $(date)" | sudo tee -a /var/log/demo-security.log

sudo docker exec single-node-wazuh.manager-1 grep "100003" /var/ossec/logs/alerts/alerts.json
```

---

# Outcome

Today I learned how Wazuh processes custom logs, applies custom detection rules, and connects them to Active Response commands. I also gained hands-on experience creating and testing a custom Active Response script while understanding how automated responses are configured in a SOC environment.