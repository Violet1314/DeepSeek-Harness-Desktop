# DeepSeek-Harness-Desktop

DeepSeek Harness 官方 Web 界面的 Windows 桌面客户端 支持Win10/11。

---

## 界面预览

<img width="493" height="360" alt="2" src="https://github.com/user-attachments/assets/327fa3e1-a257-4a2c-8138-7ab1edcf47b5" />

<img width="1585" height="1021" alt="1" src="https://github.com/user-attachments/assets/78633fdc-a27e-4f43-a8c2-48a5e98de685" />

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
