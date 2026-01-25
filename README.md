<div align="center">

# DotNet AI MCP Server

### _The essential Model Context Protocol server for .NET developers building AI applications_

[![MCP](https://img.shields.io/badge/MCP-Compliant-5A67D8?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0wIDE4Yy00LjQxIDAtOC0zLjU5LTgtOHMzLjU5LTggOC04IDggMy41OSA4IDgtMy41OSA4LTggOHoiLz48L3N2Zz4=)](https://modelcontextprotocol.io)
[![.NET 9](https://img.shields.io/badge/.NET-9.0-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![NuGet](https://img.shields.io/badge/NuGet-DotNetAIMcpServer-blue?style=for-the-badge)](https://www.nuget.org/packages/DotNetAIMcpServer)
[![npm](https://img.shields.io/badge/npm-dotnet--ai--mcp--server-red?style=for-the-badge)](https://www.npmjs.com/package/dotnet-ai-mcp-server)

<br/>

[Quick Start](#-quick-start) |
[Why This Exists](#-the-problem--solution) |
[Tools](#%EF%B8%8F-available-tools) |
[Tracked Repos](#-tracked-repositories)

</div>

---

## Quick Start

### Claude Desktop

Add to your Claude Desktop config (`~/Library/Application Support/Claude/claude_desktop_config.json` on macOS, `%APPDATA%\Claude\claude_desktop_config.json` on Windows):

```json
{
  "mcpServers": {
    "dotnet-ai": {
      "command": "npx",
      "args": ["-y", "dotnet-ai-mcp-server"]
    }
  }
}
```

### VS Code / GitHub Copilot

Add to your VS Code settings (`settings.json`):

```json
{
  "mcp": {
    "servers": {
      "dotnet-ai": {
        "command": "npx",
        "args": ["-y", "dotnet-ai-mcp-server"]
      }
    }
  }
}
```

### Prerequisites

- [.NET 9.0 SDK](https://dotnet.microsoft.com/download) - The underlying tool is built with .NET
- Node.js 16+ - For npx

### Alternative: Direct dotnet tool

If you prefer not to use npm/npx:

```bash
# Install once
dotnet tool install -g DotNetAIMcpServer

# Then use in your MCP config:
{
  "mcpServers": {
    "dotnet-ai": {
      "command": "dotnet-ai-mcp"
    }
  }
}
```

---

## The Problem & Solution

### The Problem

Ask any LLM about **Semantic Kernel**, **Microsoft.Extensions.AI**, or **MCP in .NET** and you'll likely get:

- Hallucinated APIs that don't exist
- Outdated syntax from deprecated packages
- Confident but wrong code examples

The .NET AI ecosystem moves fast. Training data can't keep up.

### The Solution

This MCP server fetches **real code** from live GitHub repositories:

| Source              | What You Get                                                                         |
| ------------------- | ------------------------------------------------------------------------------------ |
| **GitHub Repos**    | Live code & docs from `semantic-kernel`, `openai-dotnet`, `mcp-csharp-sdk`, and more |
| **Microsoft Learn** | Official documentation with optimized token usage                                    |

#### Token Optimization

- **Gradual data exposure** - Starts with repo/folder structure, only fetches file content when needed
- **Filtered results** - Excludes test folders, build outputs, and irrelevant content
- **Truncated summaries** - Documentation snippets optimized for context windows
- **C#-only filtering** - Code samples pre-filtered to .NET languages

---

## Available Tools

### Zero-Configuration Agentic Workflow

Just ask naturally:

> _"How do I create a chat completion with Semantic Kernel?"_

The LLM automatically orchestrates the tools in sequence: **repositories -> folders -> files -> code**.

### GitHub Tools

| Tool                     | What It Does                           |
| ------------------------ | -------------------------------------- |
| `Start_DotNet_Reasoning` | Lists all tracked .NET AI repositories |
| `GitHubGetFolders`       | Shows folder structure of a repository |
| `GitHubListFiles`        | Lists files in specific folders        |
| `GitHubFetchFiles`       | Retrieves actual file content          |

### Microsoft Learn Tools

| Tool                           | What It Does                           |
| ------------------------------ | -------------------------------------- |
| `MicrosoftDocsSearch`          | Searches Microsoft Learn documentation |
| `MicrosoftDocsFetch`           | Fetches full documentation page        |
| `MicrosoftCodeSampleSearch`    | Finds official code samples            |

---

## Optional: Session Prompt

A built-in prompt (`dotnet-ai-session`) reinforces the agentic workflow:

```
/prompt dotnet-ai-session
```

---

## Tracked Repositories

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

### Local LLM

| Repository                                              | Owner     | Focus                      |
| ------------------------------------------------------- | --------- | -------------------------- |
| [OllamaSharp](https://github.com/awaescher/OllamaSharp) | awaescher | Ollama .NET client library |

---

## Privacy & Security

| Aspect              | Details                                                |
| ------------------- | ------------------------------------------------------ |
| **Data Collection** | None. No prompts stored. No analytics.                 |
| **File Access**     | Read-only. Only fetches public GitHub/Microsoft Learn. |
| **Authentication**  | No auth required from users.                           |

---

## Additional Resources

- [Model Context Protocol Specification](https://modelcontextprotocol.io/)
- [Microsoft Learn MCP Server](https://github.com/MicrosoftDocs/mcp)
- [Semantic Kernel Documentation](https://learn.microsoft.com/semantic-kernel/)

---

## License

[MIT](LICENSE) - Built for the .NET community.

---

<div align="center">

**Made for .NET developers who are tired of hallucinated APIs**

</div>
