# SCOPE — Testing Evidence

## Testing Methods Reported

- Postman API testing.
- Manual testing through the web application UI.
- Integration testing across Supabase, n8n, and Gemini.

The user reported that the three principal integration paths reached
successful integration testing. Postman screenshots or exported Postman
collections were not supplied in this documentation bundle; attach them
when available.

## Functional Areas Reviewed

| Feature                                    | Reported status                                    | Notes                                                                                       |
|--------------------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------------------|
| Project management                         | Working                                            | Reviewed through application use and screenshots.                                           |
| Service management                         | Working                                            | Service details include deliverables, exclusions, revisions and pricing information.        |
| Request analysis                           | Working                                            | AI extracts facts, missing information, ambiguities, risks and suggested questions/message. |
| Clarification questions and client message | Working                                            | User can review/edit suggested results.                                                     |
| Scope draft and approval/versioning        | Working                                            | Scope version and approval history visible in screenshots.                                  |
| Change detection                           | Working; detailed classification evidence expected | Additional-work and clarification examples were exercised.                                  |
| Classification with evidence/reason        | Expected to work; not fully confirmed by user      | Keep as partially verified until test artifacts are attached.                               |
| Scope Resolution UI end-to-end             | Not yet tested                                     | Workflow export shows validation and RPC sequence; UI flow still requires end-to-end test.  |
| Project message/change history             | Working                                            | Project history screenshot supplied.                                                        |

## Access-Control Checks Reported

The user confirmed the following checks: a user can see their own
project data; one user cannot access another user’s records;
unauthenticated users cannot access protected data.

## RLS Policy Inventory

The supplied Supabase policy query output reports RLS enabled on:
`projects`, `services`, `request_analyses`, `change_reviews`,
`scope_versions`, `scope_items`, `project_messages`, and `profiles`. The
policies use ownership expressions based on `auth.uid()` and
`WITH CHECK`. The policy role field appeared as `{public}` in the query
output, so role targeting and grants should be reviewed separately
before making a broad security assurance.

See `../docs/supabase-rls-policy-inventory.csv`.

## Human Review and Responsible AI Example

During request-analysis prompt refinement, a client asked for a short
promotional video and suggested a Thursday delivery. The system needed
to distinguish what the client explicitly requested from services
available in the freelancer’s package, and it must not treat the
proposed Thursday date as an accepted deadline. Prompt rules were
refined so that only explicitly requested items are treated as client
requirements and unconfirmed deadlines remain unconfirmed pending
clarification.

The freelancer reviews and can edit AI results. AI does not approve
changes or create commitments on the freelancer’s behalf.

## Development Issues and Improvements

1.  A Gemini `503 UNAVAILABLE` response occurred during integration. The
    model configuration was changed to Gemini 3.5 Flash Lite and the
    tested workflow subsequently returned structured JSON.
2.  Change Detection orchestration/persistence required adjustment
    during development. The workflow and Supabase integration were
    revised and tested. The supplied JSON export snapshot still needs
    reconciliation with the live workflow because some nodes appear
    disconnected in the export.

## Evidence Files Included

- Application screenshots: `../assets/screenshots/application/`.
- n8n workflow screenshots: `../assets/screenshots/integrations/`.
- Supabase table inventory screenshot and RLS CSV:
  `../assets/screenshots/integrations/` and `../docs/`.
- Capstone presentation: `../docs/SCOPE_Capstone_Presentation.pdf`.

## Evidence Still to Add

- Postman screenshots for Request Analysis, Change Detection and Scope
  Resolution/RPC.
- Optional n8n execution screenshots showing successful runs.
- Optional Supabase policy detail screenshots.
- Automated test suite results were not confirmed and are not claimed.

## Demonstration Scenario and Evidence Qualification

The capstone presentation illustrates a change-comparison scenario in
which the approved scope is one vertical video at 1080×1920 with a
45-second duration, and the incoming request asks for a 60-second
version plus a horizontal version. The user confirmed that a similar
scenario was executed in the application; the exact slide wording should
be treated as the presentation scenario, not as a claim that every field
was entered verbatim in the recorded run.

The demonstrated logic identifies the duration increase and the
additional horizontal version as changes to review against the approved
scope. The freelancer reviews the evidence and suggested response before
deciding what to do.

## Automated Test and Production Build Reconciliation

Slide 5 of the supplied presentation mentions automated TypeScript tests
and a production build. However, no automated test source files,
test-run logs, CI report, or production-build output were supplied in
the evidence package for independent review. Therefore: - The
presentation claim is recorded as a stated testing activity. - Automated
test execution is **not independently verified in this documentation
package**. - Do not claim a passing automated test suite or a verified
production build until the corresponding logs or artifacts are added.

## Postman Evidence Status

Postman API testing was reported as performed, but screenshots or a
Postman collection were not included in the supplied package. Add
sanitized evidence for: 1. Request Analysis. 2. Change Detection. 3.
Scope Resolution / RPC.

Screenshots should show the endpoint/action, response status and
relevant response body, while hiding authorization headers, tokens, API
keys, personal data and customer content.
