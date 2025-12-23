<div align="center">

# 🚀 DotNet AI MCP Server

### _The essential Model Context Protocol server for .NET developers building AI applications_

[![MCP](https://img.shields.io/badge/MCP-Compliant-5A67D8?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0wIDE4Yy00LjQxIDAtOC0zLjU5LTgtOHMzLjU5LTggOC04IDggMy41OSA4IDgtMy41OSA4LTggOHoiLz48L3N2Zz4=)](https://modelcontextprotocol.io)
[![.NET 10](https://img.shields.io/badge/.NET-10.0-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

<br/>

**🌐 Public Server:** [`https://dotnetaimcp.net`](https://dotnetaimcp.net)

<br/>

[Quick Start](#-quick-start) •
[Why This Exists](#-the-problem--solution) •
[Tools](#%EF%B8%8F-available-tools) •
[Tracked Repos](#-tracked-repositories)

</div>

---

## ⚡ Quick Start

### VS Code / GitHub Copilot

1. Open Command Palette: `Cmd + Shift + P` (Mac) or `Ctrl + Shift + P` (Windows/Linux)
2. Type `MCP: Add Server...` and select it
3. Choose `HTTP`
4. Paste the URL: `https://dotnetaimcp.net`

### Claude Desktop

1. Open **Settings** → **Connectors**
2. Click **Add custom connector**
3. Enter a name (e.g., `DotNet MCP Server`)
4. Paste the URL: `https://dotnetaimcp.net`
5. Click **Add**

---

## 💻 Running Locally

### Prerequisites

- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) (Preview)
- [GitHub Personal Access Token](https://github.com/settings/tokens) (Classic or Fine-grained) with `repo` scope

### Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/dotnet-mcp-server.git
   cd dotnet-mcp-server/DotNetMCPServer
   ```

2. **Configure GitHub Token**
   This project uses .NET User Secrets to keep your token safe.

   ```bash
   dotnet user-secrets init
   dotnet user-secrets set "GitHub:Token" "your_github_token_here"
   ```

3. **Run the server**

   ```bash
   dotnet run
   ```

   The server will start at `http://localhost:5000` (or the port defined in `launchSettings.json`).

4. **Connect your MCP Client**
   Use `http://localhost:5000/mcp` as the endpoint for your MCP client (VS Code, Claude, etc.).

---

## 🎯 The Problem & Solution

### The Problem

Ask any LLM about **Semantic Kernel**, **Microsoft.Extensions.AI**, or **MCP in .NET** and you'll likely get:

- ❌ **Hallucinated APIs** that don't exist
- ❌ **Outdated syntax** from deprecated packages
- ❌ **Confident but wrong** code examples

The .NET AI ecosystem moves fast. Training data can't keep up.

### Why Not Just Use Microsoft Learn MCP?

The [Microsoft Learn MCP Server](https://github.com/MicrosoftDocs/mcp) is great for documentation, but has limitations:

- **Token inefficient** — Returns large documentation chunks that flood your context window
- **No GitHub access** — Can't fetch actual code from repositories like `semantic-kernel`, `openai-dotnet`, or `mcp-csharp-sdk`
- **Generic results** — Optimized for broad Microsoft docs, not specifically for .NET AI development

### The Solution

This MCP server combines the best of both worlds:

| Source              | What You Get                                                                         |
| ------------------- | ------------------------------------------------------------------------------------ |
| **GitHub Repos**    | Live code & docs from `semantic-kernel`, `openai-dotnet`, `mcp-csharp-sdk`, and more |
| **Microsoft Learn** | Official documentation with **optimized token usage** — filtered and truncated       |

#### 💡 Token Optimization

This server implements smart token management:

- **Gradual data exposure** — Starts with repo/folder structure, only fetches file content when needed
- **Filtered results** — Excludes test folders, build outputs, and irrelevant content
- **Truncated summaries** — Documentation snippets optimized for context windows
- **C#-only filtering** — Code samples pre-filtered to .NET languages

**Result:** Real, compiling code and documentation with minimal token overhead.

---

## 🛠️ Available Tools

### Zero-Configuration Agentic Workflow

Unlike other MCP servers that require custom instructions or manual tool invocation, this server uses an **agentic workflow** that automatically triggers when you ask any .NET AI-related question.

Just ask naturally:

> _"How do I create a chat completion with Semantic Kernel?"_

The LLM automatically orchestrates the tools in sequence: **repositories → folders → files → code** — no prompting required.

### GitHub Tools

Navigates tracked repositories to fetch **code and documentation** — the LLM uses both to formulate answers, whether you're asking how to implement something or how something works.

| Tool                 | What It Does                           |
| -------------------- | -------------------------------------- |
| `github_get_repos`   | Lists all tracked .NET AI repositories |
| `github_get_folders` | Shows folder structure of a repository |
| `github_list_files`  | Lists files in specific folders        |
| `github_fetch_files` | Retrieves actual file content          |

### Microsoft Learn Tools

Enhanced versions of the [Microsoft Learn MCP](https://github.com/MicrosoftDocs/mcp) tools with improved token efficiency:

| Tool                           | What It Does                           | Improvements Over Original              |
| ------------------------------ | -------------------------------------- | --------------------------------------- |
| `microsoft_docs_search`        | Searches Microsoft Learn documentation | Truncated snippets, reduced token usage |
| `microsoft_docs_fetch`         | Fetches full documentation page        | Optimized markdown output               |
| `microsoft_code_sample_search` | Finds official code samples            | C#-only filter applied by default       |

---

## 💡 Optional: Session Prompt

A built-in prompt (`dotnet-ai-session`) is automatically exposed when connecting to the server. It reinforces the agentic workflow and ensures the LLM prioritizes the tools over its training data.

**To use it:** Add to any conversation with:

```
/prompt dotnet-ai-session
```

> **Note:** This is optional insurance. The agentic workflow works automatically, but the prompt can help with edge cases.

---

## 📦 Tracked Repositories

### AI Frameworks & Orchestration

| Repository                                                       | Owner     | Focus                                |
| ---------------------------------------------------------------- | --------- | ------------------------------------ |
| [semantic-kernel](https://github.com/microsoft/semantic-kernel)  | Microsoft | AI orchestration framework           |
| [autogen](https://github.com/microsoft/autogen)                  | Microsoft | Multi-agent framework                |
| [kernel-memory](https://github.com/microsoft/kernel-memory)      | Microsoft | RAG & memory management              |
| [extensions](https://github.com/dotnet/extensions)               | .NET      | Microsoft.Extensions.AI abstractions |
| [csharp-sdk](https://github.com/modelcontextprotocol/csharp-sdk) | MCP       | Model Context Protocol for C#        |
| [LangChain](https://github.com/tryAGI/LangChain)                 | tryAGI    | LangChain port for .NET              |

### LLM Provider SDKs

| Repository                                                                 | Owner     | Focus               |
| -------------------------------------------------------------------------- | --------- | ------------------- |
| [openai-dotnet](https://github.com/openai/openai-dotnet)                   | OpenAI    | Official OpenAI SDK |
| [dotnet-genai](https://github.com/googleapis/dotnet-genai)                 | Google    | Google Gemini SDK   |
| [anthropic-sdk-csharp](https://github.com/anthropics/anthropic-sdk-csharp) | Anthropic | Claude SDK          |

### Vector Databases

| Repository                                                                      | Owner    | Focus                     |
| ------------------------------------------------------------------------------- | -------- | ------------------------- |
| [pinecone-dotnet-client](https://github.com/pinecone-io/pinecone-dotnet-client) | Pinecone | Pinecone vector DB client |
| [qdrant-dotnet](https://github.com/qdrant/qdrant-dotnet)                        | Qdrant   | Qdrant vector DB client   |
| [weaviate-dotnet-client](https://github.com/weaviate/weaviate-dotnet-client)    | Weaviate | Weaviate vector DB client |
| [NRedisStack](https://github.com/redis/NRedisStack)                             | Redis    | Redis Stack .NET client   |

### Local LLM & Utilities

| Repository                                              | Owner     | Focus                      |
| ------------------------------------------------------- | --------- | -------------------------- |
| [OllamaSharp](https://github.com/awaescher/OllamaSharp) | awaescher | Ollama .NET client library |

---

## 🔒 Privacy & Security

| Aspect              | Details                                                        |
| ------------------- | -------------------------------------------------------------- |
| **Data Collection** | None. No prompts stored. No analytics.                         |
| **File Access**     | Read-only. Only fetches public GitHub/Microsoft Learn content. |
| **Authentication**  | No auth required                                               |

## ⚡ Rate Limiting

To ensure fair usage and service stability, this server implements IP-based rate limiting:

| Limit Type         | Details                                                     |
| ------------------ | ----------------------------------------------------------- |
| **Requests/IP**    | 20 requests per minute per IP address                       |
| **Window**         | 1 minute rolling window                                     |
| **Queue**          | Up to 5 requests queued when limit reached                  |
| **Response Code**  | `429 Too Many Requests` when exceeded                       |
| **Retry After**    | 60 seconds                                                  |

**Response when rate limit is exceeded:**
```json
{
  "error": "Rate limit exceeded",
  "message": "Too many requests. Please try again later.",
  "retryAfter": "60 seconds"
}
```

**Note:** Rate limits are applied per IP address. If you need higher limits for production use, consider self-hosting.

---

## 📚 Additional Resources

- [Model Context Protocol Specification](https://modelcontextprotocol.io/)
- [Microsoft Learn MCP Server](https://github.com/MicrosoftDocs/mcp)
- [Semantic Kernel Documentation](https://learn.microsoft.com/semantic-kernel/)

---

## 📝 License

[MIT](LICENSE) — Built for the .NET community.

---

<div align="center">

**Made with 💜 for .NET developers who are tired of hallucinated APIs**

</div>
