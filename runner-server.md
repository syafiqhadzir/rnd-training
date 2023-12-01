<!-- omit in toc -->
# ![Runner Server](https://gitlab.msu.edu/uploads/-/system/project/avatar/6141/gitlab-ci-cd-logo_2x.png)

[Runner Server](https://docs.gitlab.com/runner/) is an application that works with GitLab CI/CD to run jobs in a pipeline.

<!-- omit in toc -->
## Table of Contents

- [System Requirements](#system-requirements)
  - [Operating System](#operating-system)
  - [Node.js](#nodejs)
  - [CPU](#cpu)
  - [Memory](#memory)
- [Runner Server](#runner-server)
  - [Step 1: Connect using SSH](#step-1-connect-using-ssh)
  - [Step 2: Install GitLab Runner](#step-2-install-gitlab-runner)
  - [Step 3: Install Dependencies](#step-3-install-dependencies)

## System Requirements

### Operating System

Users are recommended to use 64-bit Debian flavoured **Linux** operating system.

1. Ubuntu 20.04 and above.
2. Debian 8 and above.

### Node.js

Cypress is running using Node, we recommend Node.js **20.x** and above.

**Note:** Cypress generally aligns with Node's release schedule.

### CPU

- 2 CPUs minimum to run Cypress
- 1 additional CPU if video recording is enabled
- 1 additional CPU per process you run outside of Cypress, such as:
  - App server (frontend)
  - App server (backend)
  - App database
  - Any additional infrastructure (Redis, Kafka, etc..) 0193086449

### Memory

4GB minimum, 8GB+ for longer test runs.

## Runner Server

### Step 1: Connect using SSH

Open terminal and execute the following command:-

```bash
ssh {username}@{remote_host}
```

### Step 2: Install GitLab Runner

To install GitLab Runner, we need to add the official GitLab repository for Ubuntu:-

```bash
curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh" | sudo bash
```

Install the latest version of GitLab Runner by using:-

```bash
sudo apt-get install gitlab-runner
```

**Note:** If you want to use the Docker executor, make sure to install Docker **before** using GitLab Runner.

### Step 3: Install Dependencies

Users should have the required dependencies installed on the server for the runner to execute Cypress jobs properly.

```bash
apt-get install libgtk2.0-0 libgtk-3-0 libgbm-dev libnotify-dev libnss3 libxss1 libasound2 libxtst6 xauth xvfb
```
