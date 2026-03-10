# Self VPN Skill

## 概览

本仓库提供一套 AI Agent 技能与结构化步骤，帮助用户在阿里云 SWAS 上搭建个人专属 VPN 并完成客户端配置。适合希望拥有独立 IP、更高稳定性或更强控制权的用户。

## 适用人群

- 拥有 AI 订阅，希望避免共享 IP 带来的风控问题
- 对网络质量要求高且使用流量较大
- 重视隐私，希望完全掌控网络出口
- 不想依赖第三方 VPN 服务商，对第三方 VPN 缺乏信任

## 免责声明

本技能完全开源，与任何商业机构无利益关系。用户仅需向云服务商支付费用。

## 内容说明

- `plan.md`: 给人手动安装使用的完整步骤与排错说明
- `skills/self-vpn-setup/`: AI Agent 技能定义与参考资料

## AI Agent 使用

本技能可用于 OpenClaw、Claude Code 等支持加载本地技能的 AI Agent。

### 安装提示词

将下面提示词直接发给你的 AI Agent，让它自动安装并加载该技能：

```text
请从 GitHub 仓库 gansxx/self-vpn-skill 获取技能，并直接安装 skills/self-vpn-setup 到你的本地 skills 目录（例如 $CODEX_HOME/skills/self-vpn-setup）。安装后启用该技能；当用户请求搭建个人 VPN / 代理、需要阿里云 SWAS 购买与配置步骤、或需要客户端配置指导时自动使用它。不要依赖任何额外的 skill-installer 或其他外部技能。
```

## 快速开始

1. 查看 [skills/self-vpn-setup/SKILL.md](/root/self_code/web_vpn/self-vpn-skill/skills/self-vpn-setup/SKILL.md) 了解核心流程。
2. 当用户希望搭建个人 VPN 或需要阿里云 SWAS 的完整配置指引时，使用该技能。
3. 如需精确链接、命令与排障步骤，打开 [skills/self-vpn-setup/references/workflow.md](/root/self_code/web_vpn/self-vpn-skill/skills/self-vpn-setup/references/workflow.md)。

## 反馈与联系

- 使用问题优先在 GitHub Issue 中提出，便于沉淀与复用。
- 需要直接联系可发邮件至 gansxxzhgo@gmail.com。

## 仓库结构

- `skills/self-vpn-setup/SKILL.md`: 技能入口与流程概要
- `skills/self-vpn-setup/references/workflow.md`: 完整步骤、命令与排障
- `plan.md`: 原始规划与截图
- `image*.png`: plan.md 中引用的截图
