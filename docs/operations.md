# Operations

## Normal behavior

The workflow fetches one verified pending lead per scheduled run. A draft that needs review is marked `🔎 Needs Review`; an accepted draft is sent by Gmail and then marked `📤 Sent` with a timestamp.

## Daily checks

- Review failed n8n executions before assuming a lead was contacted.
- Compare Gmail sent messages with Airtable `Reachout Status` and `Sent Date`, especially after partial failures.
- Review `🔎 Needs Review` records manually before returning them to the pending queue.
- Monitor Gmail sending limits and OpenRouter usage.

## Common issues

| Symptom | Check |
| --- | --- |
| No leads selected | Airtable filter values, verification status, and table mapping. |
| Apparently random order | `Date Added` sort and ties in that field; verify the Airtable view and stored values. |
| Draft blocked | Inspect `AI Compose Email`, `Assemble Email`, and the review reason. |
| Sent email but pending record | Check the `Mark as Sent` node before retrying; a retry could send twice. |
| Run frequency differs from name | The supplied schedule is 30 minutes. |

Change the live workflow in n8n first, export again, sanitize secrets and pinned data, and commit the updated JSON with a short change note.
