# 📑 Correlation Rule Investigation Report

## Overview

This report documents the design, implementation, troubleshooting, and validation of a custom correlation rule in Wazuh. Unlike basic detection rules that generate an alert for every matching event, correlation rules analyze multiple related events occurring within a specified time window before triggering an alert.

The objective of this exercise was to detect repeated successful SSH login events within a short period by using Wazuh's correlation capabilities. This demonstrates how SIEM platforms can identify suspicious behavioral patterns instead of isolated security events.

The implementation was completed in a Docker-based Wazuh 4.14.6 environment and included rule development, configuration validation, troubleshooting, deployment, and verification through the Wazuh Dashboard.

---

# Objectives

The objectives of this investigation were to:

- Understand the difference between basic detection rules and correlation rules.
- Create a custom correlation rule using Wazuh.
- Configure event frequency and time window conditions.
- Learn the purpose of the `<if_matched_sid>` element.
- Validate rule syntax before deployment.
- Troubleshoot configuration errors.
- Verify successful alert generation in the Wazuh Dashboard.

---

# Lab Environment

| Component | Description |
|-----------|-------------|
| Host OS | Windows 11 |
| Virtualization | VMware Workstation |
| SIEM Platform | Wazuh 4.14.6 (Docker Single Node) |
| Endpoint | Ubuntu 26.04 LTS |
| Attack Machine | Kali Linux |
| Detection Engine | Wazuh Rule Engine |

---

# Background

Traditional detection rules generate an alert whenever a single event matches specific conditions.

Correlation rules extend this capability by combining multiple related events into a single detection. Instead of identifying one event, they detect patterns of activity that may indicate suspicious behavior.

In Wazuh, correlation rules commonly use:

- `if_matched_sid`
- `frequency`
- `timeframe`

These parameters allow the rule engine to determine how many matching events must occur within a defined period before generating an alert.

---

# Rule Design

The custom rule was created using the existing successful SSH authentication rule as the parent event.

The rule monitored successful SSH login events and generated an alert only after multiple successful logins occurred within the configured time window.

Key configuration elements included:

| Parameter | Purpose |
|----------|---------|
| Rule ID | 100002 |
| Parent Rule | 5715 |
| if_matched_sid | References the successful SSH login rule |
| Frequency | Number of matching events required |
| Timeframe | Time window for correlation |

This approach reduces alert noise by focusing on repeated activity rather than isolated login events.

---

# Initial Configuration Error

During implementation, the rule was modified by adding the `frequency` and `timeframe` options.

When the configuration was validated, Wazuh reported an error indicating that correlation options require the use of `if_matched_sid`.

The validation utility produced an error similar to:

> Invalid use of frequency/context options. Missing if_matched_sid.

Rather than restarting the manager with an invalid configuration, the issue was investigated and corrected.

This demonstrated the importance of validating rule changes before deployment.

---

# Troubleshooting

After reviewing the Wazuh documentation and existing rule structure, the rule was updated by replacing the parent rule reference with the appropriate correlation reference.

The corrected rule included:

- `if_matched_sid`
- `frequency`
- `timeframe`

The configuration was validated again using the Wazuh analysis utility.

This time, the validation completed successfully without errors.

---

# Deployment

Following successful validation:

- The updated rule file was copied into the Wazuh Manager container.
- File ownership was verified.
- The Wazuh Manager container was restarted.
- The manager loaded the updated rule configuration successfully.

This completed the deployment phase of the correlation rule.

---

# Validation

To verify the rule, multiple successful SSH login events were generated within the configured time window.

The Wazuh Dashboard generated a correlation alert after the required number of events occurred.

The generated alert confirmed:

- Rule ID **100002**
- Alert level **3**
- Multiple successful SSH login events detected
- Correct event correlation

This demonstrated that the rule behaved as expected.

---

# Evidence

The implementation process is documented through the following screenshots:

1. Initial correlation rule configuration.
2. Validation error caused by missing `if_matched_sid`.
3. Updated rule configuration.
4. Successful configuration validation.
5. Wazuh Manager restart.
6. Dashboard showing correlation alert.
7. Final alert verification.

---

# Technical Analysis

This investigation highlights an important distinction between event detection and event correlation.

A basic detection rule generates one alert for every matching event.

A correlation rule evaluates the relationship between multiple events before producing a single alert.

This technique provides several operational advantages:

- Reduces repetitive alerts.
- Improves analyst efficiency.
- Detects behavioral patterns.
- Supports higher-level threat detection.

The investigation also demonstrated how Wazuh enforces rule validation by preventing invalid correlation configurations from being deployed.

---

# SOC Relevance

Correlation rules play a significant role in Security Operations Centers because many attacks are identified through behavioral patterns rather than individual events.

Examples include:

- Multiple authentication attempts.
- Repeated privilege escalation.
- Port scanning.
- Brute-force activity.
- Credential abuse.
- Lateral movement.

By correlating multiple related events, SIEM platforms reduce false positives and help analysts focus on meaningful security incidents.

---

# Key Learning Outcomes

Through this investigation I learned how to:

- Differentiate between detection rules and correlation rules.
- Implement event correlation using `if_matched_sid`.
- Configure frequency and timeframe conditions.
- Validate Wazuh rule configurations safely.
- Troubleshoot correlation rule errors.
- Deploy updated rules in a Docker-based Wazuh environment.
- Verify correlation alerts in the Wazuh Dashboard.

---

# Conclusion

The custom correlation rule was successfully implemented, validated, and tested within the Wazuh SIEM environment. The project demonstrated how multiple successful SSH authentication events can be correlated into a single meaningful alert, improving detection quality while reducing unnecessary alert volume.

This exercise strengthened my understanding of SIEM rule development, event correlation, and troubleshooting techniques commonly used in Security Operations Centers.