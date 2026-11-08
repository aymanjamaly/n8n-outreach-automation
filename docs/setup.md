# Setup

## Requirements

- n8n instance with the Airtable, Gmail, and OpenRouter nodes available.
- Airtable base with the Apollo leads table and the fields `Business Name`, `Email Status`, `Reachout Status`, `Date Added`, and `Sent Date`.
- Airtable access token, Gmail OAuth connection for the intended sender, and OpenRouter API credential.

## Import

1. In n8n, create a workflow and import [`../workflow.json`](../workflow.json).
2. Reconnect the credentials in **Get Pending Leads**, **Mark as Sent**, **Mark Needs Review**, **Send Email**, and **OpenRouter Chat Model**.
3. Check the Airtable base/table selectors. The supplied export points to base `appWzgzC0MmOvHTg8`, table `tblnlqNdqg0tfwdhF`.
4. Check **Send Email**: sender account, reply-to address, subject, and body mappings.
5. Check the **Every 15 Minutes** node. Its configured interval in this snapshot is **30 minutes** despite the name.
6. Keep the workflow inactive until the checks below pass.

## Safe first test

Use a controlled Airtable lead whose email address you own. Verify the pending/verified filter, one-record limit, generated copy, review branch, successful Gmail send, and Airtable status/date update. Confirm that a `Needs Review` draft does not reach Gmail.

The exported `active` field reflects the source workflow. Importing and activating a second copy alongside the original can cause duplicate sends.
