---
name: alldone-team
description: Use when the user asks to work with alldone.team, connect its tools, or choose between Story Builder, Judy Job, and Property Screener.
---

# Work with alldone.team

This plugin connects the existing `https://alldone.team/mcp` server. It operates
Story Builder, Judy Job, and Property Screener as the connected account. The
Alldone productivity/task-management MCP is a separate service.

## Start with the relevant product

| User's task | Start here | Workflow skill |
| --- | --- | --- |
| Stories, pitches, narrated videos, scenes, captions | `story_capabilities`, then `story_list` or `story_get` | `story-builder` |
| Job matches, applications, CVs, application tracking | `judy_context`, then `judy_capabilities` | `judy-job` |
| Saved property calculations and what-if scenarios | `property_capabilities`, then `property_list` or `property_get` | `property-screener` |

Discover the actual connected tool names and current schemas. Do not invent
tools, identifiers, prices, or results. Use the product's current instructions
and existing saved records before creating or editing anything. Paginate lists
before claiming to have inspected every record.

## Connection

The plugin adds the MCP server `plugin:alldone-team:alldone-team`. In Claude Code
its tools carry the prefix `mcp__plugin_alldone-team_alldone-team__`, for example
`mcp__plugin_alldone-team_alldone-team__story_list`. If the tools are missing or
the server needs authentication, ask the user to run `/mcp`, select that server,
and choose Authenticate; other hosts use their own connection flow. The server
uses OAuth authorization code with PKCE S256 and dynamic client registration. The
user completes sign-in and consent on alldone.team in their browser. Never
request, extract, copy, or package credentials, cookies, tokens, or browser
storage.

If the alldone.team connector is also connected from claude.ai, the host may hide
the plugin's server as a duplicate (the tools then carry the connector's prefix,
such as `mcp__claude_ai_Alldone_team__story_list`) or list both sets of tools.
Both act as the same signed-in account; use one set consistently.

The package requests the server's supported product scopes. Consent gives API
access; perform paid actions, purchases, deletion, sharing, or other consequential
actions only within the user's authorization. Reuse authorization already given
for the exact action. Existing account permissions and credit costs still apply.
If a tool reports `insufficient_scope`, use the supported reconnection flow for
the missing permissions. Do not treat an authorization error as a successful
connection or route around it.

If the tools are unavailable, help the user connect as described above and do not
work around a missing connection. For steps that need the product page itself,
give the user its link:

| Product | Page |
| --- | --- |
| Story Builder | https://alldone.team/connor-consultant/story-builder |
| Judy Job | https://alldone.team/judy-job/job-radar |
| Property Screener | https://alldone.team/ricky-returns/check-investment-opportunity |

## Results

Keep changes in the product's saved record and return its canonical browser or
result URL. Verify writes by reading their result/current state. Poll the returned
job or operation instead of repeating its start call. Report failures and partial
results accurately. Never put personal job documents or property details in an
unrelated project or log.
