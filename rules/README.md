# 🛡️ Custom Detection Rules

## 📖 Overview

This folder contains the custom Wazuh detection rules created and tested during the Wazuh Blue Team Detection Lab.

The objective was to understand how Wazuh processes security events, create custom detection logic, and validate alerts using simulated attack activities.

---

## 📂 Files

| File | Description |
|------|-------------|
| `local_rules.xml` | Custom Wazuh detection and correlation rules |
| `screenshots/` | Screenshots showing successful rule validation |

---

## 📋 Custom Rules

### Rule 100001 – Failed SSH Authentication

- Detects failed SSH authentication attempts from a specific IP address.
- Demonstrates basic custom rule creation using `if_sid`.

### Rule 100002 – Multiple Successful SSH Logins

- Correlation rule that detects five successful SSH logins within 60 seconds.
- Uses `if_matched_sid`, `frequency`, and `timeframe` to identify repeated events.

### Rule 100003 – Custom Security Event

- Detects log entries containing the text `DEMO-SECURITY`.
- Demonstrates custom log matching using the `<match>` tag.

---

## 🧪 Validation

Each rule was tested by generating the corresponding events and verifying that:

- The expected Rule ID was triggered.
- Alerts appeared in the Wazuh Dashboard.
- Alert details matched the configured detection logic.

Validation screenshots are available in the `screenshots/` folder.

---

## 🎯 Key Learning Outcomes

- Created and tested custom Wazuh detection rules.
- Implemented correlation-based detection logic.
- Understood rule inheritance using `if_sid`.
- Gained practical experience with Wazuh Detection Engineering.