# 📑 Security Investigation Reports

## 📖 Overview

This folder contains the security investigation reports created during the **Wazuh Blue Team Detection Lab**. Each report documents a specific security scenario that was implemented, detected, investigated, and validated using Wazuh 4.14.6.

Rather than simply confirming that alerts were generated, these reports follow a structured investigation approach similar to the workflow performed by Security Operations Center (SOC) analysts. Each investigation explains the objective, implementation, detection process, technical analysis, and the lessons learned throughout the project.

Together, these reports demonstrate practical experience in configuring security monitoring, developing custom detection rules, investigating alerts, and understanding core SIEM operations.

---

# 🎯 Objectives

The reports in this folder were created to:

- Document the implementation and validation of Wazuh security features.
- Demonstrate practical security event investigation.
- Validate custom detection rules and alert generation.
- Understand how Wazuh processes and correlates security events.
- Practice documenting security investigations using a structured methodology.
- Build a portfolio that reflects practical Blue Team and SOC analyst skills.

---

# 📂 Investigation Reports

| Report | Description |
|---------|-------------|
| **File Integrity Monitoring (FIM) Investigation** | Documents the configuration of Wazuh Syscheck and the investigation of file creation, modification, and deletion events. |
| **Custom Detection Rule Development** | Covers the analysis of built-in SSH rules, development of custom detection rules, deployment, validation, and alert verification. |
| **Correlation Rule Investigation** | Explains the implementation of a custom correlation rule using `if_matched_sid`, `frequency`, and `timeframe` to detect repeated SSH login events. |
| **Active Response Configuration Investigation** | Documents the exploration of Wazuh's Active Response framework, including built-in scripts, configuration files, and command definitions. |

---

# 🔍 Investigation Methodology

Although each investigation focuses on a different Wazuh capability, the reports follow a consistent workflow:

1. Define the objective.
2. Configure or implement the required feature.
3. Generate or simulate the relevant security event.
4. Validate the configuration.
5. Investigate the generated alerts using the Wazuh Dashboard.
6. Analyze the results and document key findings.
7. Summarize lessons learned and SOC relevance.

This methodology reflects a structured approach to security monitoring and incident investigation while maintaining consistency across all project documentation.

---

# 🛠️ Technologies Used

The investigations were performed using the following technologies:

| Technology | Purpose |
|------------|---------|
| Wazuh 4.14.6 | SIEM and XDR platform |
| Docker | Containerized Wazuh deployment |
| Ubuntu 26.04 LTS | Monitored endpoint |
| Kali Linux | Attack simulation |
| VMware Workstation | Virtualization platform |
| Wazuh Dashboard | Alert monitoring and investigation |

---

# 📚 Key Learning Outcomes

Completing these investigations provided practical experience in:

- Configuring and validating File Integrity Monitoring (FIM).
- Developing and deploying custom Wazuh detection rules.
- Understanding parent-child rule relationships using `if_sid`.
- Building correlation rules with `if_matched_sid`, `frequency`, and `timeframe`.
- Investigating security alerts using the Wazuh Dashboard.
- Understanding the architecture of Wazuh Active Response.
- Troubleshooting configuration and deployment issues in a Docker-based environment.
- Documenting technical investigations using a structured SOC reporting approach.

---

# 🎯 Conclusion

These investigation reports represent the practical implementation and validation of key Wazuh capabilities within a home lab environment. Together, they demonstrate the complete workflow of configuring security monitoring, generating security events, validating detections, investigating alerts, and documenting findings.

The knowledge and hands-on experience gained through these investigations strengthened my understanding of SIEM operations, detection engineering, and security monitoring workflows commonly used by Blue Team and SOC analysts.