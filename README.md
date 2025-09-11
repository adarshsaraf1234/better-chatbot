


### Quick Start 

```bash
# 1. Clone the repository

git clone https://github.com/cgoinglove/better-chatbot.git
cd better-chatbot

# 2. (Optional) Install pnpm if you don't have it

npm install -g pnpm

# 3. Install dependencies

pnpm i

# 4. (Optional) Start a local PostgreSQL instance

pnpm docker:pg

# If you already have your own PostgreSQL running, you can skip this step.
# In that case, make sure to update the PostgreSQL URL in your .env file.

# 5. Enter required information in the .env file

# The .env file is created automatically. Just fill in the required values.
# For the fastest setup, provide at least one LLM provider's API key (e.g., OPENAI_API_KEY, CLAUDE_API_KEY, GEMINI_API_KEY, etc.) and the PostgreSQL URL you want to use.

# 6. Start the server

pnpm build:local && pnpm start

# (Recommended for most cases. Ensures correct cookie settings.)
# For development mode with hot-reloading and debugging, you can use:
# pnpm dev
```


> This project is evolving at lightning speed! ⚡️ We're constantly shipping new features and smashing bugs. **Star this repo** to join the ride and stay in the loop with the latest updates!

## Preview

Get a feel for the UX — here's a quick look at what's possible.

### 🧩 Browser Automation with Playwright MCP

