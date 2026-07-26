# 📑 Active Response Configuration Investigation Report

## Overview

This report documents the investigation and initial configuration of Wazuh's Active Response framework within the Blue Team Detection Lab.

Active Response is a feature that enables Wazuh to automatically execute predefined actions when specific security rules are triggered. These actions can include blocking IP addresses, disabling user accounts, terminating malicious processes, or running custom response scripts.

The objective of this exercise was to understand how Active Response is implemented in Wazuh, explore the available response scripts, review the default configuration, and prepare the environment for future automation.

---

# Objectives

The objectives of this investigation were to:

- Understand the purpose of Active Response in Wazuh.
- Explore the built-in response scripts.
- Review the default Active Response configuration.
- Examine command definitions used by the Wazuh Manager.
- Understand how response actions are linked to detection rules.
- Prepare the environment for future Active Response implementation.

---

# Lab Environment

| Component | Description |
|-----------|-------------|
| Host OS | Windows 11 |
| Virtualization | VMware Workstation |
| SIEM Platform | Wazuh 4.14.6 (Docker Single Node) |
| Endpoint | Ubuntu 26.04 LTS |
| Wazuh Manager | Docker Container |
| Feature Investigated | Active Response |

---

# Background

Security monitoring platforms traditionally generate alerts when suspicious activity is detected. While alerts provide visibility, they still require a security analyst to investigate and respond manually.

Active Response extends this capability by allowing Wazuh to automatically execute predefined actions after specific detection rules are triggered.

Examples include:

- Blocking malicious IP addresses.
- Disabling compromised accounts.
- Terminating suspicious processes.
- Restarting services.
- Executing custom response scripts.

This capability helps reduce response time and supports automated containment of security incidents.

---

# Investigation Process

The investigation focused on understanding how Active Response is implemented within Wazuh rather than immediately enabling automatic execution.

The following activities were performed:

- Explored the Active Response directory.
- Reviewed available built-in response scripts.
- Examined the default manager configuration.
- Reviewed predefined command definitions.
- Studied how commands are associated with detection rules.

This provided a foundational understanding of Wazuh's automated response architecture.

---

# Built-in Response Scripts

The Active Response directory was inspected to identify the scripts included with the default Wazuh installation.

Several built-in scripts were observed, including examples for:

- Firewall management
- Host blocking
- Route management
- Account management
- Service restart operations

These scripts demonstrate the range of automated actions that Wazuh can perform when properly configured.

---

# Configuration Review

The Wazuh Manager configuration file was examined to understand how Active Response is configured.

During this review, the following components were analyzed:

- Command definitions
- Executable paths
- Timeout settings
- Global configuration options
- Local configuration sections

Understanding these settings is essential before enabling automated response actions in a production environment.

---

# Command Definitions

The built-in command definitions were reviewed to understand how Wazuh executes Active Response actions.

Each command specifies:

- Command name
- Executable script
- Execution permissions
- Timeout behavior

These definitions provide the interface between detection rules and the corresponding response scripts.

---

# Configuration Preparation

The manager configuration was opened and reviewed in preparation for enabling Active Response.

Rather than immediately enabling automatic execution, the configuration was carefully examined to understand the available options and avoid introducing unintended behavior into the lab environment.

This step emphasized understanding the configuration before making operational changes.

---

# Findings

The investigation confirmed that Wazuh includes a comprehensive Active Response framework by default.

Key observations include:

- Multiple built-in response scripts are available.
- Active Response behavior is controlled through manager configuration.
- Commands and response actions are modular.
- Automated response can be associated with specific detection rules.

The lab environment was successfully prepared for future implementation of automated response actions.

---

# Evidence

The following screenshots document the investigation process:

1. Built-in Active Response scripts.
2. Default Active Response configuration.
3. Built-in command definitions.
4. Wazuh Manager configuration review.

---

# Technical Analysis

Active Response represents the transition from passive monitoring to automated incident response.

Unlike traditional SIEM alerts that require analyst intervention, Active Response can automatically execute predefined actions when detection rules meet configured conditions.

Understanding the configuration architecture before enabling automated actions is important because incorrect response rules could unintentionally disrupt legitimate services or user activity.

The investigation provided insight into how Wazuh separates detection logic, command definitions, and response execution, making the framework flexible and extensible.

---

# SOC Relevance

Automated response capabilities are widely used in modern Security Operations Centers to reduce response times and improve operational efficiency.

Common use cases include:

- Blocking malicious IP addresses.
- Temporarily disabling compromised accounts.
- Preventing brute-force attacks.
- Isolating affected endpoints.
- Executing automated containment procedures.

Although this project focused on understanding the framework rather than deploying automatic responses, the investigation established the knowledge required for future implementation.

---

# Key Learning Outcomes

Through this investigation I learned how to:

- Understand the purpose of Active Response in Wazuh.
- Identify built-in response scripts.
- Review manager configuration files.
- Analyze command definitions.
- Understand how detection rules can trigger automated actions.
- Prepare a Wazuh environment for future Active Response deployment.

---

# Limitations

Automatic execution of Active Response actions was not fully implemented during this project.

Instead, the focus was placed on understanding the architecture, configuration, and operational workflow required for future implementation.

This approach ensured a solid understanding of the feature before enabling automated security actions.

---

# Conclusion

This investigation provided a practical understanding of Wazuh's Active Response framework and its role in automated incident response. By exploring the built-in scripts, reviewing configuration files, and analyzing command definitions, the project established a strong foundation for implementing automated response actions in future enhancements of the lab.

Although automatic execution was not enabled within the scope of this project, the investigation demonstrates an understanding of the components required to support security automation in a Wazuh-based SOC environment.