---
{"dg-publish":true,"permalink":"/what-does-mcp-stands-for/","dg-note-properties":{}}
---



## MCP stands for **Model Context Protocol**.
### How Does MCP Work in Its Place?

MCP functions as an **orchestration layer** that sits between AI models and enterprise systems[](https://imanage.com/resources/resource-center/blog/agentic-ai-begins-with-model-context-protocol/). In this position, it does not move data out of systems of record—instead, it allows AI to interact directly with systems like document management, knowledge platforms, or CRMs without copying sensitive data to external AI systems[](https://imanage.com/resources/resource-center/blog/agentic-ai-begins-with-model-context-protocol/). The host application manages the coordination, while each server connection maintains isolation so that servers cannot see into other servers or read the full conversation history[](https://modelcontextprotocol.io/specification/2025-11-25/architecture/index).

# ### How Does MCP Work?

MCP operates on a **client-host-server architecture** using **JSON-RPC 2.0** messages for communication[](https://modelcontextprotocol.io/specification/2026-07-28/index.md)[](https://modelcontextprotocol.io/specification/2025-11-25/architecture/index). The process works through the following components:

- **Host**: The AI application (like an IDE or chatbot) that initiates connections and manages security policies[](https://modelcontextprotocol.io/specification/2025-11-25/architecture/index).
    
- **Client**: A connector within the host application that maintains an isolated connection to a specific server[](https://modelcontextprotocol.io/specification/2025-11-25/architecture/index).
    
- **Server**: A service that exposes context and capabilities to the client[](https://modelcontextprotocol.io/specification/2026-07-28/index.md).
    

When a connection is established, the client and server perform **capability negotiation** to declare which features they support[](https://modelcontextprotocol.io/docs/learn/architecture?jid=4837286101). Servers can expose three main types of features:

- **Tools**: Executable functions the AI model can call (e.g., search, calculate, execute SQL)[](https://modelcontextprotocol.io/specification/2026-07-28/index.md)[](https://mktgsite.enterprisedb.com/blog/building-real-time-data-aware-intelligence-postgres-and-model-context-protocol).
    
- **Resources**: Read-only contextual data for the AI to use[](https://modelcontextprotocol.io/specification/2026-07-28/index.md).
    
- **Prompts**: Reusable templates and workflows[](https://modelcontextprotocol.io/specification/2026-07-28/index.md).
    

For example, when a user asks an AI to "Show me top 5 customers by revenue," the LLM doesn't guess. It discovers the database schema step by step, learns the table and column names, and then executes the query with proper access controls[](https://mktgsite.enterprisedb.com/blog/building-real-time-data-aware-intelligence-postgres-and-model-context-protocol).

### What is MCP?

The **Model Context Protocol (MCP)** is an open-source standard that enables AI applications to connect with external systems, data sources, and tools in a uniform way[](https://modelcontextprotocol.io/docs/draft/getting-started/intro). It was developed by Anthropic to act as a "universal translator" or a "USB-C port for AI applications," allowing AI models like Claude or ChatGPT to access key information and perform tasks outside their built-in knowledge[](https://modelcontextprotocol.io/docs/draft/getting-started/intro)[](https://research.lbl.gov/2025/09/22/model-context-protocol-an-ai-tool-for-seamless-access-to-data-scientific-resources/?utm_source=LBNL&utm_campaign=fd23a3eeb0-EMAIL_CAMPAIGN_2022_09_08_12_39_COPY_01&utm_medium=email&utm_term=0_1d5d2d8c73-fd23a3eeb0-295863835).

### What is MCP?

The **Model Context Protocol (MCP)** is an open-source standard that enables AI applications to connect with external systems, data sources, and tools in a uniform way[](https://modelcontextprotocol.io/docs/draft/getting-started/intro). It was developed by Anthropic to act as a "universal translator" or a "USB-C port for AI applications," allowing AI models like Claude or ChatGPT to access key information and perform tasks outside their built-in knowledge[](https://modelcontextprotocol.io/docs/draft/getting-started/intro)[](https://research.lbl.gov/2025/09/22/model-context-protocol-an-ai-tool-for-seamless-access-to-data-scientific-resources/?utm_source=LBNL&utm_campaign=fd23a3eeb0-EMAIL_CAMPAIGN_2022_09_08_12_39_COPY_01&utm_medium=email&utm_term=0_1d5d2d8c73-fd23a3eeb0-295863835).

### How Does MCP Work?

MCP operates on a **client-host-server architecture** using **JSON-RPC 2.0** messages for communication[](https://modelcontextprotocol.io/specification/2026-07-28/index.md)[](https://modelcontextprotocol.io/specification/2025-11-25/architecture/index). The process works through the following components:

- **Host**: The AI application (like an IDE or chatbot) that initiates connections and manages security policies[](https://modelcontextprotocol.io/specification/2025-11-25/architecture/index).
    
- **Client**: A connector within the host application that maintains an isolated connection to a specific server[](https://modelcontextprotocol.io/specification/2025-11-25/architecture/index).
    
- **Server**: A service that exposes context and capabilities to the client[](https://modelcontextprotocol.io/specification/2026-07-28/index.md).
    

When a connection is established, the client and server perform **capability negotiation** to declare which features they support[](https://modelcontextprotocol.io/docs/learn/architecture?jid=4837286101). Servers can expose three main types of features:

- **Tools**: Executable functions the AI model can call (e.g., search, calculate, execute SQL)[](https://modelcontextprotocol.io/specification/2026-07-28/index.md)[](https://mktgsite.enterprisedb.com/blog/building-real-time-data-aware-intelligence-postgres-and-model-context-protocol).
    
- **Resources**: Read-only contextual data for the AI to use[](https://modelcontextprotocol.io/specification/2026-07-28/index.md).
    
- **Prompts**: Reusable templates and workflows[](https://modelcontextprotocol.io/specification/2026-07-28/index.md).
    

For example, when a user asks an AI to "Show me top 5 customers by revenue," the LLM doesn't guess. It discovers the database schema step by step, learns the table and column names, and then executes the query with proper access controls[](https://mktgsite.enterprisedb.com/blog/building-real-time-data-aware-intelligence-postgres-and-model-context-protocol).