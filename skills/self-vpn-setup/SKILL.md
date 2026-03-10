---
name: self-vpn-setup
description: Guide Codex to help users provision a personal VPN on Aliyun SWAS and configure a client (primarily v2rayN). Use when a user asks to set up a self-hosted VPN/proxy, wants a dedicated IP for AI subscriptions, needs higher stability/privacy than shared VPNs, or requests step-by-step Aliyun SWAS provisioning and client setup.
---

# Self VPN Setup

## Overview

Provide a step-by-step workflow to help the user buy an Aliyun SWAS instance, install the VPN stack with a one-line script, and configure their client. Keep the flow interactive by confirming prerequisites, OS, and credentials before running commands.

## Workflow

### 0. Collect Required Inputs First

- Request a single reply containing: client OS, Aliyun account status, target region, instance public IP, and whether the user allows credential sharing.
- If the user does not want to share credentials, switch to "user-runs-command" mode and provide exact copy-paste commands.

### 1. Qualify And Prepare

- Confirm the user wants a self-hosted VPN and understands they will pay the cloud provider directly.
- Ask which OS the user will run the client on. Default workflow assumes Windows with v2rayN.
- Ask whether the user already has an Aliyun account and a payment method.

### 2. Provision The Server

- Direct the user to the Aliyun SWAS purchase page and walk them through instance selection.
- Ensure the user opens all required ports in the SWAS firewall (TCP+UDP all).
- Ask for the instance public IP after purchase.

### 3. Install The VPN Stack

- Ask the user to reset the instance password in the SWAS console.
- If credentials are shared, use SSH to connect and run the install script.
- If credentials are not shared, instruct the user to run the same command locally and paste back the final share link line(s).
- Capture the output and return only the final share link line(s) to the user.

### 4. Configure The Client

- Provide the correct client download link for the user OS.
- For v2rayN, instruct how to import the share link and test latency.

### 5. Validate And Troubleshoot

- Recommend testing with the hysteria protocol first if present.
- If latency is -1 or no connectivity, check firewall settings and IP/password correctness first.
- If Google or other sites fail, advise checking client rules and enabling TUN mode.
- If campus/corporate networks block ports, suggest waiting or switching ports.
- Declare setup success only when latency is not `-1` and at least one target site is reachable.

## Reference

Follow the detailed workflow and troubleshooting checklist in `references/workflow.md`. Load it when you need the exact URLs, copy-paste commands, or testing steps.
