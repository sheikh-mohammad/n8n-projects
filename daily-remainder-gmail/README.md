# Project Overview

This is an **n8n workflow automation project** designed to send daily Gmail reminders. The project contains a single workflow that automates sending an email at a scheduled time each day.

## Project Structure

```
daily-remainder-gmail/
├── workflow.json    # n8n workflow definition
└── README.md          # This file
```

## Workflow Details

**Name:** Daily Remainder Gmail

**Functionality:**
- **Trigger:** Schedule-based trigger that fires daily at 8:10 AM
- **Timezone:** Asia/Karachi
- **Action:** Sends a Gmail message

**Nodes:**
1. **Schedule Trigger** - Triggers the workflow daily at 08:10
2. **Send a message** - Sends an email via Gmail OAuth2

**Workflow Configuration:**
| Setting | Value |
|---------|-------|
| Subject | N8N Daily Remainder |
| Recipient | haji08307@gmail.com |
| Message Type | Plain text |
| Status | Inactive (`active: false`) |

## Technologies

- **n8n** - Workflow automation platform
- **Gmail API** - Email sending via OAuth2 authentication
- **Node Type:** `n8n-nodes-base` (Schedule Trigger v1.2, Gmail v2.1)

## Usage

### Importing the Workflow

1. Open your n8n instance
2. Go to **Workflows** → **Import from File**
3. Select `workflow.json`
4. The workflow will be imported with all nodes and connections

### Activating the Workflow

1. Open the imported workflow in n8n
2. Toggle the **Active** switch to enable automatic execution
3. Ensure Gmail OAuth2 credentials are properly configured

### Credentials Required

- **Gmail OAuth2** - Named "Gmail account" (ID: `pLrWUaSoZslEA0CE`)
  - Must be set up with appropriate Gmail API permissions

## Tags

- `chat-gpt` - Workflow is tagged for categorization

## Notes

- The workflow is currently **inactive** and needs to be activated in n8n
- The email content is plain text: "This is n8n dialy remainder using daily sheduele"
- Execution order is set to `v1` (standard sequential execution)
- Caller policy is restricted to `workflowsFromSameOwner`
