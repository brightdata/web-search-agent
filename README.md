<div align="center">
  
## A powerful AI-powered web search assistant built with [Mastra](https://mastra.ai) that can search, extract and crawl the open web and provide accurate, sourced information.
  
<img width="1200" height="404" alt="brightdata-mastra-fixed" src="https://github.com/user-attachments/assets/de4ca0fe-7e09-4f9b-bc02-13d2f222deee" />
</div>


## Overview

This agent combines Google's Gemini 2.5 Flash model with Bright Data's web search capabilities to create an intelligent search assistant that can:

- Search the web for current information on any topic
- Provide accurate, well-sourced responses with citations
- Maintain conversation context with persistent memory
- Return structured, organized results from multiple sources

## Features

- **AI-Powered Responses**: Uses Google Gemini 2.5 Flash for intelligent text generation
- **Web Search Integration**: Leverages Bright Data's MCP (Model Context Protocol) for web scraping and search
- **Persistent Memory**: Maintains conversation history using LibSQL database
- **Source Citations**: Always provides URLs and source attribution
- **Structured Logging**: Built-in logging with Pino for monitoring and debugging

## Architecture

### Core Components

- **Web Search Agent** (`src/mastra/agents/web-search-agent.ts`): Main AI agent with search capabilities
- **Bright Data MCP Client** (`src/mastra/mcp/bright-data-client.ts`): Integration with Bright Data's search API
- **Mastra Core** (`src/mastra/index.ts`): Central configuration and orchestration

### Key Dependencies

- `@mastra/core` - Main framework for agents and workflows
- `@ai-sdk/google` - Google AI integration for Gemini models
- `@mastra/mcp` - Model Context Protocol client
- `@mastra/memory` - Persistent memory management
- `@mastra/libsql` - LibSQL database adapter
- `@mastra/loggers` - Logging utilities

## Requirements

### System Requirements

- **Node.js**: >= 20.9.0
- **npm**: Latest version

### API Keys Required

1. **Bright Data Token**: For web search capabilities
2. **Google AI API Key**: For Gemini model access

## Setup

### 1. Clone and Install

```bash
cd web-search-agent
npm install
```

### 2. Environment Configuration

Copy the example environment file and add your API keys:

```bash
cp .env.example .env
```

Edit `.env` and add your API keys:

```env
BRIGHT_DATA_TOKEN=your_bright_data_token_here
GOOGLE_GENERATIVE_AI_API_KEY=your_google_ai_api_key_here
```

#### Getting API Keys

**Bright Data Token:**
1. Sign up at [Bright Data](https://brightdata.com)
2. Navigate to your dashboard
3. Generate an MCP token for web search

**Google AI API Key:**
1. Go to [Google AI Studio](https://aistudio.google.com)
2. Create a new project or select existing
3. Generate an API key for Gemini models

### 3. Database Setup

The agent uses LibSQL for persistent memory:
- **Development**: Uses in-memory database (`:memory:`)
- **Production**: Uses file-based storage (`file:../mastra.db`)

No additional setup required - the database will be created automatically.

## Usage

### Development Mode

Start the development server with hot reloading:

```bash
npm run dev
```

### Production Build

Build the application:

```bash
npm run build
```

### Start Production Server

```bash
npm run start
```

## Agent Capabilities

The Web Search Agent is designed to:

### Search Operations
- Perform real-time web searches
- Access current information beyond training data
- Handle complex, multi-part queries
- Search across multiple domains and sources

### Response Quality
- Provide accurate, fact-checked information
- Include proper source citations with URLs
- Organize information in clear, readable format
- Summarize key findings from multiple sources

### Memory & Context
- Remember previous conversations
- Build on prior search results
- Maintain context across sessions
- Store search history for reference

## Project Structure

```
web-search-agent/
├── src/
│   └── mastra/
│       ├── agents/
│       │   └── web-search-agent.ts    # Main AI agent
│       ├── mcp/
│       │   └── bright-data-client.ts  # Bright Data integration
│       └── index.ts                   # Mastra configuration
├── .env.example                       # Environment template
├── .gitignore                         # Git ignore rules
├── package.json                       # Dependencies and scripts
├── tsconfig.json                     # TypeScript configuration
└── README.md                         # This file
```

## Configuration

### Agent Settings

The agent is configured in `src/mastra/agents/web-search-agent.ts`:

- **Model**: Google Gemini 2.5 Flash
- **Memory**: Persistent LibSQL storage
- **Tools**: Bright Data web search capabilities
- **Timeout**: 120 seconds for search operations

### Database Configuration

Storage settings in `src/mastra/index.ts`:

- **Development**: In-memory database for fast iteration
- **Production**: File-based storage for persistence

## Troubleshooting

### Common Issues

**"BRIGHT_DATA_TOKEN environment variable is required"**
- Ensure `.env` file exists with valid `BRIGHT_DATA_TOKEN`
- Check that the token is not expired

**"Google AI API key not found"**
- Verify `GOOGLE_GENERATIVE_AI_API_KEY` in `.env`
- Ensure the API key has Gemini model access

**Search timeouts**
- Check internet connectivity
- Verify Bright Data service status
- Consider increasing timeout in `bright-data-client.ts`

### Logging

The application uses Pino for structured logging. Logs include:
- Agent responses and reasoning
- Search API calls and responses
- Error details and stack traces
- Performance metrics

## Development

### Adding New Features

1. **New Tools**: Add to `src/mastra/tools/`
2. **Agent Modifications**: Update `src/mastra/agents/web-search-agent.ts`
3. **Configuration Changes**: Modify `src/mastra/index.ts`

### Testing

Currently no tests are configured. To add testing:

```bash
npm install --save-dev jest @types/jest
```
