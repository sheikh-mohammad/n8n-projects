# Hello World Workflow - Project Documentation

## Project Overview

This is an **n8n workflow project** containing a basic "Hello World" workflow. n8n is a workflow automation tool that allows users to create automated workflows through a visual node-based editor.

### Workflow Structure

The workflow (`workflow.json`) consists of:

1. **Manual Trigger Node** - Initiates the workflow when the user clicks "Execute workflow"
2. **Set Node (Edit Fields)** - Sets a variable named `message` with the value `"Hello World"`

### Architecture

```
[Manual Trigger] → [Edit Fields (sets message = "Hello World")]
```

**Workflow Configuration:**
- **Name:** Hello World Workflow
- **ID:** Yr2XvP9P3OCwM4Td
- **Status:** Inactive (`active: false`)
- **Execution Order:** v1

## Building and Running

### Prerequisites

- n8n instance (self-hosted or cloud)
- n8n version compatible with:
  - `n8n-nodes-base.manualTrigger` v1
  - `n8n-nodes-base.set` v3.4

### Importing the Workflow

1. Open your n8n editor
2. Go to **Workflows** → **Import from File**
3. Select `workflow.json`
4. Click **Execute workflow** to test

### Running via CLI (if using n8n CLI)

```bash
# Start n8n
n8n start

# Or with docker
docker run -it --rm --name n8n -p 5678:5678 n8nio/n8n
```

## Development Conventions

### File Structure

- `workflow.json` - n8n workflow definition in JSON format
- `QWEN.md` - This context file for AI assistant interactions

### Workflow JSON Structure

n8n workflows follow this structure:
- `nodes` - Array of workflow nodes with parameters, types, and positions
- `connections` - Defines how nodes are connected
- `settings` - Workflow-level settings
- `meta` - Metadata about the workflow

### Best Practices (Inferred)

- Nodes are positioned on a 2D grid (`position: [x, y]`)
- Each node has a unique `id` and descriptive `name`
- Connections define the flow of data between nodes
- The `main` connection type is used for standard data flow

## Key Files

| File | Description |
|------|-------------|
| `workflow.json` | n8n workflow definition containing nodes, connections, and settings |
| `README` | Project documentation for viewer's assistant |

## Usage

This workflow serves as:
- A starter template for learning n8n workflow creation
- A test workflow for verifying n8n setup
- A base for extending with additional nodes and logic
