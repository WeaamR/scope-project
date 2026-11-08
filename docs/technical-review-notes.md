# Technical Review Notes — SCOPE Workflow Exports

The three JSON files in `workflows/exports-review-only/` are sanitized
snapshots of the user-supplied n8n exports. They are included for
documentation/review only and are **not represented as verified
import-ready production workflows**. Credentials, webhook IDs, internal
instance identifiers and hard-coded publishable-key values were
redacted.

## Request Analysis Agent

The export contains Webhook → HTTP Request (Gemini) → JavaScript
parsing/validation → Respond to Webhook. A Supabase node named
`Save Request Analysis1` exists in the export but has no outgoing
connection and is not connected to the main execution path in that
snapshot. Confirm the live workflow wiring before treating this export
as a complete persistence path.

## Change Detection Agent

The export contains a main Webhook → Gemini HTTP Request → Parse Result
→ Respond path. Separate nodes for fetching the approved scope version,
fetching scope items, preparing analysis input, and saving the change
review appear in the export, but their connections do not form a
complete connected path into the Gemini request or save step. This
snapshot therefore does not demonstrate the complete live orchestration
reported during project testing. Re-export from the current live
workflow after confirming the intended connections.

## Scope Resolution

The export shows a connected sequence: Webhook → Validate Resolution
Input → Supabase RPC (`resolve_scope_item`) → Format Resolution Response
→ Respond to Webhook. The code checks required fields, UUID format,
allowed categories, explicit freelancer confirmation, and a Bearer
token. The UI journey still needs an end-to-end test.

## Security and Sharing

- Credential references and IDs have been replaced with placeholders.
- The Supabase publishable-key value in the supplied export has been
  redacted.
- The internal n8n instance ID and webhook IDs have been
  removed/replaced.
- Review these files before any public upload; do not add actual API
  keys, tokens, passwords, customer data, or unredacted credentials.

## Architecture Notes from the Supplied Pitch Deck

The supplied architecture slide describes these application-facing Edge
Function routes: - `analyze-request` - `detect-changes` -
`resolve-scope-item`

It also depicts the following persistence responsibilities: - Request
Analysis → `request_analyses` - Change Detection → `project_messages`
and `change_reviews` - Scope Resolution → `resolve_scope_item` RPC →
`scope_items` - Scope Approval → `approve_scope_version` RPC →
`scope_versions`

These are recorded as the architecture presented in the capstone deck.
The exact runtime wiring should be checked against the current deployed
Edge Functions, Supabase RPC definitions and live n8n workflows before
treating this list as a deployment-level trace.
