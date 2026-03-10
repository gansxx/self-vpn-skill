# Aliyun SWAS Personal VPN Workflow

Use this reference for exact URLs, commands, and troubleshooting details. Keep the main SKILL.md short and load this file only when you need the concrete steps.

## Prerequisites

- Aliyun account with payment method.
- A client device to run the VPN client (default: Windows with v2rayN).
- Willingness to pay the cloud provider directly.

## Intake Template (Reduce Back-And-Forth)

Ask the user to provide this in one message before starting:

```text
Client OS:
Aliyun account ready: yes/no
Preferred region: Tokyo/US/other
SWAS instance purchased: yes/no
Public IP:
Credential sharing allowed with agent: yes/no
```

## Step 1: Create Or Confirm Aliyun Account

- If the user does not have an account, direct them to:
  - https://account.aliyun.com/register/qr_register.htm

## Step 2: Purchase An SWAS Instance

- Open the SWAS purchase page:
  - https://swasnext.console.aliyun.com/buy#/
- Recommended choices:
  - Plan: general-purpose entry tier (often around 28 CNY/month, confirm current price).
  - System image: Debian.
  - Region: user choice. Tokyo is a common default for speed and fewer restrictions; US regions can help with access to newer AI products.
  - Duration: 1 month (auto-renew optional).
- Firewall requirements:
  - In SWAS firewall, open all ports and select TCP+UDP all.

## Step 3: Download And Install Client

- Default client (Windows): v2rayN
  - Releases: https://github.com/2dust/v2rayN/releases
  - Release notes: https://github.com/2dust/v2rayN/wiki/Release-files-introduction
- On Windows: unzip the archive and launch `v2rayN.exe`.
- If the user is not on Windows, ask for OS and suggest a compatible client rather than guessing.

## Step 4: Reset Password, SSH, And Install

- In the SWAS console servers page, reset the instance password:
  - https://swasnext.console.aliyun.com/servers
- Ask the user to provide instance public IP.
- If the user allows credential sharing, ask for reset password and run:

```bash
bash <(wget -qO- https://raw.githubusercontent.com/gansxx/net_tools/main/sb.sh)
```

- If the user does not allow credential sharing, ask them to SSH from their terminal and run the same command, then paste only the final share link line(s).
- The script prints multiple outputs. Return only the share link line(s) to the user. The line usually starts with one of:
  - `vless://`
  - `vmess://`
  - `hysteria2://`
  - `tuic://`

## Step 5: Client Import And Testing

- In v2rayN, import the share link and test latency.
- Recommend testing the `hysteria` / `hysteria2` profile first if available.
- If latency shows `-1`, start with firewall checks and IP/password confirmation.
- Treat setup as completed only when latency is not `-1` and one real website test succeeds.

## Troubleshooting Checklist

- Firewall not open or missing UDP: re-check SWAS firewall settings.
- Google or other sites not opening: client rule set issue; enable TUN mode for system-wide routing.
- Campus or corporate network blocks: possible port blocking on local network. Wait and retry or switch ports.
- If still blocked, ask the user whether they can provide more logs or prefer to contact support.

## Support Escalation

- For unresolved issues, instruct the user to contact: gansxxzhgo@gmail.com
