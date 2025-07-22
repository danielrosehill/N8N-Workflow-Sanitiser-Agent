# N8N-Workflow-Sanitiser-Agent

A JSON sanitization tool for N8N workflow exports that automatically identifies and removes sensitive information while preserving workflow structure.

## Purpose

This agent processes JSON exports from N8N (or similar workflow automation tools) and sanitizes them by identifying and replacing sensitive information with safe placeholder values. This allows workflows to be shared publicly without exposing:

- API keys and tokens
- OAuth credentials
- Email addresses
- CDN-based URLs
- IP addresses
- Webhook URLs
- Usernames and passwords
- Phone numbers
- Internal system paths with identifying information

## Usage

The agent uses the system prompt defined in `system-prompt.md` to process N8N workflow JSON files. Simply provide your workflow JSON as input, and the agent will return a sanitized version.

## Output Format

The agent returns a structured JSON response:

```json
{
  "sanitized_json": { /* Complete sanitized workflow */ },
  "notes": "### Changes Made\n\n- List of all replacements made..."
}
```

## Files

- `system-prompt.md` - The main system prompt that defines the sanitization behavior
- `schema-example.json` - Example output format
- `README.md` - This file

## How It Works

1. The agent recursively inspects all JSON values
2. Identifies potentially sensitive information
3. Replaces sensitive values with realistic fake data or clear placeholders
4. Returns the complete sanitized workflow with detailed change notes

The sanitized output maintains the original structure and functionality while being safe to share publicly.
