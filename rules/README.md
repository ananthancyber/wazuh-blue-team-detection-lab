# 🛡️ Custom Detection Rules

## 📖 Overview

This directory contains the custom Wazuh detection rules developed during the Wazuh Blue Team Detection Lab.

The purpose of this phase was to understand how the Wazuh Rules Engine processes security events, extend the default detection capabilities using custom rules, and validate the generated alerts through real attack simulations.

Instead of relying only on built-in detections, custom rules were created to identify specific authentication events, correlate repeated activity, and detect custom security logs generated within the lab environment.

---

# 🎯 Objectives

The custom rules were developed to:

- Understand the Wazuh Rules Engine
- Learn how built-in rules can be extended
- Create custom detection logic
- Implement event correlation
- Validate custom alerts inside the Wazuh Dashboard
- Gain practical experience with Detection Engineering

---

# 📂 Repository Contents

| File | Description |
|------|-------------|
| `local_rules.xml` | Custom Wazuh detection and correlation rules |
| `screenshots/` | Screenshots demonstrating rule creation, deployment, validation, and alert generation |

---

# 📋 Implemented Rules

## Rule 100001 – Failed SSH Authentication

### Purpose

Detect failed SSH authentication attempts originating from a specific IP address.

### Detection Logic

- Uses the built-in SSH authentication failure rule as its parent.
- Extends the default detection using the `if_sid` directive.
- Filters authentication failures from the configured source IP.

### Concepts Learned

- Rule inheritance
- `if_sid`
- Custom rule creation
- Alert customization

---

## Rule 100002 – Multiple Successful SSH Logins

### Purpose

Detect repeated successful SSH logins occurring within a short time period.

### Detection Logic

This correlation rule monitors successful SSH authentication events and generates an alert when:

- Five successful logins occur
- Within sixty seconds

The rule uses:

- `if_matched_sid`
- `frequency`
- `timeframe`

to correlate multiple events into a single higher-level alert.

### Concepts Learned

- Event correlation
- Frequency-based detection
- Time-based rule evaluation
- Correlation rule design

---

## Rule 100003 – Custom Security Event

### Purpose

Detect a manually generated security event containing the text:

```
DEMO-SECURITY
```

### Detection Logic

The rule uses the `<match>` directive to identify custom log entries and generate a security alert.

### Concepts Learned

- Pattern matching
- Custom log detection
- Rule validation
- Alert generation

---

# 🔧 Rule Development Workflow

The following workflow was followed while developing the custom rules:

1. Study the existing built-in Wazuh SSH rules.
2. Create a backup of the original `local_rules.xml`.
3. Develop custom detection rules.
4. Validate the XML syntax.
5. Copy the updated rule file into the Wazuh Docker container.
6. Correct file ownership and permissions.
7. Restart the Wazuh Manager.
8. Generate attack events.
9. Verify alerts inside the Wazuh Dashboard.
10. Review alert details using Threat Hunting.

---

# 🧪 Rule Validation

Each rule was validated by generating the corresponding security events inside the lab environment.

Validation included:

- Failed SSH authentication attempts
- Successful SSH authentication events
- Multiple successful logins for correlation testing
- Custom log generation using `DEMO-SECURITY`

Successful validation confirmed that:

- The expected Rule ID was triggered.
- The correct alert level was assigned.
- Detection logic executed successfully.
- Alerts appeared in the Wazuh Dashboard.
- Alert details matched the configured rule behavior.

Supporting evidence is available in the `screenshots/` directory.

---

# 🛠️ Detection Engineering Concepts

During this phase of the project, the following Wazuh concepts were explored:

- Built-in rules
- Rule inheritance
- Custom rules
- Event correlation
- Rule IDs
- Alert levels
- `if_sid`
- `if_matched_sid`
- `frequency`
- `timeframe`
- `match`
- XML rule syntax
- Rule validation
- Rule deployment

---

# 📚 Key Learning Outcomes

Developing custom detection rules provided practical experience with how Wazuh processes security events and generates alerts.

This phase improved my understanding of:

- How built-in Wazuh rules can be extended using custom logic.
- How authentication events are detected and processed.
- How correlation rules identify repeated attacker behavior.
- How custom log patterns can be detected using pattern matching.
- How detection rules are validated, deployed, and tested inside a production-style Wazuh environment.
- The complete workflow involved in designing, implementing, and verifying custom detections for a SIEM platform.