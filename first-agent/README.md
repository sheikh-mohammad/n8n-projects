# First Agent - n8n Workflow Project

## Project Overview

This directory contains an **n8n automation workflow** named "First Agent". It implements a conversational AI chat agent using Google's Gemini language model with memory capabilities.

### Architecture

The workflow consists of 4 nodes connected in a linear flow:

| Node | Type | Purpose |
|------|------|---------|
| **When chat message received** | Chat Trigger | Entry point that captures incoming chat messages |
| **AI Agent** | LangChain Agent | Core processing unit that handles conversation logic |
| **Google Gemini Chat Model** | Language Model | AI model provider (Google Gemini/PaLM) for generating responses |
| **Simple Memory** | Memory Buffer | Maintains conversation context using window-based memory |

### Data Flow

```
Chat Message → AI Agent (with Gemini LM + Memory) → Response
```

## Key Files

| File | Description |
|------|-------------|
| `workflow.json` | The n8n workflow definition containing all node configurations and connections |
| `workflow.png` | Visual diagram of the workflow |
| `demo_chat.png` | Screenshot demonstrating the chat functionality |
| `README.md` | This documentation file |

## Prerequisites

- **n8n instance** (self-hosted or cloud)
- **Google Gemini API credentials** configured in n8n
  - Credential name: `Google Gemini(PaLM) Api account`
  - Credential ID: `xxxxxxxxxxxxxxxx`

## Usage

### Importing the Workflow

1. Open your n8n instance
2. Go to **Workflows** → **Import from File**
3. Select `workflow.json`
4. Ensure the Google Gemini credentials are configured

### Running the Workflow

1. Activate the workflow using the toggle in n8n
2. Send a message to the chat trigger endpoint
3. The AI Agent will process the message using Google Gemini and return a response

### Webhook Information

- **Webhook ID**: `f6e60897-6876-4d1b-9c22-d35e036d10a5`
- Use this ID to construct the webhook URL for your n8n instance

## Configuration Details

### Node Versions

- Chat Trigger: `v1.3`
- AI Agent: `v2.2`
- Google Gemini Chat Model: `v1`
- Memory Buffer Window: `v1.3`

### Current Status

- **Active**: `false` (workflow is currently inactive)
- **Execution Order**: `v1`

## Development Notes

- The workflow uses LangChain nodes (`@n8n/n8n-nodes-langchain.*`)
- Memory is configured with a simple buffer window to maintain conversation context
- No custom parameters are set; all nodes use default `options: {}`

## Troubleshooting

1. **Workflow not triggering**: Ensure the workflow is activated and the webhook URL is correct
2. **AI not responding**: Verify Google Gemini API credentials are valid and have quota
3. **Memory not working**: Check that the memory node is properly connected to the AI Agent
