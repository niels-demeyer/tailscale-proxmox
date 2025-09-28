# Tailscale Proxmox LXC

A script to easily install Tailscale in Proxmox LXC containers.

## Features

- Automatically configures LXC container for Tailscale support
- Installs Tailscale in the selected container
- Handles DNS resolution issues automatically
- Provides interactive container selection with validation
- Tags containers for easy identification

## Usage

Run the script directly from GitHub:

```bash
bash <(curl -s https://raw.githubusercontent.com/niels-demeyer/tailscale-proxmox/main/tailscale-lxc.sh)
```

Or download and run locally:

```bash
wget https://raw.githubusercontent.com/niels-demeyer/tailscale-proxmox/main/tailscale-lxc.sh
chmod +x tailscale-lxc.sh
./tailscale-lxc.sh
```

## Requirements

- Must be run on the Proxmox VE host (not inside an LXC container)
- Requires root privileges
- LXC containers must be created before running the script

## What it does

1. Lists all available LXC containers
2. Allows you to select which container to configure
3. Adds necessary device permissions to the container configuration
4. Mounts `/dev/net/tun` in the container
5. Installs Tailscale package in the selected container
6. Tags the container with "tailscale" for identification

## After installation

1. Reboot the container
2. Run `tailscale up` inside the container to activate and authenticate
