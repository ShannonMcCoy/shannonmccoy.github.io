# Installing the Monitoring Agent on Linux (Sample Doc)

This sample document demonstrates a developer-facing infrastructure documentation.  

---

## Prerequisites

Before you begin, ensure the following:

- A supported Linux distribution (Ubuntu, Debian, CentOS, or RHEL)
- `sudo` or root access to the host
- Outbound internet access on port **443** (HTTPS)
- A valid API key from your monitoring platform

---

## Step 1: Download and Run the Install Script

Run the following command on the target host:

```bash
DD_API_KEY=<YOUR_API_KEY> DD_SITE="datadoghq.com" bash -c \
"$(curl -L https://s3.amazonaws.com/dd-agent/scripts/install_script.sh)"
Replace <YOUR_API_KEY> with your actual API key.
```
## What this command does

- Downloads the official install script from the vendor

- Installs the Agent and its dependencies

- Registers the Agent with your account using the API key

- Starts the Agent service

## Step 2: Verify the Agent Status

Once installation completes, verify that the Agent is running:

sudo datadog-agent status


You should see output that includes:

- collector

- forwarder

- dogstatsd

If any components are marked as CRASHED or NOT RUNNING, review the log file:

sudo less /var/log/datadog/agent.log

## Step 3: Configure Basic Tags

Tags help you group and filter metrics (for example, by environment or application).

1. Open the main configuration file:

sudo nano /etc/datadog-agent/datadog.yaml

2. Locate the tags: section and add entries such as:

tags:
  - env:production
  - role:web
  - region:us-east-1

3. Save the file and restart the Agent:

sudo systemctl restart datadog-agent

## Step 4: Confirm Data in the UI

Log into your monitoring platform’s UI and:

1. Navigate to the Infrastructure or Hosts page.
2. Confirm that your Linux host appears in the host list.
3. Check that metrics (CPU, memory, disk, etc.) are updating in near real-time.

## Uninstalling the Agent (Optional)

If you need to remove the Agent:

sudo apt-get remove datadog-agent


Or on RHEL/CentOS:

sudo yum remove datadog-agent

## Notes

This document is a sample authored to demonstrate structure, clarity, and technical depth for SRE and developer audiences.

I typically tailor the exact commands, configuration snippets, and troubleshooting sections to the target environment and toolset.
