# ⚔️ Attack Simulation

## 📖 Overview

This directory documents the attack simulation activities performed during the development of the Wazuh Blue Team Detection Lab.

A Kali Linux virtual machine was used to simulate attacker behavior against the monitored Ubuntu endpoint running the Wazuh Agent. The objective was to generate realistic security events that could be detected, analyzed, and investigated through the Wazuh SIEM platform.

Rather than relying on sample logs, every alert generated in this project was produced through hands-on testing inside the lab environment.

---

# 🎯 Objectives

The attack simulations were performed to:

- Generate realistic security events
- Validate Wazuh detection capabilities
- Test custom detection rules
- Verify File Integrity Monitoring (FIM)
- Test correlation rule behavior
- Practice alert investigation using the Wazuh Dashboard
- Understand how attacker activity appears from a SOC analyst's perspective

---

# 🧪 Simulated Attack Scenarios

The following attack scenarios were executed during this project.

## 1. Failed SSH Authentication

Multiple failed SSH login attempts were generated from the Kali Linux machine by intentionally providing incorrect credentials.

Purpose:

- Generate authentication failure events
- Trigger default Wazuh SSH detection rules
- Validate custom SSH detection rules
- Observe authentication logs inside the Wazuh Dashboard

---

## 2. Successful SSH Authentication

After validating failed authentication events, successful SSH logins were performed using valid credentials.

Purpose:

- Generate successful authentication events
- Verify event collection by the Wazuh Agent
- Test custom login detection rules
- Validate event visibility inside the dashboard

---

## 3. File Integrity Monitoring (FIM)

File Integrity Monitoring was tested by performing file operations inside the monitored directory configured in Wazuh.

The following operations were performed:

- File creation
- File modification
- File deletion

Purpose:

- Verify FIM configuration
- Generate integrity monitoring alerts
- Validate built-in Wazuh FIM rules
- Understand checksum and metadata monitoring

---

## 4. Custom Security Event Generation

A custom security event containing the string:

```
DEMO-SECURITY
```

was generated on the monitored endpoint.

Purpose:

- Validate the custom Wazuh detection rule
- Verify rule matching behavior
- Confirm custom alerts appeared inside the Wazuh Dashboard

---

## 5. Correlation Rule Validation

After individual alerts were successfully generated, correlation logic was tested using multiple authentication events.

Purpose:

- Test frequency-based detection
- Validate event correlation
- Understand how Wazuh links multiple related events into higher-level alerts

---

# 🔍 Investigation Workflow

Each generated event followed the same investigation workflow:

1. Execute the simulated activity from Kali Linux.
2. Generate security events on the Ubuntu endpoint.
3. Collect logs using the Wazuh Agent.
4. Forward events to the Wazuh Server.
5. Process events through the Rules Engine.
6. Generate alerts inside the Wazuh Dashboard.
7. Investigate alert details using Threat Hunting.
8. Validate detection accuracy.

---

# 📸 Evidence

Screenshots for each attack simulation are available in the `Screenshots/` directory.

The collected evidence includes:

- Failed SSH authentication
- Successful SSH authentication
- File creation alerts
- File modification alerts
- File deletion alerts
- Custom rule validation
- Correlation rule alerts
- Threat hunting investigation
- Alert details from the Wazuh Dashboard

---

# 🛡️ Skills Demonstrated

This phase of the project demonstrates practical experience with:

- Linux system administration
- SSH authentication analysis
- Attack simulation
- SIEM alert generation
- Threat hunting
- Detection engineering
- File Integrity Monitoring (FIM)
- Wazuh custom rule validation
- Event correlation
- Security investigation

---

# 📚 Key Learning Outcomes

Through these attack simulations, I learned how attacker actions are translated into security events and processed throughout the Wazuh detection pipeline.

The exercises improved my understanding of:

- How Wazuh detects authentication events
- How File Integrity Monitoring identifies file system changes
- How custom detection rules are developed and validated
- How correlation rules combine multiple events into meaningful alerts
- How SOC analysts investigate alerts using the Wazuh Dashboard
- The complete workflow from attack execution to security investigation within a SIEM environment