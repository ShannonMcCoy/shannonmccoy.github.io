# Installing the Monitoring Agent on Linux (Sample Doc)

This sample document demonstrates my style for developer-facing infrastructure documentation.  
It is modeled after Datadog-style installation and configuration guides.

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
