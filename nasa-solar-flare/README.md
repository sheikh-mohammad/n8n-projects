# NASA Solar Flare - n8n Workflow

## Project Overview

This directory contains an **n8n automation workflow** that monitors solar flare activity from NASA's DONKI (Space Weather Database) system. The workflow is designed to:

1. **Schedule Trigger**: Runs daily at 20:45 (Asia/Karachi timezone)
2. **Fetch Solar Flare Data**: Retrieves DONKI solar flare data from NASA API
3. **Filter by Class**: Checks if the solar flare catalog contains "M" class flares
4. **Send Notifications**: Sends requests/notifications when M-class solar flares are detected

## Directory Contents

| File | Description |
|------|-------------|
| `workflow.json` | n8n workflow definition (importable into n8n) |
| `workflow.png` | Visual diagram of the workflow |
| `README.md` | This documentation file |

## Workflow Architecture

```
Schedule Trigger (20:45) 
    → Get DONKI Solar Flare (NASA API) 
    → If (contains "M" class) 
    → Send Request (notification)
```

### Nodes

1. **Schedule Trigger** (`n8n-nodes-base.scheduleTrigger`)
   - Triggers at 20:45 daily
   - Timezone: Asia/Karachi

2. **Get a DONKI solar flare** (`n8n-nodes-base.nasa`)
   - Resource: `donkiSolarFlare`
   - Requires NASA API credentials

3. **If** (`n8n-nodes-base.if`)
   - Condition: Checks if `$json.catalog` contains "M"
   - M-class flares are medium-strength solar flares

4. **Send a request** / **Send a request1** (`n8n-nodes-base.postBin`)
   - Sends notification with flare class type

## Usage

### Importing into n8n

1. Open your n8n instance
2. Go to **Workflows** → **Import from File**
3. Select `workflow.json`
4. Configure the NASA API credentials (currently references `xxxxxxxxxxxxxxx`)
5. Activate the workflow

### Prerequisites

- n8n instance (self-hosted or cloud)
- NASA API key (get one at https://api.nasa.gov/)
- Credentials configured for the `nasaApi` connection

## Configuration

The workflow settings include:
- **Timezone**: Asia/Karachi
- **Execution Order**: v1
- **Save Executions**: All (success and error)
- **Caller Policy**: workflowsFromSameOwner

## Development Notes

- The workflow is marked as `active: true`
- Two parallel "Send a request" nodes exist (may need consolidation depending on use case)
- The `binContent` field uses template expressions to include flare class data
