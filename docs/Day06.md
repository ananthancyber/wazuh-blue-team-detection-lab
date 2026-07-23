# Day 6 - Creating a Custom Wazuh Detection Rule

## Objective

Learn how the Wazuh detection engine works by exploring built-in rules and creating a custom detection rule for successful SSH logins.

---

## Topics Covered

- Wazuh detection pipeline
- Decoders vs Rules
- Built-in rule structure
- Rule hierarchy using `if_sid`
- Custom rule creation
- Docker container configuration
- File permissions and ownership
- Configuration validation
- Triggering and verifying custom alerts

---

## Understanding the Detection Pipeline

Learned how Wazuh processes security events:

User Activity
→ Log Generated
→ Wazuh Agent Collects Log
→ Decoder Parses Log
→ Rule Evaluates Event
→ Alert Generated
→ Alert Stored in Indexer
→ Displayed in Wazuh Dashboard

---

## Exploring Built-in Rules

Entered the Wazuh Manager Docker container and explored:

```
/var/ossec/ruleset/rules
```

Learned that:

- Built-in rules are organized into multiple XML files.
- Rules are grouped by service (SSH, Syslog, PAM, etc.).
- Built-in rules should not be modified directly.

Also explored:

```
/var/ossec/etc
```

and identified the location for custom rules:

```
/var/ossec/etc/rules/
```

---

## Analyzing Built-in SSH Rules

Inspected the SSH rule file:

```
0095-sshd_rules.xml
```

Analyzed Rule ID **5715**.

Key observations:

- Rule ID: 5715
- Level: 3
- Description:
  "sshd: authentication success."
- Uses `if_sid` to build rule hierarchy.

Learned how Wazuh evaluates parent and child rules.

---

## Creating a Custom Rule

Created a new custom rule inside:

```
/var/ossec/etc/rules/local_rules.xml
```

Rule created:

```xml
<rule id="100002" level="7">
  <if_sid>5715</if_sid>
  <description>Custom Rule: Successful SSH login detected.</description>
  <group>local,authentication_success,</group>
</rule>
```

Purpose:

Generate a custom alert whenever a successful SSH login occurs.

---

## Configuration Backup

Created a backup before making modifications:

```
local_rules.xml.bak
```

This follows production best practices for configuration management.

---

## Troubleshooting

Encountered a permission issue after copying the updated rule into the Docker container.

Error:

```
Permission denied
```

Investigation revealed that the copied file was owned by UID/GID `1000:1000` instead of the `wazuh` user.

Resolved by:

- Identifying the Wazuh user inside the container.
- Changing ownership:

```bash
chown wazuh:wazuh /var/ossec/etc/rules/local_rules.xml
```

Validated the configuration successfully afterwards.

---

## Reloading Wazuh

Restarted the Wazuh Manager container:

```bash
sudo docker restart single-node-wazuh.manager-1
```

Confirmed the manager started successfully.

---

## Testing the Custom Rule

Generated a successful SSH login event by connecting to the Ubuntu host over SSH.

Verified the alert inside the Wazuh Dashboard.

Result:

- Rule ID: 100002
- Level: 7
- Description:
  "Custom Rule: Successful SSH login detected."

The custom detection rule worked successfully.

---

## Skills Learned

- Understanding Wazuh detection workflow
- Rule hierarchy (`if_sid`)
- Reading built-in detection rules
- Writing custom XML detection rules
- Docker container management
- Linux file ownership and permissions
- Configuration validation
- Detection testing
- Wazuh Threat Hunting

---

## Screenshots

29-built-in-rules-and-config-directory.png

30-built-in-sshd-rule-analysis.png

31-local-rules-backup-created.png

32-custom-rule-added.png

33-custom-rule-copied-to-container.png

34-wazuh-manager-restarted.png

35-custom-rule-triggered.png

---

## Outcome

Successfully created, deployed, validated, and tested a custom Wazuh detection rule.

This demonstrated how to extend Wazuh's built-in detection capabilities using custom XML rules and verified the alert generation through the Wazuh Dashboard.