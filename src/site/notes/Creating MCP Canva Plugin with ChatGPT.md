---
{"dg-publish":true,"permalink":"/creating-mcp-canva-plugin-with-chat-gpt/","dg-note-properties":{}}
---

see:[[MCP\|MCP]]
Building a **Canva MCP Server / Plugin for ChatGPT** creates a bridge that lets ChatGPT interact directly with a user’s Canva account via the **Model Context Protocol (MCP)** standard.

Instead of copying and pasting content manually, ChatGPT can inspect Canva templates, generate designs, autofill brand templates, add comments, or export completed graphics—all driven by natural language prompts.

## Architecture: How It Works Under the Hood

The setup consists of three primary layers communicating over standardized protocols:

```
┌─────────────────┐       JSON-RPC      ┌─────────────────────────┐       HTTPS / REST       ┌───────────────────┐
│     ChatGPT     │  ◄───────────────►  │    Canva MCP Server     │  ◄────────────────────►  │     Canva API     │
│  (MCP Client)   │    (Streamable      │ (Node.js / Python app)  │    (OAuth 2.0 Auth)      │ (REST Endpoints)  │
└─────────────────┘       HTTP/SSE)     └─────────────────────────┘                          └───────────────────┘
```

1. **ChatGPT (MCP Client):** Reads user prompts (e.g., _"Generate a social media poster for a pizza grand opening"_), analyzes available tools registered on your server, and formats tool calls into standard JSON-RPC payloads.
    
2. **Canva MCP Server (Middle Layer):** A server (built with TypeScript/Node.js or Python) that exposes Canva's capabilities as **MCP Tools**. It receives the model's tool calls, verifies OAuth access tokens, and executes HTTP requests against the official Canva API.
    
3. **Canva REST API:** Performs actions in the user's Canva workspace (such as searching designs, autofilling datasets, or running generation pipelines) and returns data back through the server to ChatGPT.
    

## Key Steps to Build and Connect It

### 1. Register a Canva Developer App

- Go to the **Canva Developers Portal** and create a integration app.
    
- Set up your **OAuth 2.0 Client Credentials** (Client ID & Client Secret).
    
- Request the necessary API scopes (e.g., `design:read`, `design:meta:read`, `brandkit:read`, `folder:read`, etc.).
    

### 2. Implement the MCP Server

Using the official Model Context Protocol SDK (available in TypeScript or Python), define your tools and schemas:

- **Tools Discovery:** Respond to MCP `tools/list` requests by exposing functions like `search_brand_templates`, `generate_design`, `autofill_design`, or `get_design_content`.
    
- **Execution Handlers:** Respond to `tools/call` by executing the corresponding Canva REST API calls.
    
- **Authentication:** Implement OAuth token handling so ChatGPT can authenticate users securely.
    

TypeScript

```
// Example: TypeScript snippet using @modelcontextprotocol/sdk
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { ListToolsRequestSchema, CallToolRequestSchema } from "@modelcontextprotocol/sdk/types.js";

const server = new Server({ name: "canva-mcp-server", version: "1.0.0" });

// 1. Expose Canva tools to ChatGPT
server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [
    {
      name: "search_brand_templates",
      description: "Searches available Canva brand templates for autofilling content.",
      inputSchema: {
        type: "object",
        properties: {
          query: { type: "string", description: "Search query string" }
        }
      }
    }
  ]
}));

// 2. Handle execution requests from ChatGPT
server.setRequestHandler(CallToolRequestSchema, async (request) => {
  if (request.params.name === "search_brand_templates") {
    const { query } = request.params.arguments;
    // Call official Canva REST API using user's access token
    const response = await fetch(`https://api.canva.com/v1/brand-templates?query=${query}`, {
      headers: { Authorization: `Bearer ${userAccessToken}` }
    });
    const data = await response.json();
    return { content: [{ type: "text", text: JSON.stringify(data) }] };
  }
});
```

### 3. Connect the MCP Server to ChatGPT

1. **Deploy your MCP server:** Host it on a cloud platform (Vercel, Render, AWS, Fly.io) so it has a publicly accessible HTTPS endpoint (or test locally using a secure tunnel).
    
2. **Enable Developer Mode in ChatGPT:** Navigate to **Settings → Security & Login → Developer mode**.
    
3. **Add the Server as a Developer App/Plugin:**
    
    - In ChatGPT, navigate to the **Plugins / Developer Tools** section.
        
    - Click **+ Add App / Connection** and paste your server's endpoint URL (e.g., `[https://your-canva-mcp.com/mcp](https://your-canva-mcp.com/mcp)`).
        
    - Authenticate via Canva's OAuth prompt when asked.
        

## Example User Workflow in ChatGPT

Once connected, a interaction proceeds smoothly:

1. **User Request:** _"Find my company's 'Newsletter' brand template on Canva and autofill it with our product updates for October."_
    
2. **Tool Discovery:** ChatGPT reads your MCP tool definitions and identifies `search_brand_templates` and `autofill_design` as the appropriate tools.
    
3. **Execution:**
    
    - ChatGPT sends a request to your MCP server to search for "Newsletter" templates.
        
    - The server queries Canva and returns the template ID and schema.
        
    - ChatGPT populates the dataset matching the schema and issues an `autofill_design` tool call.
        
4. **Final Response:** ChatGPT presents the newly created Canva design link and thumbnail directly inside the conversation.