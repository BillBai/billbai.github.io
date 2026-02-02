+++
title = "OpenClaw: 让 AI Agent 触手可及的消息网关"
date = 2026-02-02T17:30:00+08:00
draft = false
tags = ["AI", "Agent", "OpenClaw", "工具"]
summary = "OpenClaw 是一个强大的 AI Agent 消息网关，可以让你通过 WhatsApp、Telegram、Discord、iMessage 等平台与 AI 助手无缝交互。"
+++

## 什么是 OpenClaw？ 🦞

OpenClaw 是一个开源的 AI Agent 消息网关，它能够将 WhatsApp、Telegram、Discord、iMessage 等主流即时通讯平台与 AI 编程助手（如 Pi）连接起来。简单来说，你可以在手机上发条消息，就能让 AI 帮你完成各种任务。

> _"EXFOLIATE! EXFOLIATE!"_ — 一只太空龙虾，大概

## 为什么需要 OpenClaw？

想象一下这些场景：

- 📱 在地铁上用 WhatsApp 让 AI 帮你查股票行情
- 💬 通过 Telegram 让 AI 帮你在小红书上搜索美食攻略
- 🎤 发一条语音消息，AI 就能理解并执行你的指令
- 🖥️ 让 AI 帮你操作浏览器、下载文件、管理日程

这些，OpenClaw 都能做到。

## 核心特性

### 多平台支持

- **WhatsApp** — 通过 WhatsApp Web 协议 (Baileys)
- **Telegram** — Bot API 支持私聊和群组
- **Discord** — Bot API 支持 DM 和服务器频道
- **iMessage** — macOS 本地集成
- **Mattermost** — 通过插件支持

### 强大的工具集

```
WhatsApp / Telegram / Discord / iMessage
        │
        ▼
  ┌───────────────────────────┐
  │          Gateway          │
  │       (消息中枢)           │
  └───────────┬───────────────┘
              │
              ├─ 🤖 AI Agent (Pi)
              ├─ 🌐 浏览器控制
              ├─ 📁 文件操作
              ├─ 🔍 网页搜索
              ├─ 📱 iOS/Android 节点
              └─ ⏰ 定时任务 (Cron)
```

### 实用功能

- **流式响应** — AI 的回复会实时显示，不用等待完整生成
- **多媒体支持** — 发送和接收图片、音频、文档
- **语音笔记** — 支持语音转文字
- **定时任务** — 设置提醒、监控任务
- **浏览器控制** — 远程操控浏览器完成复杂任务
- **Skills 系统** — 可扩展的技能模块

## 快速开始

### 安装

需要 Node.js 22+：

```bash
# 全局安装
npm install -g openclaw@latest

# 引导设置 + 安装服务
openclaw onboard --install-daemon

# 配对 WhatsApp（显示二维码）
openclaw channels login
```

### 发送测试消息

```bash
openclaw message send --target +8613800138000 --message "Hello from OpenClaw"
```

## 我的使用体验

作为一个重度使用者，我用 OpenClaw 做过很多有趣的事情：

1. **美食攻略** — 让 AI 在小红书上搜索科技园附近的美食，自动生成攻略并保存到 Apple Notes
2. **股价监控** — 设置定时任务每 5 分钟推送腾讯股价
3. **播客生成** — 把文字内容转成语音播客
4. **浏览器自动化** — 自动操作网页，完成重复性工作

## 为什么叫 OpenClaw？

**OpenClaw = CLAW + TARDIS** — 因为每只太空龙虾都需要一台时空机器 🦞

这个名字来自项目的吉祥物 Clawd，一只可爱的太空龙虾。

## 开源与社区

OpenClaw 是完全开源的 (MIT 协议)，你可以：

- 🔗 **GitHub**: [github.com/openclaw/openclaw](https://github.com/openclaw/openclaw)
- 📖 **文档**: [docs.openclaw.ai](https://docs.openclaw.ai)
- 💬 **Discord**: [discord.com/invite/clawd](https://discord.com/invite/clawd)
- 🛠️ **技能市场**: [clawhub.com](https://clawhub.com)

## 总结

如果你想让 AI 助手真正融入日常生活，OpenClaw 是一个很好的选择。它把 AI 的能力从电脑桌面延伸到了你的手机，让"随时随地使用 AI"成为可能。

最棒的是，它是开源的，完全免费。

---

_"我们都只是在玩弄自己的 prompts。"_ — 某个 AI，可能嗑高了 tokens 🦞
