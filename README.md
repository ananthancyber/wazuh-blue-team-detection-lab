# 🛡️ Wazuh Blue Team Detection Lab

A hands-on cybersecurity home lab built using Ubuntu, Docker, and Wazuh SIEM/XDR to learn Blue Team operations, log monitoring, threat detection, and incident investigation.

---

## 📌 Project Objective

Build a practical SOC (Security Operations Center) lab from scratch and gain hands-on experience with:

- SIEM (Security Information and Event Management)
- XDR (Extended Detection and Response)
- Docker
- Linux Administration
- Threat Detection
- Log Analysis
- Incident Investigation

---

## 🛠️ Technologies Used

- Ubuntu 26.04 LTS
- Docker Engine
- Docker Compose
- Wazuh 4.14.6
- VMware Workstation
- Git
- GitHub
- VS Code

---

## 📂 Project Structure

```text
Project-01-Wazuh-Blue-Team-Lab/
│
├── architecture/
├── attack-simulation/
├── diagrams/
├── docs/
│   ├── Day01.md
│   └── Day02.md
├── reports/
├── rules/
├── screenshots/
├── scripts/
└── README.md
```

---

## ✅ Progress

### Day 1
- Ubuntu VM setup
- VMware Tools installation
- Git & GitHub setup
- Project folder structure
- Documentation created

### Day 2
- Docker installed
- Docker Compose installed
- Wazuh Docker deployment
- TLS certificates generated
- Wazuh Manager deployed
- Wazuh Indexer deployed
- Wazuh Dashboard deployed
- Successfully logged into Wazuh Dashboard

### Day 3

- Verified Wazuh Manager connectivity
- Installed and configured the Wazuh Agent
- Registered the Ubuntu endpoint
- Verified agent communication
- Investigated security events using Threat Hunting
- Learned Wazuh rule IDs and severity levels

### Day 4

- Configured File Integrity Monitoring (FIM)
- Enabled real-time directory monitoring
- Detected file creation
- Detected file modification
- Detected file deletion
- Investigated FIM events in Threat Hunting

### Day 5

✅ Investigated Wazuh File Integrity Monitoring (FIM) alerts

- Investigated Rules 554, 550, and 553
- Analyzed alerts using Table and JSON views
- Compared file creation, modification, and deletion events
- Learned how Wazuh identifies file lifecycle activities
- Understood the role of hashes in integrity monitoring

### Day 6

✅ Learned how the Wazuh detection engine works

- Explored the Wazuh detection pipeline
- Understood Decoders and Rules
- Analyzed built-in SSH detection rules
- Learned rule hierarchy using `if_sid`
- Explored built-in rule files
- Created a custom Wazuh detection rule
- Backed up configuration before modification
- Resolved Docker file permission issues
- Validated the custom rule configuration
- Restarted the Wazuh Manager
- Triggered a successful SSH login
- Verified the custom alert (Rule ID 100002) in the Wazuh Dashboard
- Gained hands-on experience in Wazuh detection engineering

### Day 7

✅ Learned Detection Engineering and Wazuh Correlation Rules

- Understood Alert Fatigue, False Positives, and False Negatives
- Learned Detection Tuning techniques
- Tuned the custom SSH detection rule severity
- Learned correlation rules using `frequency`, `timeframe`, and `if_matched_sid`
- Implemented a threshold-based SSH login detection rule
- Configured SSH key authentication for automated testing
- Generated multiple successful SSH login events
- Validated the custom rule configuration
- Restarted the Wazuh Manager
- Verified the correlation alert (Rule ID **100002**) in the Wazuh Dashboard
- Resolved Docker file permission issues
- Troubleshot SSH public key authentication
- Gained hands-on experience with Wazuh Detection Engineering and Rule Correlation


### Day 8

✅ Learned Wazuh Active Response and Custom Response Automation

- Learned how Wazuh Active Response works
- Explored built-in Active Response scripts
- Developed a custom Active Response Bash script
- Registered a custom Wazuh command
- Configured a custom Active Response
- Validated Wazuh configuration successfully
- Tested the custom script manually
- Investigated the Active Response execution pipeline
- Troubleshot event collection and detection workflow
- Gained practical experience debugging Wazuh automation

### Day 9

✅ Learned Wazuh Active Response and Custom Detection Rules

- Configured Wazuh Agent to monitor a custom log source
- Created a custom detection rule (Rule ID **100003**)
- Generated and detected custom security events
- Validated the Wazuh Manager configuration
- Restarted the Wazuh Manager to apply changes
- Verified custom alerts in Wazuh Dashboard and alerts.json
- Created a custom Active Response script
- Registered a custom Active Response command
- Linked Active Response to the custom detection rule
- Manually tested the custom Active Response script
- Gained hands-on experience with Detection Engineering and Active Response fundamentals

---

## 📸 Project Screenshots

| Screenshot | Description |
|------------|-------------|
| 06-docker-service-running.png | Docker service verification |
| 07-docker-hello-world.png | Docker installation test |
| 08-wazuh-project-files.png | Stable Wazuh project structure |
| 08-wazuh-image-tag-error.png | Initial image tag issue |
| 08-wazuh-image-not-found-error.png | Docker image troubleshooting |
| 09-certificates-generated.png | TLS certificate generation |
| 10-wazuh-containers-running.png | Wazuh containers running |
| 11-wazuh-dashboard-home.png | Wazuh Dashboard |

---

## 🎯 Skills Demonstrated

- Linux Administration
- Docker
- Docker Compose
- SIEM Deployment
- TLS Certificate Management
- Security Monitoring
- Technical Documentation
- Git Version Control
---

## 👤 Author

**Ananthan D**

- GitHub: https://github.com/ananthancyber
- LinkedIn: https://www.linkedin.com/in/ananthan-d-ab295321b