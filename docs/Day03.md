# Day 03 – Registering and Monitoring the First Endpoint

## Objective

Install the Wazuh Agent on the Ubuntu host, register it with the Wazuh Manager, and investigate the first security events.

---

## Tasks Completed

- Verified the Wazuh Manager was running
- Verified the Manager was listening on port 1514
- Generated Wazuh Agent installation commands
- Installed the Wazuh Agent
- Enabled and started the Wazuh Agent service
- Verified the agent was running
- Registered the Ubuntu endpoint with the Wazuh Manager
- Confirmed the endpoint appeared in the Wazuh Dashboard
- Generated security events using Linux commands
- Investigated events using the Threat Hunting module

---

## Commands Used

```bash
cd ~/wazuh-docker/single-node

sudo docker compose ps

sudo ss -tulpn | grep 1514

cat /etc/os-release

uname -m

sudo systemctl daemon-reload

sudo systemctl enable wazuh-agent

sudo systemctl start wazuh-agent

sudo systemctl status wazuh-agent

sudo ls /root
```

---

## Concepts Learned

- Wazuh Agent
- Endpoint Registration
- Manager Communication
- Threat Hunting
- Security Events
- PAM Authentication
- Rule IDs
- Rule Levels
- Security Monitoring Workflow

---

## Event Investigation

### Event 1

- Rule ID: 5501
- Rule Level: 3
- Description: PAM: Login session opened

### Event 2

- Rule ID: 510
- Rule Level: 7
- Description: Host-based anomaly detection event

### Event 3

- Rule ID: 5402
- Rule Level: 3
- Description: Successful `su`

### Event 4

- Rule ID: 5502
- Rule Level: 3
- Description: PAM: Login session closed

---

## Skills Practiced

- Linux Administration
- Docker-based Wazuh Deployment
- Endpoint Monitoring
- SIEM Operations
- Log Analysis
- Event Investigation
- Threat Hunting

---

## Screenshots

- 12-manager-running.png
- 13-agent-deployment-page.png
- 14-wazuh-agent-running.png
- 15-agent-connected.png
- 16-first-security-event.png
- 17-host-based-anomaly-details.png

---

## Result

Successfully connected the Ubuntu endpoint to Wazuh and verified that security events were collected, analyzed, and displayed in the Threat Hunting dashboard.