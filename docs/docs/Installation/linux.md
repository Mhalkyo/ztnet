---
id: debian_11
title: Standalone Debian & Ubuntu
slug: /installation/linux
description: Debian 11 installation instructions for ZTNET
sidebar_position: 2
---


## System Requirements

To build and run the application, your system should meet the following minimum requirements:

- **Memory**: At least 1GB of RAM
- **CPU**: At least 1 CPU Core

# Install or update ztnet 

Login as **root** on your system, then install `curl`, `lsb-release` and `sudo` if it is not already installed:

```bash
apt update && apt install -y sudo curl lsb-release
```

To continue install ztnet on Debian or Ubuntu, run the following command:

```bash
curl -s http://install.ztnet.network | sudo bash
```

## Install a specific version
If you want to rollback or install a previous version, you can specify a version like this:

```bash
curl -s http://install.ztnet.network | sudo bash -s -- -v v0.4.2
```

## Script Functionality Overview

This script executes the following steps:

1. **Prerequisites**: Installs Node.js version 18 and PostgreSQL.
2. **Clone Repository**: Clones the `ztnet` repository into a temporary directory (`/tmp/ztnet`).
3. **Install Dependencies**: Installs the necessary package dependencies.
4. **Build Artifacts**: Builds the required artifacts and copies them to `/opt/ztnet`.
5. **Systemd Service**: Sets up a systemd service to auto-start `ztnet` during system boot.

### Monitoring Service Status

To check the status of the `ztnet` service, run the following command:

```bash
sudo systemctl status ztnet
```

### Starting the Service (default)

To start the `ztnet` service, run the following command:

```bash
sudo systemctl start ztnet
```

### Stopping the Service

To stop the `ztnet` service, run the following command:

```bash
sudo systemctl stop ztnet 
```

### Enable at boot (default)

To stop the `ztnet` service, run the following command:

```bash
sudo systemctl enable ztnet
```

### Disable at boot

To stop the `ztnet` service, run the following command:

```bash
sudo systemctl disable ztnet
```

## Testing other branches
If you want to test out a specific branch of ztnet, you can specify the branch like this, change `main` to the branch you want to test:

```bash
curl http://install.ztnet.network | sudo bash -s -- -b main
```

## Uninstalling ztnet
This will remove the ztnet systemd service and the ztnet folder.  
Postgres, Git and Node.js will not be removed.
```bash
curl -s http://install.ztnet.network | sudo bash -s -- -u
```

### Development

The installation scripts is available in the [install.ztnet](https://github.com/sinamics/ztnet/tree/main/install.ztnet) folder in main repository.

## Ztnet Environment Variables
See [Environment Variables](/installation/options#environment-variables) for more information.