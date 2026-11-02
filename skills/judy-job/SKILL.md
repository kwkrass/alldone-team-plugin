---
name: judy-job
description: Use when the user wants to review job matches, manage application tracking, prepare CVs and applications, or create unsent Gmail drafts in alldone.team Judy Job.
---

# Judy Job

Start with `judy_context` and `judy_capabilities`. Read the current guide, profile,
job, application, source CV, and relevant settings before writing. Use Judy as
the system of record for job-search records and documents. Check existing jobs
before adding one; preserve IDs, statuses, notes, and history.

## Review and track

- Use the current list/get tools and pagination. Distinguish job ads from practice
  leads without an advertised vacancy; verify time-sensitive vacancies with their
  original sources before presenting them as open.
- Applications and new matches have different scopes. Use the server's counts
  and explicit filters; do not equate the first page with the full result set.
- Use `judy_crm_overview`, job details, and timeline tools for next steps, actual
  contacts, appointments, deadlines, and unanswered applications. A stale record
  suggests a follow-up; it is not an automatic rejection.
- Record real past contacts as activities and future appointments/deadlines as
  tasks. Respect the returned timezone and preserve date-only dates. Do not
  invent a meeting time or log a planned interview as completed.

## Prepare an application

1. Read the job and current application revision. Use the source CV as the facts
   source, and ask for material missing facts instead of inventing credentials,
   experience, or claims.
2. Prepare/edit the application through the discovered tools. Read it back with
   `judy_application_get`, inspect warnings, and verify the cover-letter PDF,
   tailored CV, and intended extra attachments before drafting mail.
3. Create an unsent Gmail draft only within the user's authorization. Sending
   remains a user step; there is no `judy_send` tool. Google sign-in and consent
   are completed by the user in the browser.
4. Update an existing draft through the draft-update tool. Do not call draft
   creation again to apply edits. If a draft outcome is uncertain, read current
   state and follow its recovery instructions using the same request ID.

Use the exact revision/timestamp fields required by each schema. On conflict,
reread and preserve newer user edits. Long calls return an operation; poll
`judy_operation_get` at `pollAfterMs`, and use `judy_scan_get` for scanner progress.
Do not rerun generation or Gmail mutations to check whether they finished.

## Show results

Call `judy_show` when the user wants to see/work in Judy's interactive workspace,
using its discovered schema. Hosts without MCP Apps receive useful data instead;
there, offer https://alldone.team/judy-job/job-radar for the interactive workspace.
Use list/get tools for your own analysis. Keep app-only tools for the view.
Return application/job links and the actual document attachments supplied by
tools. Treat only confirmed outcomes as applied or sent.

Local document import, microphone practice, and Google connection steps require
the product page at https://alldone.team/judy-job/job-radar; send the user there
for them.
