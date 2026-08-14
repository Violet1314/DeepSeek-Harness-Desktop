# DeepSeek-Harness-Desktop

DeepSeek Harness 官方 Web 界面的 Windows 桌面客户端 支持Win10/11。

---

## 界面预览

<img width="2559" height="1373" alt="4" src="https://github.com/user-attachments/assets/de83ab84-c2a9-4394-8d6b-fbdd9df619d2" />

## 📦 下载安装

1. 前往 **[Releases](https://github.com/DeepSeek-Harness-Desktop/DeepSeek-Harness-Desktop/releases)** 页面
2. 下载最新的安装包
3. 双击运行 → 选择安装目录（可选）→ 完成安装
4. 桌面快捷方式双击启动，即可开始使用

> ⚠️ **SmartScreen 提示说明**：本应用暂未购买代码签名证书，Windows 首次运行可能弹出蓝色 SmartScreen 警告。点击「更多信息」→「仍要运行」即可正常使用。

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
