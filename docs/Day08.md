# Day 8 – Wazuh Active Response

## Objective

Learn how Wazuh Active Response works by creating and integrating a custom Active Response script that executes automatically when a detection rule is triggered.

---

## Concepts Learned

- What Active Response is
- Difference between Detection and Response
- Wazuh Active Response workflow
- Built-in Active Response scripts
- Active Response command registration
- Active Response configuration
- Custom Bash scripting for Wazuh
- Wazuh configuration validation
- Troubleshooting Active Response execution

---

## Understanding Active Response

Active Response allows Wazuh to automatically execute predefined actions whenever a detection rule is triggered.

Typical responses include:

- Blocking IP addresses
- Restarting services
- Disabling user accounts
- Running custom scripts

Workflow:

```
Event
    ↓
Detection Rule
    ↓
Alert
    ↓
Active Response
    ↓
Automated Action
```

---

## Exploring Built-in Active Responses

Explored the Active Response directory:

```
/var/ossec/active-response/bin
```

Observed several built-in response scripts including:

- firewall-drop
- host-deny
- restart-wazuh
- disable-account
- ip-customblock
- wazuh-slack

This helped understand how Wazuh organizes executable response scripts.

---

## Creating a Custom Active Response

Created a custom script:

```
demo-active-response.sh
```

Purpose:

- Execute automatically when triggered
- Write execution details into a log file
- Demonstrate how custom automation works in Wazuh

The script records:

- Execution time
- User
- Script arguments

Output log:

```
/var/ossec/logs/demo-active-response.log
```

---

## Manual Script Testing

Before integrating with Wazuh:

- Made the script executable
- Executed it manually
- Verified log generation

This confirmed:

- Script permissions
- Successful execution
- Correct log creation

---

## Registering the Script

Added a new command inside:

```
wazuh_manager.conf
```

Registered:

```
demo-active-response
```

which references:

```
demo-active-response.sh
```

---

## Configuring Active Response

Configured a custom Active Response using:

- Command:
  - demo-active-response
- Location:
  - server
- Rule ID:
  - 100001

Validated configuration successfully using:

```
wazuh-analysisd -t
```

Validation returned:

```
0
```

indicating a valid configuration.

---

## Troubleshooting

During testing several issues were encountered.

### Script Compatibility

Initially used:

```
hostname
```

inside the script.

The Wazuh container image did not include the hostname utility.

Resolved by modifying the script to avoid unsupported commands.

---

### SSH Testing

Generated multiple failed SSH login attempts.

Expected:

```
Failed SSH
        ↓
Rule Triggered
        ↓
Active Response
```

However, the custom response was never executed.

---

### Investigation

Verified:

- Wazuh Manager running
- Configuration valid
- Ubuntu agent connected
- Active Response registered
- Script executable
- Manual execution successful

Further investigation showed:

- Ubuntu agent monitors **systemd-journald**
- SSH authentication failures were not present in the journal
- Therefore Wazuh never received SSH authentication events
- No detection rule was triggered
- No Active Response was executed

The issue was identified as a log collection problem rather than an Active Response configuration problem.

---

## Key Takeaways

Today demonstrated that automation depends on the complete detection pipeline.

A successful Active Response requires:

1. Event generation
2. Log collection
3. Rule matching
4. Alert generation
5. Active Response execution

Failure at any earlier stage prevents automated response execution.

---

## Skills Gained

- Wazuh Active Response
- Detection vs Response concepts
- Bash scripting
- Wazuh configuration
- Linux permissions
- Wazuh validation
- Debugging automation pipelines
- Root cause analysis