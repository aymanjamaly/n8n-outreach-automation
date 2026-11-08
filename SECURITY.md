# Security

This private repository is still a source of operational information. Limit access to maintainers who need it.

- Do not commit API keys, OAuth tokens, Airtable lead records, or n8n execution data.
- Store credentials in n8n credential management. Reconnect them after importing the workflow.
- If a secret is accidentally committed, rotate it at the provider and remove it from the repository history; deleting the latest line alone is insufficient.
- Keep the repository private unless the workflow and all associated data have been reviewed for public release.
