---
name: property-screener
description: Use when the user wants to inspect, edit, compare, export, or share property investment calculations in alldone.team Property Screener with Ricky Returns.
---

# Property Screener

Start with `property_capabilities`, then `property_list` or `property_get` for
the canonical saved `analysisId`. Use the provided ID; never substitute a user ID
or guess an ID from the property's name. Resolve ambiguity before editing.

## Analyze and compare

Read the actual saved inputs, country, units, scenario settings, notes, and
decisions. `property_analyze` and `property_compare` calculate what-if scenarios
without overwriting the saved inputs. `property_export` returns the report.

Distinguish observed facts from country defaults and starter assumptions.
Automatic rent is calculated break-even rent before tax, not market rent.
Own-use saved rent means comparable warm rent. Leave unknown values and undefined
returns unknown. Explain the decisive assumptions, currency/area units, cash
flow, debt, investment horizon, and nominal versus present-value basis.
Verify current market, tax, and financing claims with authoritative sources.

## Edit saved inputs

- Read the latest analysis before each change. Use its `expectedRevision` and a
  UUID `requestId`. Reuse identical arguments and ID only for an uncertain retry.
  On conflict, reread, preserve newer edits, and reassess the intended change.
- Batch related changes atomically and respect decision locks. Replace a locked
  decision only with the user's authorization to unlock/change it. Notes should
  explain evidence and rationale; locking is not proof of research.
- `property_guide` is a paid Ricky proposal. It does not apply changes. Review the
  proposal and use `property_update` for accepted changes; do not charge again
  by regenerating an uncertain request with another ID.
- A successful write with a browser-sync error already changed saved state.
  Reopen/recover the view instead of repeating the mutation.

## Sharing and delivery

Return the canonical `browserUrl`, report, and scenario findings. Share or change
access only when authorized. A shared calculation link allows a verified signed-in
user to explicitly join as an editor; normal reads never join. Check invitation
email delivery separately from collaborator access. Ricky conversations remain
private per account. Duplication creates a private copy.

Pro purchases, deletion, and starting paid voice/video require the corresponding
user authorization. Microphone/video are interactive browser operations; a remote
MCP result containing a browser link does not mean a call has started.

For anything that needs the page itself, give the user the analysis's canonical
`browserUrl`.
