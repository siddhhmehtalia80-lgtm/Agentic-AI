---
{"dg-publish":true,"permalink":"/module-context-protocol/","dg-note-properties":{}}
---

The **Model Context Protocol (MCP)** is an open standard and open-source framework created to solve a common problem in AI development: **how AI models securely connect to external tools, databases, and local applications.**

Before MCP, every time developers wanted an AI model (like Claude, ChatGPT, or an IDE assistant) to interact with a specific tool—such as GitHub, Postgres databases, Google Drive, or local files—they had to write custom, one-off integrations (APIs or plugins) for each platform.

MCP acts like **USB-C for AI apps**: it provides a single universal standard so any AI application can instantly connect to any supported data source or tool without needing a unique connector.

## How MCP Works

MCP uses a **Client-Server Architecture**. Communication typically runs over standard JSON-RPC protocol over `stdio` (local process execution) or `HTTP with SSE/WebSockets` (remote network connections).

```
               +-------------------------------------------------+
               |                    MCP Host                     |
               |         (e.g., Claude Desktop, Cursor)          |
               +-----------------------+-------------------------+
                                       |
                   +-------------------+-------------------+
                   |                                       |
                   v                                       v
         [ MCP Client 1 ]                        [ MCP Client 2 ]
                   |                                       |
                   | (JSON-RPC)                            | (JSON-RPC)
                   v                                       v
         [ MCP Server 1 ]                        [ MCP Server 2 ]
    (e.g., Postgres Database)                  (e.g., GitHub API)
```

### Key Components

1. **MCP Host:** The main AI application or environment you interact with (e.g., Claude Desktop, an IDE like Cursor, or an AI agent framework).
    
2. **MCP Client:** A light internal module managed by the Host that maintains a 1-to-1 connection to a specific MCP Server.
    
3. **MCP Server:** A lightweight, specialized program that wraps around a specific dataset or utility (like your local file system, a Slack workspace, or an SQL database) and exposes standard primitives to the client.
    

## What Can an MCP Server Provide?

An MCP Server provides three primary building blocks ("primitives") to the AI model:

|**Primitive**|**Description**|**Example Use Case**|
|---|---|---|
|**Resources**|Static or dynamic data context that the AI model can read.|Reading local code files, system logs, or database schemas.|
|**Tools**|Executable actions that the AI model can run (with user authorization).|Sending an email, creating a GitHub issue, or executing a SQL query.|
|**Prompts**|Reusable templates pre-configured by the server creator.|Preset prompt workflows, like "Summarize database table" or "Analyze Git diff."|

## Why MCP Matters

- **Eliminates Custom Integrations:** Developers write one MCP server for their tool, and it immediately works across all AI applications supporting the protocol.
    
- **Keeps Data Secure:** Rather than uploading raw databases or entire directories into a remote AI context, local MCP servers can act as secure gatekeepers that only supply requested data.
    
- **Empowers Autonomous Agents:** Gives AI agents structured, standard ways to discover available tools and execute actions dynamically across different software environments.