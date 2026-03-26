# Mini Workflow - n8n Project

## Project Overview

This is an **n8n workflow automation project** containing a simple workflow that fetches Hacker News items. The workflow is defined in `workflow.json` and is designed to run in an n8n instance.

### Workflow Details

| Property | Value |
|----------|-------|
| **Name** | Mini Workflow |
| **ID** | xxxxxxxxxxxxxxxx |
| **Status** | Inactive |
| **Tags** | `panaversity`, `hacker-news` |

### Nodes

1. **When clicking 'Execute workflow'** (Manual Trigger)
   - Type: `n8n-nodes-base.manualTrigger`
   - Position: [0, 0]
   - Initiates the workflow on manual execution

2. **Get many items** (Hacker News)
   - Type: `n8n-nodes-base.hackerNews`
   - Position: [224, 0]
   - Configuration:
     - Resource: `all`
     - Limit: `10` items
     - Keyword: `automation`
   - Note: "News"

### Connections

```
[Manual Trigger] ──main──> [Hacker News: Get many items]
```

## Building and Running

### Prerequisites

- An n8n instance (self-hosted or cloud)
- n8n CLI or access to the n8n editor UI

### Importing the Workflow

1. **Via n8n UI:**
   - Open your n8n instance
   - Go to **Workflows** → **Add workflow**
   - Click the three dots menu → **Import from file**
   - Select `workflow.json`

2. **Via n8n CLI:**
   ```bash
   n8n import:workflow --input=workflow.json
   ```

### Running the Workflow

1. Open the workflow in the n8n editor
2. Click **"Execute workflow"** button to trigger manually
3. The workflow will fetch up to 10 Hacker News items containing the keyword "automation"

## Development Conventions

- **Workflow files** are stored as JSON with the n8n workflow schema
- **Node positioning** uses [x, y] coordinates for visual layout
- **Tags** are used for categorization (`panaversity`, `hacker-news`)
- **Notes** are added to nodes for documentation (`notesInFlow: true`)

## File Structure

```
mini-workflow/
├── workflow.json    # n8n workflow definition
└── README.md          # Project documentation
```
