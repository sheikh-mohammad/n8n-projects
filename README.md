# n8n Workflows Collection

## Project Overview

This directory contains a collection of **[n8n](https://n8n.io/) workflow automation projects**. n8n is a fair-code licensed workflow automation tool that allows you to connect apps and services together to automate tasks.

Each subdirectory represents a standalone workflow that can be imported into an n8n instance. Workflows are defined in `workflow.json` files following the n8n workflow export format.

## Directory Structure

```
n8n-projects/
├── hello-world-workflow/       # Basic "Hello World" example workflow
├── mini-workflow/              # Hacker News fetcher with keyword filter
├── first-agent/                # AI chat agent using Google Gemini
├── daily-remainder-gmail/      # Scheduled Gmail reminder
├── customer-support-data/      # Customer support test workflow
├── hacker-news-automation/     # Scheduled Hacker News scraper
├── nasa-solar-flare/           # NASA solar flare monitoring (active)
└── README.md                   # Project Documentation - This File
```

## Workflow Descriptions

### 1. Hello World Workflow (`hello-world-workflow/`)
- **Purpose**: Basic introductory workflow demonstrating n8n fundamentals
- **Trigger**: Manual trigger (click to execute)
- **Nodes**: ManualTrigger → Set (creates a "Hello World" message)
- **Use Case**: Learning n8n basics, testing workflow execution

### 2. Mini Workflow (`mini-workflow/`)
- **Purpose**: Fetches Hacker News stories with keyword filtering
- **Trigger**: Manual trigger
- **Nodes**: ManualTrigger → HackerNews (fetches top stories with "automation" keyword)
- **Tags**: `panaversity`, `hacker-news`
- **Use Case**: News aggregation, content monitoring

### 3. First Agent (`first-agent/`)
- **Purpose**: AI-powered chat agent with conversation memory
- **Trigger**: Chat message trigger (webhook-based)
- **Nodes**: ChatTrigger → AI Agent → Google Gemini Chat Model + Simple Memory
- **Credentials Required**: Google Gemini API
- **Use Case**: Conversational AI assistant, chatbot development

### 4. Daily Remainder Gmail (`daily-remainder-gmail/`)
- **Purpose**: Sends scheduled email reminders via Gmail
- **Trigger**: Schedule trigger (daily at 08:10 Asia/Karachi timezone)
- **Nodes**: ScheduleTrigger → Gmail (sends email)
- **Credentials Required**: Gmail OAuth2
- **Use Case**: Daily reminders, notifications, scheduled communications

### 5. Customer Support Test (`customer-support-data/`)
- **Purpose**: Customer support testing workflow using n8n training nodes
- **Trigger**: Manual trigger
- **Nodes**: ManualTrigger → Customer Datastore → Edit Fields → Customer Messenger
- **Use Case**: Testing customer support flows, n8n training exercises

### 6. Hacker News Automation (`hacker-news-automation/`)
- **Purpose**: Automated Hacker News monitoring
- **Trigger**: Schedule trigger (daily at 09:00)
- **Nodes**: ScheduleTrigger → HackerNews (fetches "automation" keyword stories)
- **Use Case**: Automated news monitoring, content aggregation

### 7. NASA Solar Flare (`nasa-solar-flare/`)
- **Purpose**: Monitors NASA DONKI solar flare data and sends alerts
- **Trigger**: Schedule trigger (daily at 20:45 Asia/Karachi)
- **Nodes**: ScheduleTrigger → NASA API → If (filter M-class flares) → PostBin (alerts)
- **Credentials Required**: NASA API
- **Status**: **Active** (only workflow with `active: true`)
- **Use Case**: Space weather monitoring, scientific alerts

## Building and Running

### Prerequisites

1. **n8n Instance**: You need access to an n8n instance (self-hosted or cloud)
   - Self-hosted: `npm install n8n -g` then `n8n start`
   - Cloud: [n8n.cloud](https://n8n.io/cloud/)

2. **Credentials Setup**: Some workflows require API credentials:
   - **Google Gemini API**: For AI chat agent
   - **Gmail OAuth2**: For email sending workflows
   - **NASA API**: For solar flare monitoring

### Importing Workflows

1. Open your n8n instance
2. Go to **Workflows** → **Add Workflow**
3. Click the three dots menu → **Import from File**
4. Select the `workflow.json` file from the desired workflow directory
5. Configure required credentials when prompted
6. Activate the workflow (toggle the active switch)

### Running Workflows

- **Manual Trigger Workflows**: Click "Execute Workflow" button in n8n editor
- **Scheduled Workflows**: Run automatically based on configured schedule
- **Chat Trigger Workflows**: Access via the chat webhook URL provided by n8n

## Development Conventions

### Workflow Naming
- Use descriptive, title-case names (e.g., "NASA Solar Flare")
- Match directory names to workflow names (kebab-case)

### File Structure
- `workflow.json`: The main workflow definition (required)
- `workflow.png`: Screenshot of the workflow in n8n editor (optional)
- `README.md`: Workflow-specific documentation (optional)
- `LICENSE`: License file (optional)

### Best Practices Observed

1. **Timezone Configuration**: Workflows with schedule triggers specify timezone (`Asia/Karachi`)
2. **Execution Order**: All workflows use `v1` execution order
3. **Credential Management**: Credentials are referenced by ID and name
4. **Tagging**: Some workflows use tags for organization (e.g., `hacker-news`, `chat-gpt`)
5. **Active Status**: Most workflows are inactive by default; activate after credential setup

## Credentials Reference

| Workflow | Required Credential | Purpose |
|----------|-------------------|---------|
| first-agent | Google Gemini API | AI language model |
| daily-remainder-gmail | Gmail OAuth2 | Sending emails |
| nasa-solar-flare | NASA API | Fetching solar flare data |

## Notes

- All workflows share the same n8n instance ID, indicating they were exported from the same n8n installation
- The `travel-agent/` directory appears to be empty or not yet populated
- The `customer-support-data/` folder contains `worflow.json` (typo) instead of `workflow.json`

## Useful Commands

```bash
# Start n8n locally
n8n start

# Start n8n with tunnel (for webhook testing)
n8n start --tunnel

# Import workflow via CLI (if using n8n CLI)
n8n import:workflow --input=workflow.json
```

## Resources

- [n8n Documentation](https://docs.n8n.io/)
- [n8n Workflow Export/Import](https://docs.n8n.io/hosting/cli-commands/#import-and-export)
- [n8n Node Reference](https://docs.n8n.io/integrations/)
