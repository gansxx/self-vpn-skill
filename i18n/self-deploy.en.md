## Languages

- English Deployment Guide: [`self-deploy.en.md`](./self-deploy.en.md)
- 中文部署文档：[`../self-deploy.md`](../self-deploy.md)
- English README: [`README.en.md`](./README.en.md)
- 中文 README：[`../README.md`](../README.md)
- License: [`../LICENSE`](../LICENSE)

# Step 1: Prerequisites
- Register an Alibaba Cloud account (skip if you already have one). If not registered, go to [Alibaba Cloud Registration](https://account.aliyun.com/register/qr_register.htm).
- If you have international payment capability (mainland China bank cards are usually not accepted for some overseas products), you can also choose AWS Lightsail. The method is basically the same.
- Other cheap VPS providers are not recommended. In practice, routes to mainland China are often poor and lack proper network optimization.

# Step 2: After registration is complete
- Go to [Alibaba Cloud SWAS Purchase Page](https://swasnext.console.aliyun.com/buy#/) to buy a VPS.
- Choose the general-purpose plan (about 28 RMB/month) and Debian as the system image (2 vCPU + 0.5 GB RAM is enough for personal VPN use).
- Choose region by your needs. Tokyo is recommended (few restrictions with decent speed). If you want early access to the latest AI products, US regions are also an option.
- Buy one month first. Decide whether to enable auto-renewal yourself. Alibaba Cloud supports unconditional refund within 5 days, so deployment failure risk is manageable.
- Open all ports in the firewall and select all TCP + UDP.
![Firewall open ports](../assets/screenshots/firewall-open-ports.png)

# Step 3: Download the client
- Based on your environment, download from [v2rayN Releases](https://github.com/2dust/v2rayN/releases). Installation reference: [Release files introduction](https://github.com/2dust/v2rayN/wiki/Release-files-introduction)
- For Windows users, download `v2rayN-windows-64-desktop.zip`
- On Windows, unzip and run `v2rayN.exe`
- For other platforms (including mobile), see installation docs in [v2rayN repository](https://github.com/2dust/v2rayN)
![v2rayN import example](../assets/screenshots/v2rayn-client-import.png)

# Step 4: Reset password on [Alibaba Cloud SWAS Instance Page](https://swasnext.console.aliyun.com/servers)
- Execute the following command to connect.
- Run this command on the remote server. Script source repo: [gansxx/net_tools](https://github.com/gansxx/net_tools)
```bash
bash <(wget -qO- https://raw.githubusercontent.com/gansxx/net_tools/main/sb.sh)
```
- Wait for script completion and copy the generated link at the end.
- Example:
```text
🚀【All-in-one aggregated subscription】Node info:
Share link
(dmxl...base64 content omitted)
```

# Step 5: Test and reminders
- `hysteria` protocol is recommended first for best experience and lowest latency.

## Test
- After pasting the link into the client, right-click and run real latency test.
![Real latency test](../assets/screenshots/client-latency-test.png)
- If latency is not `-1`, access should work normally.
![Client connected state](../assets/screenshots/client-connected.png)

## Extra reminders
- If latency is `-1` and connection fails, the firewall config in Step 2 is usually the first thing to check.
- If you need all apps (for example antigravity, cursor, and apps inside WSL) to use VPN, enable TUN mode.
- If Google cannot be opened, it is usually a routing rule issue. You can rewrite rules: keep common mainland sites as direct, proxy everything else.
- If ports suddenly become unreachable on campus or corporate networks, it is often temporary internal network blocking rather than server failure. Workarounds: wait for a while or configure port hopping.
- If problems persist, open an issue or contact `gansxxzhgo@gmail.com` for help.
