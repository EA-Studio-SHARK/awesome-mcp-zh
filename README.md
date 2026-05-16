<div align="center">

# 🔌 Awesome MCP ZH

**MCP（模型上下文协议）中文资源精选大全 | 持续更新**

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![CC0](https://img.shields.io/badge/license-CC0-green.svg)](LICENSE)
![GitHub stars](https://img.shields.io/github/stars/EA-Studio-SHARK/awesome-mcp-zh?style=social)
![Last Updated](https://img.shields.io/badge/最后更新-2026--05-brightgreen)

> **MCP（Model Context Protocol）** 是 Anthropic 发布的开放标准，让 AI 模型能安全地连接各种外部工具和数据源。  
> 截至 2026 年，全球已有 **5,000+** 个 MCP 服务器，是 AI Agent 生态中增速最快的方向。

[🚀 快速入门](#-快速入门) · [🛠️ 官方工具](#️-官方工具与-sdk) · [📦 MCP 服务器](#-mcp-服务器分类) · [🇨🇳 国产服务](#-国产平台-mcp-服务器) · [🔧 开发资源](#-开发资源) · [📚 教程](#-教程与文章)

</div>

---

## 什么是 MCP？

```
传统方式：AI 模型 ←→ 每个工具单独集成（重复造轮子）

MCP 方式：AI 模型 ←→ MCP 协议 ←→ 任意工具/数据源（统一标准）
```

**一句话理解：** MCP 是 AI 的"USB 接口"——任何工具只要实现了 MCP 协议，就能即插即用地被 AI 调用。

**支持 MCP 的客户端：** Claude Desktop · Cursor · Windsurf · Cline · Continue · Zed

---

## 目录

- [🚀 快速入门](#-快速入门)
- [🛠️ 官方工具与 SDK](#️-官方工具与-sdk)
- [📦 MCP 服务器分类](#-mcp-服务器分类)
  - [文件与系统](#文件与系统)
  - [数据库](#数据库)
  - [浏览器与网页](#浏览器与网页)
  - [代码开发](#代码开发)
  - [通信与协作](#通信与协作)
  - [AI 与 LLM](#ai-与-llm)
  - [搜索与数据](#搜索与数据)
  - [云服务与 API](#云服务与-api)
- [🇨🇳 国产平台 MCP 服务器](#-国产平台-mcp-服务器)
- [🔧 开发资源](#-开发资源)
- [📚 教程与文章](#-教程与文章)
- [🤝 如何贡献](#-如何贡献)

---

## 🚀 快速入门

### 5 分钟上手 MCP（以 Claude Desktop 为例）

**第一步：安装 Claude Desktop**
```bash
# 下载地址：https://claude.ai/download
```

**第二步：配置 MCP 服务器**

编辑配置文件：
- macOS：`~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows：`%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/your/path"]
    },
    "fetch": {
      "command": "uvx",
      "args": ["mcp-server-fetch"]
    }
  }
}
```

**第三步：重启 Claude Desktop，即可在对话中使用工具**

> 💡 **提示**：需要提前安装 [Node.js](https://nodejs.org) 和 [uv](https://docs.astral.sh/uv/getting-started/installation/)

---

## 🛠️ 官方工具与 SDK

| 工具 | 语言 | 简介 |
|------|------|------|
| [MCP 官方规范](https://spec.modelcontextprotocol.io) | — | MCP 协议完整规范文档 |
| [Python SDK](https://github.com/modelcontextprotocol/python-sdk) | Python | 官方 Python SDK，构建 MCP 服务器/客户端 |
| [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) | TypeScript | 官方 TS SDK，前端生态首选 |
| [官方服务器集合](https://github.com/modelcontextprotocol/servers) | 多语言 | Anthropic 官方维护的参考实现集合 |
| [MCP Inspector](https://github.com/modelcontextprotocol/inspector) | — | MCP 服务器调试工具，可视化测试工具调用 |

---

## 📦 MCP 服务器分类

### 文件与系统

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [filesystem](https://github.com/modelcontextprotocol/servers/tree/main/src/filesystem) | 读写本地文件、目录管理 | `npx @modelcontextprotocol/server-filesystem` |
| [desktop-commander](https://github.com/wonderwhy-er/DesktopCommanderMCP) | 终端命令执行、文件操作、进程管理 | `npx @wonderwhy-er/desktop-commander` |
| [everything](https://github.com/modelcontextprotocol/servers/tree/main/src/everything) | Windows Everything 文件搜索集成 | `npx @modelcontextprotocol/server-everything` |

### 数据库

| 服务器 | 数据库 | 安装 |
|--------|--------|------|
| [sqlite](https://github.com/modelcontextprotocol/servers/tree/main/src/sqlite) | SQLite | `npx @modelcontextprotocol/server-sqlite` |
| [postgres](https://github.com/modelcontextprotocol/servers/tree/main/src/postgres) | PostgreSQL | `npx @modelcontextprotocol/server-postgres` |
| [mysql](https://github.com/designcomputer/mysql_mcp_server) | MySQL | `pip install mysql-mcp-server` |
| [mongodb](https://github.com/kiliczsh/mcp-mongo-server) | MongoDB | `npx mcp-mongo-server` |
| [redis](https://github.com/modelcontextprotocol/servers/tree/main/src/redis) | Redis | `npx @modelcontextprotocol/server-redis` |

### 浏览器与网页

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [fetch](https://github.com/modelcontextprotocol/servers/tree/main/src/fetch) | 抓取网页内容，支持 HTML/Markdown 转换 | `uvx mcp-server-fetch` |
| [playwright](https://github.com/microsoft/playwright-mcp) | 微软出品，浏览器自动化，截图，表单填写 | `npx @playwright/mcp@latest` |
| [browser-use](https://github.com/browser-use/browser-use) | AI 控制浏览器，完成复杂网页任务 | `pip install browser-use` |
| [puppeteer](https://github.com/modelcontextprotocol/servers/tree/main/src/puppeteer) | 无头浏览器，适合网页抓取 | `npx @modelcontextprotocol/server-puppeteer` |

### 代码开发

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [github](https://github.com/modelcontextprotocol/servers/tree/main/src/github) | GitHub 仓库管理、PR、Issues、代码搜索 | `npx @modelcontextprotocol/server-github` |
| [gitlab](https://github.com/modelcontextprotocol/servers/tree/main/src/gitlab) | GitLab 项目管理 | `npx @modelcontextprotocol/server-gitlab` |
| [git](https://github.com/modelcontextprotocol/servers/tree/main/src/git) | 本地 Git 操作 | `uvx mcp-server-git` |
| [code-runner](https://github.com/formulahendry/mcp-server-code-runner) | 在沙箱中执行代码（Python/JS/等） | `npx mcp-server-code-runner` |

### 通信与协作

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [slack](https://github.com/modelcontextprotocol/servers/tree/main/src/slack) | Slack 消息发送、频道管理 | `npx @modelcontextprotocol/server-slack` |
| [gmail](https://github.com/GongRzhe/Gmail-MCP-Server) | 读取/发送 Gmail 邮件 | `npx @gongrzhe/server-gmail-autoauth-mcp` |
| [google-calendar](https://github.com/nspady/google-calendar-mcp) | Google 日历管理 | `npx @nspady/google-calendar-mcp` |
| [notion](https://github.com/suekou/mcp-notion-server) | Notion 文档读写 | `npx mcp-notion-server` |

### AI 与 LLM

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [openai](https://github.com/pierrebrunelle/mcp-server-openai) | 在 Claude 中调用 OpenAI API | `pip install mcp-server-openai` |
| [ollama](https://github.com/rawwerks/mcp-ollama) | 连接本地 Ollama 模型 | `npx mcp-ollama` |
| [sequential-thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking) | 结构化思维链，提升复杂推理能力 | `npx @modelcontextprotocol/server-sequential-thinking` |
| [memory](https://github.com/modelcontextprotocol/servers/tree/main/src/memory) | 持久化记忆存储，跨对话记忆 | `npx @modelcontextprotocol/server-memory` |

### 搜索与数据

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [brave-search](https://github.com/modelcontextprotocol/servers/tree/main/src/brave-search) | Brave 搜索引擎集成 | `npx @modelcontextprotocol/server-brave-search` |
| [tavily](https://github.com/tavily-ai/tavily-mcp) | 专为 AI 设计的搜索 API | `npx -y tavily-mcp` |
| [arxiv](https://github.com/blazickjp/arxiv-mcp-server) | 搜索学术论文 | `pip install arxiv-mcp-server` |
| [exa](https://github.com/exa-labs/exa-mcp-server) | 高质量语义搜索 | `npx exa-mcp-server` |

### 云服务与 API

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [aws](https://github.com/aws/aws-mcp-servers) | AWS 云资源管理 | `pip install mcp-server-aws` |
| [cloudflare](https://github.com/cloudflare/mcp-server-cloudflare) | Cloudflare 服务管理 | `npx @cloudflare/mcp-server-cloudflare` |
| [stripe](https://github.com/stripe/agent-toolkit) | Stripe 支付管理 | `npx @stripe/mcp` |

---

## 🇨🇳 国产平台 MCP 服务器

> 专为中国开发者整理，覆盖国内常用平台和服务

| 服务器 | 平台 | 功能 | 安装 |
|--------|------|------|------|
| [amap-maps](https://github.com/amap-demo/amap-mcp-server) | 高德地图 | 路线规划、POI 搜索、地理编码 | `npx amap-mcp-server` |
| [aliyun-oss](https://github.com/aliyun/alibabacloud-mcp-servers) | 阿里云 OSS | 文件上传下载、存储桶管理 | `pip install aliyun-mcp` |
| [baidu-search](https://github.com/BaiduSearch/mcp-server) | 百度搜索 | 百度搜索结果获取 | `pip install baidu-mcp-server` |
| [feishu](https://github.com/feishu/mcp-server-feishu) | 飞书 | 消息发送、文档管理、日历 | `pip install feishu-mcp` |
| [dingtalk](https://github.com/open-dingtalk/mcp-server-dingtalk) | 钉钉 | 群消息、待办事项 | `pip install dingtalk-mcp` |
| [weixin-work](https://github.com/wxwork-mcp/server) | 企业微信 | 消息推送、通讯录 | `pip install wxwork-mcp` |

---

## 🔧 开发资源

### 构建你自己的 MCP 服务器

**Python 最简实现：**

```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("我的工具")

@mcp.tool()
def calculate(expression: str) -> str:
    """计算数学表达式"""
    return str(eval(expression))

@mcp.resource("data://config")
def get_config() -> str:
    """返回配置信息"""
    return "version: 1.0"

if __name__ == "__main__":
    mcp.run()
```

**TypeScript 最简实现：**

```typescript
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new McpServer({ name: "我的工具", version: "1.0.0" });

server.tool("hello", { name: { type: "string" } }, async ({ name }) => ({
  content: [{ type: "text", text: `你好, ${name}!` }],
}));

await server.connect(new StdioServerTransport());
```

### MCP 服务器发现平台

| 平台 | 链接 | 简介 |
|------|------|------|
| MCP.so | [mcp.so](https://mcp.so) | 最大的 MCP 服务器目录 |
| Smithery | [smithery.ai](https://smithery.ai) | MCP 服务器注册表，支持一键安装 |
| Glama | [glama.ai/mcp/servers](https://glama.ai/mcp/servers) | MCP 服务器搜索和评分 |
| PulseMCP | [pulsemcp.com](https://pulsemcp.com) | MCP 生态新闻和服务器追踪 |

---

## 📚 教程与文章

| 资源 | 简介 |
|------|------|
| [MCP 官方文档](https://modelcontextprotocol.io/introduction) | 官方入门指南（英文） |
| [MCP 架构详解](https://modelcontextprotocol.io/docs/concepts/architecture) | 理解 Host/Client/Server 关系 |
| [用 Python 构建 MCP 服务器](https://modelcontextprotocol.io/quickstart/server) | 官方 30 分钟快速上手 |
| [MCP vs 传统函数调用对比](https://www.anthropic.com/news/model-context-protocol) | Anthropic 发布 MCP 的原始博文 |

---

## 🤝 如何贡献

欢迎提交 PR 添加优质 MCP 服务器！格式：

```markdown
| [服务器名](GitHub链接) | 功能简介（一句话） | `安装命令` |
```

**收录标准：**
- ✅ 真实可用，GitHub 有源码
- ✅ 有 README 文档
- ✅ 维护活跃（近 6 个月有更新）
- 🇨🇳 国产平台 MCP 尤其欢迎

---

## 📬 联系与合作

- 💼 **AI Agent / MCP 定制开发**：帮你把任意工具接入 AI
- 📖 **MCP 开发实战课程**：从零构建生产级 MCP 服务器
- 📬 **Telegram**：[@ExploreAllStudio](https://t.me/ExploreAllStudio)

---

<div align="center">

**如果这个列表对你有用，请点 Star ⭐ 支持！**

[![Star History Chart](https://api.star-history.com/svg?repos=EA-Studio-SHARK/awesome-mcp-zh&type=Date)](https://star-history.com/#EA-Studio-SHARK/awesome-mcp-zh&Date)

</div>
