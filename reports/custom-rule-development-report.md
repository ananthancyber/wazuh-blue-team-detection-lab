# 📑 Custom Detection Rule Development Report

## Overview

This report documents the development, implementation, and validation of custom detection rules in the Wazuh SIEM platform. The objective was to extend Wazuh's built-in SSH detection capabilities by creating custom rules that generate alerts for specific authentication events.

The implementation was performed in a Docker-based Wazuh 4.14.6 single-node environment. The process included analyzing existing Wazuh rules, creating custom rules, validating the configuration, troubleshooting deployment issues, and verifying successful alert generation in the Wazuh Dashboard.

This exercise demonstrates the fundamentals of detection engineering by showing how Wazuh can be customized to detect organization-specific security events beyond its default rule set.

---

# Objectives

The primary objectives of this investigation were to:

- Understand the structure of Wazuh's built-in detection rules.
- Explore how SSH authentication events are processed.
- Create custom detection rules using `local_rules.xml`.
- Deploy custom rules to the Wazuh Manager running in Docker.
- Validate the rule configuration before deployment.
- Troubleshoot configuration and permission issues.
- Verify successful alert generation within the Wazuh Dashboard.
- Modify rule severity to understand alert prioritization.

---

# Lab Environment

| Component | Description |
|-----------|-------------|
| Host OS | Windows 11 |
| Virtualization | VMware Workstation |
| SIEM Platform | Wazuh 4.14.6 (Docker Single Node) |
| Endpoint | Ubuntu 26.04 LTS |
| Attack Machine | Kali Linux |
| Detection Module | Wazuh Rule Engine |
| Configuration File | `/var/ossec/etc/rules/local_rules.xml` |

---

# Background

Wazuh includes thousands of built-in detection rules that identify common security events such as authentication failures, privilege escalation, malware activity, and system modifications.

Rather than modifying these built-in rules directly, Wazuh provides the `local_rules.xml` file for creating custom detection logic. This approach preserves the default rule set while allowing administrators to implement organization-specific detections that remain intact during upgrades.

Before creating custom rules, the built-in SSH rules were reviewed to understand how successful and failed SSH authentication events are processed.

---

# Built-in Rule Analysis

The built-in SSH rule definitions were examined inside the Wazuh Manager container.

During this analysis:

- SSH rule files were located.
- Existing SSH rule IDs were reviewed.
- Parent-child rule relationships were examined.
- Rule inheritance using `<if_sid>` was studied.

This analysis helped identify the appropriate parent rules required for custom rule development.

---

# Backup of Existing Configuration

Before making any changes, the original `local_rules.xml` file was backed up.

Creating a backup ensured that the original configuration could be restored if any errors occurred during testing.

This follows good operational practice when modifying SIEM detection logic.

---

# Custom Rule Development

Two custom detection rules were created.

## Rule 100001 – Failed SSH Authentication

The first rule extends Wazuh's authentication failure detection by referencing the built-in SSH authentication failure rule.

Key characteristics:

- Custom Rule ID: **100001**
- Parent Rule: **5716**
- Event Type: Failed SSH Authentication
- Purpose: Demonstrate creation of a basic custom detection rule.

---

## Rule 100002 – Successful SSH Login

A second rule was created to detect successful SSH login events.

The rule referenced the successful authentication parent rule and generated a custom alert whenever a successful SSH login was detected.

Key characteristics:

- Custom Rule ID: **100002**
- Parent Rule: **5715**
- Event Type: Successful SSH Authentication
- Purpose: Demonstrate custom detection of successful logins.

---

# Deploying the Rules

Since the Wazuh Manager was running inside a Docker container, the updated `local_rules.xml` file was copied into the container.

During deployment the following tasks were completed:

- Copied the updated rule file.
- Verified the file existed inside the container.
- Corrected file ownership.
- Verified file permissions.

Proper ownership was required so that the Wazuh Manager could successfully read the rule file.

---

# Rule Validation

Before restarting the Wazuh Manager, the configuration was validated using the Wazuh rule validation utility.

This step confirmed that:

- XML syntax was correct.
- Rule definitions were valid.
- Parent rule references were accepted.
- The configuration could be loaded successfully.

Validating the configuration before restarting helps prevent service failures caused by configuration errors.

---

# Troubleshooting

Several issues were encountered during development.

## Permission Issue

Initially, the Wazuh validation tool could not access the custom rule file because of incorrect ownership and permissions.

This was resolved by assigning the correct ownership to the Wazuh service account inside the Docker container.

---

## Rule Configuration Error

While extending the rule, a configuration error occurred when `frequency` and `timeframe` were added without the required correlation settings.

The validation utility reported the configuration problem, allowing the rule to be corrected before restarting the manager.

This demonstrated the importance of validating rule configurations before deployment.

---

# Manager Restart

After successful validation, the Wazuh Manager container was restarted to load the updated detection rules.

The manager restarted successfully without configuration errors, confirming that the custom rules had been loaded.

---

# Detection Validation

To verify the implementation, successful SSH authentication events were generated from the test environment.

The Wazuh Dashboard detected the custom rule and generated alerts showing:

- Rule ID
- Alert level
- Timestamp
- Agent information
- Rule description

This confirmed that the custom rule was functioning as expected.

---

# Severity Adjustment

After validating the rule, the alert level was modified to observe how changes affected alert prioritization.

The updated rule generated alerts with the new severity level after redeployment and manager restart.

This exercise demonstrated how custom rules can be tuned to better align with an organization's alerting requirements.

---

# Evidence

The following screenshots document the complete implementation process.

1. Reviewing built-in SSH rules.
2. Creating a backup of `local_rules.xml`.
3. Creating custom detection rules.
4. Copying the rule file into the Docker container.
5. Correcting file ownership and permissions.
6. Validating rule configuration.
7. Restarting the Wazuh Manager.
8. Successful alert generation in the Wazuh Dashboard.
9. Modifying rule severity.
10. Verifying the updated alert level.

---

# Technical Analysis

This investigation demonstrated several important concepts used in Wazuh detection engineering.

Rather than replacing built-in detection logic, custom rules inherit existing parsing capabilities through parent rule references such as `<if_sid>`. This approach minimizes duplication while extending detection functionality.

Running Wazuh inside Docker also introduced additional operational considerations, including file ownership, container management, and deployment of configuration files.

The use of the validation utility before restarting the manager reduced the risk of service interruptions by identifying configuration errors early in the deployment process.

---

# SOC Relevance

Developing custom detection rules is an important responsibility in many Security Operations Centers (SOCs).

Organizations often create custom rules to:

- Detect organization-specific threats.
- Improve alert quality.
- Reduce false positives.
- Implement internal security policies.
- Extend default SIEM capabilities.

Understanding how to safely create, validate, and deploy custom detection rules is a valuable skill for SOC analysts and detection engineers.

---

# Key Learning Outcomes

Through this exercise I learned how to:

- Analyze Wazuh's built-in detection rules.
- Create custom detection rules using `local_rules.xml`.
- Deploy configuration changes in a Docker-based Wazuh environment.
- Validate rule configurations before deployment.
- Troubleshoot permission and configuration issues.
- Restart the Wazuh Manager safely.
- Verify custom alerts using the Wazuh Dashboard.
- Adjust rule severity based on operational requirements.

---

# Conclusion

The custom detection rules were successfully implemented and validated within the Wazuh SIEM environment. The project demonstrated the complete lifecycle of detection engineering, including rule analysis, development, deployment, validation, troubleshooting, and alert verification.

This investigation provided practical experience in extending Wazuh's default detection capabilities while following configuration management and validation practices commonly used in Security Operations Centers.