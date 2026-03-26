# Customer Support Data - n8n Workflow Project

## Directory Overview

This directory contains an **n8n automation workflow** designed for customer support operations. It demonstrates a simple customer data processing pipeline using n8n's built-in training nodes for educational/testing purposes.

### Purpose
The workflow automates the process of:
1. Retrieving customer data from a training datastore
2. Transforming and mapping customer fields to a standardized format
3. Sending personalized messages to customers based on their data

## Key Files

| File | Description |
|------|-------------|
| `worflow.json` | n8n workflow definition file containing node configurations and connections (note: filename contains typo - "worflow" instead of "workflow") |
| `workflow.png` | Visual diagram/screenshot of the workflow layout |
| `README.md` | Project documentation for AI assistants |

## Workflow Architecture

### Node Structure
The workflow consists of 4 nodes connected in a linear sequence:

| Order | Node Name | Type | Function |
|-------|-----------|------|----------|
| 1 | When clicking 'Execute workflow' | Manual Trigger | Initiates the workflow on-demand |
| 2 | Customer Datastore (n8n training) | Data Source | Retrieves up to 10 customer records |
| 3 | Edit Fields | Set/Transform | Maps customer data to standardized fields |
| 4 | Customer Messenger (n8n training) | Output | Sends personalized messages |

### Data Flow
```
Manual Trigger → Customer Datastore → Edit Fields → Customer Messenger
```

### Field Mappings (Edit Fields Node)
| Output Field | Source Field |
|--------------|--------------|
| `customer_name` | `$json.name` |
| `customer_email` | `$json.email` |
| `customer_query` | `$json.notes` |
| `customer_address` | `$json.country` |

### Message Template
The Customer Messenger sends messages in this format:
```
Hello {customer_name}. Your Email Address is {customer_email}. 
You are from {customer_address}. Your query is {customer_query}. 
Thanks for contacting us.
```

## Usage

### Prerequisites
- n8n instance (self-hosted or cloud)
- n8n training nodes available (included by default in n8n)

### Importing the Workflow
1. Open your n8n instance
2. Navigate to **Workflows** → **Add Workflow**
3. Click the three-dot menu → **Import from File**
4. Select `worflow.json`
5. Save and activate the workflow

### Running the Workflow
1. Open the imported workflow in the n8n editor
2. Click **Execute workflow** (manual trigger)
3. The workflow will process up to 10 customer records from the training datastore

### Configuration Notes
- Workflow is currently **inactive** (`active: false`)
- Limited to 10 records (`limit: 10` in Customer Datastore node)
- Execution order: `v1` (default n8n execution mode)

## Development Notes

### Naming Conventions
- Workflow nodes use descriptive, human-readable names
- Custom fields use `snake_case` naming (e.g., `customer_name`, `customer_email`)

### Known Issues
- Filename typo: `worflow.json` should be `workflow.json`

### TODO
- [ ] Verify n8n version compatibility
- [ ] Consider increasing record limit for production use
- [ ] Add error handling nodes for failed operations

## Related Resources
- [n8n Documentation](https://docs.n8n.io/)
- [n8n Training Nodes Reference](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-base.customers/)
- [n8n Workflow Import/Export](https://docs.n8n.io/hosting/workflows/import-export/)
