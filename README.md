# DeepSeek-Harness-Desktop

DeepSeek Harness 官方 Web 界面的 Windows 桌面客户端。下载即用、双击即开，无需命令行配置，为 Win10/11 用户提供开箱即用的 AI 编程体验。

A Windows desktop client wrapping the official DeepSeek Harness web UI. Download, install, and start using it right away — no command-line setup required, delivering an out-of-the-box AI coding experience for Windows 10/11 users.

---

## 界面预览

<img width="493" height="360" alt="2" src="https://github.com/user-attachments/assets/327fa3e1-a257-4a2c-8138-7ab1edcf47b5" />

<img width="1585" height="1021" alt="1" src="https://github.com/user-attachments/assets/78633fdc-a27e-4f43-a8c2-48a5e98de685" />

## 为什么做这个项目？

官方 DeepSeek Harness 以 Node.js 命令行方式运行，普通用户需要安装运行环境、记忆命令、手动管理进程，使用门槛较高。本项目把官方内核整体封装进 Windows 桌面应用，让使用回归简单：

- ✅ 无需安装 Node.js / npm，无需任何命令行操作
- ✅ 双击安装包 → 装完即用，打开就是完整界面
- ✅ 关闭窗口自动终止内核进程，不留后台残留
- ✅ 跟随官方内核持续迭代，定期发布新版本

## ✨ 功能特性

- **官方内核，原汁原味**：封装官方 `@deepseek-ai/dsh` Web UI，内核零改动
- **下载即用**：NSIS 安装包，支持自定义安装目录，适配 Windows 10 / 11（x64）
- **单实例运行**：重复启动自动聚焦已有窗口，不重复拉起内核
- **自动清理**：关闭窗口即终止内核进程，不占用后台资源
- **异常兜底**：端口占用、内核异常均有中文错误提示
- **数据保留**：升级覆盖安装后，原有配置与历史会话自动保留

## 📦 下载安装

1. 前往 **[Releases](https://github.com/DeepSeek-Harness-Desktop/DeepSeek-Harness-Desktop/releases)** 页面
2. 下载最新的 `DeepSeek Harness Desktop Setup <版本>.exe` 安装包
3. 双击运行 → 选择安装目录（可选）→ 完成安装
4. 桌面快捷方式双击启动，即可开始使用

> ⚠️ **SmartScreen 提示说明**：本应用暂未购买代码签名证书，Windows 首次运行可能弹出蓝色 SmartScreen 警告。点击「更多信息」→「仍要运行」即可正常使用。

## 🚀 快速开始

1. 启动应用，内核自动在本地 3080 端口启动，稍候进入主界面
2. 首次使用：在应用内引导界面配置你的 DeepSeek API Key（如无 Key 可前往 [platform.deepseek.com](https://platform.deepseek.com) 获取）
3. 在对话窗口开始提问、编写代码

## ❓ 常见问题

| 问题 | 说明 |
| --- | --- |
| 提示 SmartScreen 拦截 | 未签名应用，点击「更多信息」→「仍要运行」 |
| 提示端口被占用 | 应用会自动检测 3080 端口，冲突时会给出提示 |
| 报错 `API key is invalid` | API Key 无效或已更换，请在应用设置中更新 |
| 如何升级到新版本 | 下载最新 Release 安装包覆盖安装即可，配置自动保留 |
| 支持哪些系统 | Windows 10 / 11（64 位） |

## 🛠️ 技术架构

```
Electron 壳层 (main.js)
├── 拉起官方 dsh 内核
├── 等待本地 3080 端口就绪
├── 打开主窗口
└── 窗口关闭时终止内核进程

官方 @deepseek-ai/dsh 内核
└── 本地 Web UI（内核零改动）
```

- 客户端壳层：Electron 43（Chromium + Node.js）
- 内核：官方 `@deepseek-ai/dsh` npm 包（零改动封装）
- 打包：electron-builder → NSIS 安装版（x64）

## 📄 License

MIT