![preview](https://github.com/user-attachments/assets/e4febb04-26d5-45da-a7bb-f7d452d333c2)


**Example:** Control a web browser using Microsoft's [playwright-mcp](https://github.com/microsoft/playwright-mcp) tool.

- The LLM autonomously decides how to use tools from the MCP server, calling them multiple times to complete a multi-step task and return a final message.

Sample prompt:

```prompt
1. Use the @tool('web-search') to look up information about “modelcontetprotocol.”

2. Then, using : @mcp("playwright")
   - navigate Google (https://www.google.com)
   - Click the “Login” button
   - Enter my email address (neo.cgoing@gmail.com)
   - Clock the "Next"  button
   - Close the browser
```

<br/>

### 🔗 Visual Workflows as Custom Tools

<img width="1912" height="953" alt="workflow" loading="lazy" src="https://github.com/user-attachments/assets/e69e72e8-595c-480e-b519-4531f4c6331f" />

<img width="1567" alt="workflow-mention" loading="lazy" src="https://github.com/user-attachments/assets/cf3e1339-ee44-4615-a71d-f6b46833e41f" />

**Example:** Create custom workflows that become callable tools in your chat conversations.

- Build visual workflows by connecting LLM nodes (for AI reasoning) and Tool nodes (for MCP tool execution)
- Publish workflows to make them available as `@workflow_name` tools in chat
- Chain complex multi-step processes into reusable, automated sequences




### ⚡️ Quick Tool Mentions (`@`) & Presets

<img width="1225" alt="image" src="https://github.com/user-attachments/assets/dfe76b3b-c3d8-436e-8a7c-7b23292e234c" loading="lazy"/>

Quickly call tool during chat by typing `@toolname`.
No need to memorize — just type `@` and pick from the list!

**Tool Selection vs. Mentions (`@`) — When to Use What:**

- **Tool Selection**: Make frequently used tools always available to the LLM across all chats. Great for convenience and maintaining consistent context over time.
- **Mentions (`@`)**: Temporarily bind only the mentioned tools for that specific response. Since only the mentioned tools are sent to the LLM, this saves tokens and can improve speed and accuracy.

Each method has its own strengths — use them together to balance efficiency and performance.

You can also create **tool presets** by selecting only the MCP servers or tools you need.
Switch between presets instantly with a click — perfect for organizing tools by task or workflow.

### 🧭 Tool Choice Mode

<img width="1225" alt="image" src="https://github.com/user-attachments/assets/8fc64c6a-30c9-41a4-a5e5-4e8804f73473" loading="lazy"/>

Control how tools are used in each chat with **Tool Choice Mode** — switch anytime with `⌘P`.

- **Auto:** The model automatically calls tools when needed.
- **Manual:** The model will ask for your permission before calling a tool.
- **None:** Tool usage is disabled completely.

This lets you flexibly choose between autonomous, guided, or tool-free interaction depending on the situation.

### 🛠️ Default Tools

#### 🌐 Web Search

<img width="1034" height="940" alt="web-search" src="https://github.com/user-attachments/assets/261037d9-e1a7-44ad-b45e-43780390a94e" />

Built-in web search powered by [Exa AI](https://exa.ai). Search the web with semantic AI and extract content from URLs directly in your chats.

- **Optional:** Add `EXA_API_KEY` to `.env` to enable web search
- **Free Tier:** 1,000 requests/month at no cost, no credit card required
- **Easy Setup:** Get your API key instantly at [dashboard.exa.ai](https://dashboard.exa.ai)

#### ⚡️ JS,PYTHON Executor

<img width="1225" alt="js-executor-preview" src="https://github.com/user-attachments/assets/7deed824-e70b-46d4-a294-de20ed4dc869" loading="lazy"/>

It is a simple JS execution tool.

#### 📊 Data Visualization Tools

**Interactive Tables**: Create feature-rich data tables with advanced functionality:

- **Sorting & Filtering**: Sort by any column, filter data in real-time
- **Search & Highlighting**: Global search with automatic text highlighting
- **Export Options**: Export to CSV or Excel format with lazy-loaded libraries
- **Column Management**: Show/hide columns with visibility controls
- **Pagination**: Handle large datasets with built-in pagination
- **Data Type Support**: Proper formatting for strings, numbers, dates, and booleans

**Chart Generation**: Visualize data with various chart types (bar, line, pie charts)

> Additionally, many other tools are provided, such as an HTTP client for API requests and more.

<br/>

…and there's even more waiting for you.
Try it out and see what else it can do!

<br/>

## Getting Started

> This project uses [pnpm](https://pnpm.io/) as the recommended package manager.

```bash
# If you don't have pnpm:
npm install -g pnpm
```

### Quick Start (Docker Compose Version) 🐳

```bash
# 1. Install dependencies
pnpm i

# 2. Enter only the LLM PROVIDER API key(s) you want to use in the .env file at the project root.
# Example: The app works with just OPENAI_API_KEY filled in.
# (The .env file is automatically created when you run pnpm i.)

# 3. Build and start all services (including PostgreSQL) with Docker Compose
pnpm docker-compose:up

```

### Quick Start (Local Version) 🚀

```bash
pnpm i

#(Optional) Start a local PostgreSQL instance
# If you already have your own PostgreSQL running, you can skip this step.
# In that case, make sure to update the PostgreSQL URL in your .env file.
pnpm docker:pg

# Enter required information in the .env file
# The .env file is created automatically. Just fill in the required values.
# For the fastest setup, provide at least one LLM provider's API key (e.g., OPENAI_API_KEY, CLAUDE_API_KEY, GEMINI_API_KEY, etc.) and the PostgreSQL URL you want to use.

pnpm build:local && pnpm start

# (Recommended for most cases. Ensures correct cookie settings.)
# For development mode with hot-reloading and debugging, you can use:
# pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to get started.

<br/>

### Environment Variables

The `pnpm i` command generates a `.env` file. Add your API keys there.

```dotenv
# === LLM Provider API Keys ===
# You only need to enter the keys for the providers you plan to use
GOOGLE_GENERATIVE_AI_API_KEY=****
OPENAI_API_KEY=****
XAI_API_KEY=****
ANTHROPIC_API_KEY=****
OPENROUTER_API_KEY=****
OLLAMA_BASE_URL=http://localhost:11434/api



# Secret for Better Auth (generate with: npx @better-auth/cli@latest secret)
BETTER_AUTH_SECRET=****

# (Optional)
# URL for Better Auth (the URL you access the app from)
BETTER_AUTH_URL=

# === Database ===
# If you don't have PostgreSQL running locally, start it with: pnpm docker:pg
POSTGRES_URL=postgres://your_username:your_password@localhost:5432/your_database_name

# (Optional)
# === Tools ===
# Exa AI for web search and content extraction (optional, but recommended for @web and research features)
EXA_API_KEY=your_exa_api_key_here


# Whether to use file-based MCP config (default: false)
FILE_BASED_MCP_CONFIG=false

# (Optional)
# === OAuth Settings ===
# Fill in these values only if you want to enable Google/GitHub/Microsoft login

#GitHub
GITHUB_CLIENT_ID=
GITHUB_CLIENT_SECRET=

#Google
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
# Set to 1 to force account selection
GOOGLE_FORCE_ACCOUNT_SELECTION=


# Microsoft
MICROSOFT_CLIENT_ID=
MICROSOFT_CLIENT_SECRET=
# Optional Tenant Id
MICROSOFT_TENANT_ID=
# Set to 1 to force account selection
MICROSOFT_FORCE_ACCOUNT_SELECTION=

# Set this to 1 to disable user sign-ups.
DISABLE_SIGN_UP=

# Set this to 1 to disallow adding MCP servers.
NOT_ALLOW_ADD_MCP_SERVERS=
```

<br/>



- Comprehensive end-to-end testing with Playwright including multi-user scenarios, agent visibility testing, and CI/CD integration
  <br/>

## 💡 Tips

#### [💬 Temporary Chat Windows](./docs/tips-guides/temporary_chat.md)

- Open lightweight popup chats for quick side questions or testing — separate from your main thread.

## 🗺️ Roadmap

Planned features coming soon to better-chatbot:


