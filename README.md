<div align="center">

# 🔌 MCP 中国开发者实战工具包

**精选 · 亲测可用 · 中国环境配置 · 持续更新**

[![CC0](https://img.shields.io/badge/license-CC0-green.svg)](LICENSE)
![GitHub stars](https://img.shields.io/github/stars/EA-Studio-SHARK/awesome-mcp-zh?style=social)
![Last Updated](https://img.shields.io/badge/最后更新-2026--05-brightgreen)

> 不是大而全的列表，而是**真正在中国网络环境下测试可用**的 MCP 精选套件  
> 附完整配置代码 · 踩坑记录 · 国产平台专区 · 5 分钟上手

**⭐ 如果觉得有用，请给个 Star！你的支持是持续更新的动力**

[⚡ 5分钟上手](#-5-分钟上手) · [✅ 精选必装](#-精选必装-mcp-亲测) · [🇨🇳 国产平台](#-国产平台-mcp) · [� 热搜工具](#-配套工具) · [�️ 自己开发](#-自己开发-mcp)

</div>

---

## ⚡ 5 分钟上手

> 适用于 Claude Desktop / Cursor / Windsurf

**前置条件：** 安装 [Node.js](https://nodejs.org) 和 [uv](https://docs.astral.sh/uv/)

**配置文件位置：**
- Claude：`~/Library/Application Support/Claude/claude_desktop_config.json`
- Cursor / Windsurf：IDE 设置 → MCP

**粘贴这份配置即可获得 5 个核心能力：**

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/你的用户名/Documents"]
    },
    "fetch": {
      "command": "uvx",
      "args": ["mcp-server-fetch"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "你的Token" }
    },
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    },
    "china-hot": {
      "command": "python3",
      "args": ["-m", "china_hot_mcp.server"]
    }
  }
}
```

重启客户端后，AI 就能：读写文件、抓网页、管理 GitHub、跨对话记忆、查中国热搜。

---

## ✅ 精选必装 MCP（亲测）

> 仅收录在中国网络环境下实测稳定可用的服务器

### 基础能力（必装）

| 服务器 | 解决什么问题 | 安装 | 备注 |
|--------|------------|------|------|
| [filesystem](https://github.com/modelcontextprotocol/servers/tree/main/src/filesystem) | AI 读写本地文件 | `npx @modelcontextprotocol/server-filesystem /path` | 官方，最稳定 |
| [fetch](https://github.com/modelcontextprotocol/servers/tree/main/src/fetch) | AI 抓取任意网页内容 | `uvx mcp-server-fetch` | 纯 Python，无 Node 依赖 |
| [memory](https://github.com/modelcontextprotocol/servers/tree/main/src/memory) | AI 跨对话记住你的信息 | `npx @modelcontextprotocol/server-memory` | 告别每次重复介绍自己 |
| [git](https://github.com/modelcontextprotocol/servers/tree/main/src/git) | AI 操作本地 Git 仓库 | `uvx mcp-server-git` | 无需 Token |

### 开发者工具

| 服务器 | 功能 | 安装 |
|--------|------|------|
| [github](https://github.com/modelcontextprotocol/servers/tree/main/src/github) | 管理仓库/PR/Issues | `npx @modelcontextprotocol/server-github` |
| [playwright](https://github.com/microsoft/playwright-mcp) | 浏览器自动化（截图/表单/抓数据） | `npx @playwright/mcp@latest` |
| [sqlite](https://github.com/modelcontextprotocol/servers/tree/main/src/sqlite) | 读写 SQLite 数据库 | `npx @modelcontextprotocol/server-sqlite` |
| [sequential-thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking) | 提升复杂推理质量 | `npx @modelcontextprotocol/server-sequential-thinking` |

### 中国常用搜索（替代 Google）

| 服务器 | 说明 | 安装 |
|--------|------|------|
| [tavily](https://github.com/tavily-ai/tavily-mcp) | 最好用的 AI 搜索，国内可访问，免费额度充足 | `npx -y tavily-mcp` |
| [arxiv](https://github.com/blazickjp/arxiv-mcp-server) | 搜索学术论文，免费无需 Key | `pip install arxiv-mcp-server` |

---

## 🇨🇳 国产平台 MCP

> 这些是中国开发者专属，其他 awesome 列表没有或更新不及时

| 服务器 | 平台 | 功能 |
|--------|------|------|
| [高德地图 MCP](https://github.com/amap-demo/amap-mcp-server) | 高德 | 路线规划、POI 搜索、天气查询 |
| [飞书 MCP](https://github.com/feishu/mcp-server-feishu) | 飞书 | 消息发送、文档读写、日历管理 |
| [钉钉 MCP](https://github.com/open-dingtalk/mcp-server-dingtalk) | 钉钉 | 群消息、待办事项推送 |
| [企业微信 MCP](https://github.com/loonghao/wecom-bot-mcp-server) | 企微 | 消息推送到工作群 |
| [阿里云 MCP](https://github.com/aliyun/alibabacloud-mcp-servers) | 阿里云 | OSS 文件管理、云资源操作 |
| [china-hot-mcp](https://github.com/EA-Studio-SHARK/china-hot-mcp) | 全平台热搜 | 微博/知乎/B站/百度/抖音实时热榜 |

---

## 🔥 配套工具

本项目配套开发的实用工具：

- **[china-hot-mcp](https://github.com/EA-Studio-SHARK/china-hot-mcp)** — 中国热搜 MCP，让 AI 实时获取微博/知乎/B站/百度/抖音热榜
- **[local-ai-china](https://github.com/EA-Studio-SHARK/local-ai-china)** — 本地 AI 部署指南，一键启动 DeepSeek/Qwen，解决国内网络问题

---

## 🛠️ 自己开发 MCP

**5 分钟写一个 MCP 服务器（Python）：**

```bash
pip install "mcp[cli]"
```

```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("我的工具")

@mcp.tool()
async def my_tool(query: str) -> str:
    """工具描述（AI 会读取这里来决定何时调用）"""
    return f"处理结果：{query}"

if __name__ == "__main__":
    mcp.run()
```

**调试：**
```bash
npx @modelcontextprotocol/inspector python my_tool.py
```

**完整示例参考：** [china-hot-mcp 源码](https://github.com/EA-Studio-SHARK/china-hot-mcp)

---

## ⚠️ 中国环境踩坑记录

**问题：`npx` 命令执行很慢或超时**
> 解决：配置 npm 镜像 `npm config set registry https://registry.npmmirror.com`

**问题：`uvx` 下载包失败**
> 解决：`pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple`

**问题：MCP 服务器配置后在客户端不显示**
> 解决：检查 JSON 格式是否有语法错误，重启客户端，查看客户端的 MCP 日志

**问题：某些 MCP 需要国外 API Key（如 Brave Search）**
> 替代：使用 Tavily（国内可访问）或本项目的 china-hot-mcp

---

## 📚 延伸资源

| 资源 | 类型 |
|------|------|
| [MCP 官方文档](https://modelcontextprotocol.io) | 官方文档 |
| [MCP.so 目录](https://mcp.so) | 最全服务器目录 |

---

## � 相关项目

- **[china-hot-mcp](https://github.com/EA-Studio-SHARK/china-hot-mcp)** — 中国热搜 MCP，让 AI 实时获取微博/知乎/B站/百度/抖音热榜
- **[ai-morning-brief](https://github.com/EA-Studio-SHARK/ai-morning-brief)** — Claude Code 中文 AI 早报 Skill
- **[local-ai-china](https://github.com/EA-Studio-SHARK/local-ai-china)** — 本地 AI 部署指南，一键启动 DeepSeek/Qwen

---

## �📬 联系与合作

- 💼 **MCP 定制开发**：帮你把任意中国平台工具接入 AI Agent
- 📬 **Telegram**：[@ExploreAllStudio](https://t.me/ExploreAllStudio)


---

## 💬 加群交流

正在维护 **「EA同学的 AI 实战圈」** 群：

- 📰 每天 9:00 同步精选 AI 早报（国内+国际双轨）
- 🛠️ 每周分享 Claude Code Skills / MCP 实战
- 💡 工具选型、踩坑、咨询都可以群里问

**加群**：知乎/掘金私信我「加群」即可，看到就发。


---

<div align="center">

**⭐ 如果觉得有用，请给个 Star！你的支持是持续更新的动力**

</div>
