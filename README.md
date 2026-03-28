# Playwright MCP 中文文档

> 🌐 **Playwright MCP 服务器** — 为 AI 助手提供浏览器自动化能力
> 
> 📦 原版项目：[microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp) (29,851⭐)
> 
> 📝 中文维护者：[@toyball860721](https://github.com/toyball860721)
> 
> ☕ 支持本项目：[爱发电](https://afdian.com/a/toyball) | [GitHub Sponsors](https://github.com/sponsors/toyball860721)

---

## 📖 项目简介

Playwright MCP 是一个 Model Context Protocol (MCP) 服务器，使用 [Playwright](https://playwright.dev) 提供浏览器自动化能力。它允许大语言模型 (LLM) 通过结构化的可访问性快照与网页交互，无需截图或视觉调优模型。

### Playwright MCP vs Playwright CLI

- **CLI**：现代编码代理更倾向于基于 CLI 的工作流（通过 SKILLS 暴露），因为 CLI 调用更节省 token — 避免将大型工具模式和冗长的可访问性树加载到模型上下文中。适合高吞吐量的编码代理。
  
- **MCP**：MCP 对于需要持久状态、丰富内省和迭代推理的专业化代理循环仍然相关，例如探索性自动化、自愈测试或长期自主工作流。

### 核心特性

- ⚡ **快速轻量** — 使用 Playwright 可访问性树，非基于像素
- 🤖 **LLM 友好** — 无需视觉模型，纯结构化数据操作
- 🎯 **确定性工具应用** — 避免基于截图方法的歧义

### 系统要求

- Node.js 18 或更高版本
- VS Code、Cursor、Windsurf、Claude Desktop、Goose 或任何支持 MCP 的客户端

---

## 🚀 快速开始

### 标准安装配置

大多数 MCP 客户端使用以下标准配置：

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

### 各平台安装指南

#### VS Code / VS Code Insiders

[![Install in VS Code](https://img.shields.io/badge/VS_Code-VS_Code?style=flat-square&label=Install%20Server&color=0098FF)](https://insiders.vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522playwright%2522%252C%2522command%2522%253A%2522npx%2522%252C%2522args%2522%253A%255B%2522%2540playwright%252Fmcp%2540latest%2522%255D%257D)

[![Install in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-VS_Code_Insiders?style=flat-square&label=Install%20Server&color=24bfa5)](https://insiders.vscode.dev/redirect?url=vscode-insiders%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522playwright%2522%252C%2522command%2522%253A%2522npx%2522%252C%2522args%2522%253A%255B%2522%2540playwright%252Fmcp%2540latest%2522%255D%257D)

#### Claude Code CLI

```bash
claude mcp add playwright npx @playwright/mcp@latest
```

#### Cursor

**方式 1：一键安装**

[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=Playwright&config=eyJjb21tYW5kIjoibnB4IEBwbGF5d3JpZ2h0L21jcEBsYXRlc3QifQ%3D%3D)

**方式 2：手动安装**

1. 打开 `Cursor Settings` → `MCP` → `Add new MCP Server`
2. 填写名称（如 Playwright）
3. 类型选择 `command`
4. 命令输入：`npx @playwright/mcp@latest`

#### Cline

在 `cline_mcp_settings.json` 中添加：

```json
{
  "mcpServers": {
    "playwright": {
      "type": "stdio",
      "command": "npx",
      "timeout": 30,
      "args": ["-y", "@playwright/mcp@latest"],
      "disabled": false
    }
  }
}
```

#### Codex CLI

```bash
codex mcp add playwright npx "@playwright/mcp@latest"
```

或编辑 `~/.codex/config.toml`：

```toml
[mcp_servers.playwright]
command = "npx"
args = ["@playwright/mcp@latest"]
```

#### Copilot CLI

```bash
/mcp add
```

或编辑 `~/.copilot/mcp-config.json`：

```json
{
  "mcpServers": {
    "playwright": {
      "type": "local",
      "command": "npx",
      "tools": ["*"],
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

#### Goose

**方式 1：一键安装**

[![Install in Goose](https://block.github.io/goose/extension-install-dark.svg)](https://block.github.io/goose/extension?cmd=npx&arg=%40playwright%2Fmcp%40latest&id=playwright&name=Playwright&description=Interact%20with%20web%20pages%20through%20structured%20accessibility%20snapshots%20using%20Playwright)

**方式 2：手动安装**

1. 打开 `Advanced settings` → `Extensions` → `Add custom extension`
2. 名称自定义
3. 类型选择 `STDIO`
4. 命令输入：`npx @playwright/mcp`

#### 其他平台

<details>
<summary>Amp</summary>

```json
"amp.mcpServers": {
  "playwright": {
    "command": "npx",
    "args": ["@playwright/mcp@latest"]
  }
}
```

或 CLI：
```bash
amp mcp add playwright -- npx @playwright/mcp@latest
```

</details>

<details>
<summary>Antigravity</summary>

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

</details>

<details>
<summary>Claude Desktop</summary>

参考 MCP 安装指南：https://modelcontextprotocol.io/quickstart/user

使用上方标准配置。

</details>

<details>
<summary>Factory</summary>

```bash
droid mcp add playwright "npx @playwright/mcp@latest"
```

或输入 `/mcp` 打开交互式 UI。

</details>

<details>
<summary>Gemini CLI</summary>

参考：https://github.com/google-gemini/gemini-cli/blob/main/docs/tools/mcp-server.md

</details>

<details>
<summary>Kiro</summary>

[![Add to Kiro](https://kiro.dev/images/add-to-kiro.svg)](https://kiro.dev/launch/mcp/add?name=playwright&config=%7B%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22%40playwright%2Fmcp%2540latest%22%5D%7D)

编辑 `~/.kiro/settings/mcp.json`：

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

</details>

<details>
<summary>LM Studio</summary>

[![Add MCP Server](https://files.lmstudio.ai/deeplink/mcp-install-light.svg)](https://lmstudio.ai/install-mcp?name=playwright&config=eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyJAcGxheXdyaWdodC9tY3BAbGF0ZXN0Il19)

或编辑 `mcp.json` 使用标准配置。

</details>

<details>
<summary>opencode</summary>

编辑 `~/.config/opencode/opencode.json`：

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "playwright": {
      "type": "local",
      "command": ["npx", "@playwright/mcp@latest"],
      "enabled": true
    }
  }
}
```

</details>

<details>
<summary>Qodo Gen</summary>

在 VSCode 或 IntelliJ 中打开 Qodo Gen 面板 → Connect more tools → + Add new MCP → 粘贴标准配置。

</details>

---

## 🛠️ 可用工具

安装完成后，你的 AI 助手将能够使用以下工具：

| 工具 | 描述 |
|------|------|
| `browser_snapshot` | 捕获当前页面的可访问性快照 |
| `browser_click` | 点击页面上的元素 |
| `browser_type` | 在输入框中输入文本 |
| `browser_select` | 选择下拉菜单选项 |
| `browser_hover` | 悬停在元素上 |
| `browser_press` | 按下键盘按键 |
| `browser_navigate` | 导航到指定 URL |
| `browser_close` | 关闭浏览器 |

---

## 📚 使用示例

### 示例 1：导航并截图

```
请打开 https://github.com 并告诉我 trending  repositories 有哪些
```

### 示例 2：填写表单

```
帮我打开 https://example.com/login，填写用户名 test@example.com 和密码 123456，然后点击登录
```

### 示例 3：数据抓取

```
访问 https://news.ycombinator.com，提取前 10 篇文章的标题和链接
```

---

## 🔧 高级配置

### 使用特定浏览器

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"],
      "env": {
        "BROWSER": "chrome"
      }
    }
  }
}
```

支持的浏览器：`chromium` (默认), `firefox`, `webkit`, `chrome`

### 无头模式

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headless"]
    }
  }
}
```

---

## 📖 完整文档

- [英文原版文档](https://github.com/microsoft/playwright-mcp)
- [Playwright 官方文档](https://playwright.dev)
- [MCP 协议规范](https://modelcontextprotocol.io)

---

## 🤝 参与贡献

欢迎提交 Issue 和 Pull Request 改进中文文档！

- 报告翻译错误
- 补充使用示例
- 添加更多中文教程

---

## 📄 许可证

本项目遵循原项目的 MIT 许可证。

---

## ☕ 支持作者

如果你觉得这个中文文档对你有帮助，欢迎支持：

- [爱发电](https://afdian.com/a/toyball)
- [GitHub Sponsors](https://github.com/sponsors/toyball860721)

**中文维护者持续更新中...** 🦞
