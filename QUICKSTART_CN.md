# Playwright MCP 中文精简版

> 🌐 为中文用户优化的 Playwright MCP 服务器快速配置指南
> 
> 📦 基于 [microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp) (29,851⭐)
> 
> 🚀 5 分钟快速上手，让 Claude/Cursor 帮你操作浏览器

---

## ⚡ 30 秒快速安装

### Cursor 用户（推荐）

**方式 1：一键安装**

点击以下链接自动安装：

[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=Playwright&config=eyJjb21tYW5kIjoibnB4IEBwbGF5d3JpZ2h0L21jcEBsYXRlc3QifQ%3D%3D)

**方式 2：手动配置**

1. 打开 Cursor 设置 (`Cmd+,` / `Ctrl+,`)
2. 找到 `MCP` 选项卡
3. 点击 `Add new MCP Server`
4. 填写：
   - Name: `Playwright`
   - Type: `command`
   - Command: `npx @playwright/mcp@latest`
5. 保存

### Claude Code CLI 用户

```bash
claude mcp add playwright npx @playwright/mcp@latest
```

### VS Code 用户

点击安装：

[![Install in VS Code](https://img.shields.io/badge/VS_Code-VS_Code?style=flat-square&label=Install%20Server&color=0098FF)](https://insiders.vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522playwright%2522%252C%2522command%2522%253A%2522npx%2522%252C%2522args%2522%253A%255B%2522%2540playwright%252Fmcp%2540latest%2522%255D%257D)

---

## 🎯 使用示例

安装完成后，重启你的 AI 助手，然后就可以这样使用：

### 示例 1：浏览网页

```
帮我打开 https://github.com/trending，看看今天最火的项目有哪些
```

### 示例 2：填写表单

```
打开 https://www.google.com，在搜索框输入"Playwright MCP"，然后搜索
```

### 示例 3：抓取数据

```
访问 https://news.ycombinator.com，提取前 5 篇文章的标题、作者和分数
```

### 示例 4：自动化操作

```
帮我登录 GitHub：
1. 打开 github.com/login
2. 用户名填：your_username
3. 密码填：your_password
4. 点击 Sign in
```

---

## 🛠️ 可用命令

AI 助手可以调用以下浏览器操作：

| 命令 | 功能 |
|------|------|
| `browser_navigate` | 打开网址 |
| `browser_snapshot` | 获取页面结构快照 |
| `browser_click` | 点击元素 |
| `browser_type` | 输入文字 |
| `browser_select` | 选择下拉选项 |
| `browser_hover` | 鼠标悬停 |
| `browser_press` | 按键操作 |
| `browser_close` | 关闭浏览器 |

---

## ❓ 常见问题

### Q: 安装后没反应？

A: 重启你的 AI 助手（Cursor/Claude Desktop 等），确保 MCP 服务器已加载。

### Q: 浏览器打不开？

A: 首次运行会自动下载 Playwright 浏览器（约 100MB），请等待下载完成。

### Q: 能用什么浏览器？

A: 默认使用 Chromium，也支持 Chrome、Firefox、WebKit。

### Q: 需要付费吗？

A: 完全免费，开源项目。

---

## 📚 进阶学习

- [完整中文文档](./README.md)
- [英文原版文档](https://github.com/microsoft/playwright-mcp)
- [Playwright 官方教程](https://playwright.dev)

---

## 💬 反馈与交流

遇到问题或有建议？

- [提交 Issue](https://github.com/toyball860721/playwright-mcp-cn/issues)
- [加入讨论](https://github.com/toyball860721/playwright-mcp-cn/discussions)

---

## ☕ 支持本项目

这是一个免费的中文本地化项目，如果你觉得有用：

- [爱发电赞助](https://afdian.com/a/toyball)
- [GitHub Sponsors](https://github.com/sponsors/toyball860721)

---

**🦞 中文维护者：[@toyball860721](https://github.com/toyball860721)**

*最后更新：2026-03-28*
