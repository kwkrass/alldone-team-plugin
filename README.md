# alldone.team for Claude

Work with your [alldone.team](https://alldone.team) account from Claude. The
plugin connects Claude to the alldone.team MCP server and adds four skills that
explain how to use its three apps well:

- **Story Builder**: plan a story or pitch with you, then build it scene by
  scene with slides, animations, narration and captions, export the video and
  share an unlisted Watch link.
- **Judy Job**: review job matches, keep your application tracker current,
  prepare tailored applications and CVs, and create unsent Gmail drafts. Sending
  stays with you.
- **Property Screener**: inspect saved property investment calculations, compare
  what-if scenarios without overwriting them, and export reports.

The plugin contains no code. It holds a connection to
`https://alldone.team/mcp` and the instructions in `skills/`. Everything runs on
alldone.team under your own account, permissions and credits.

## Requirements

- An alldone.team account. You sign in during setup; the plugin stores no
  passwords or tokens.
- Generation, export and some other actions spend alldone.team credits, as they
  do on the website. The skills tell Claude to take paid, destructive or sharing
  actions only with your authorization.

## Install

Once the plugin is listed, add **alldone.team** from the plugin directory in
Claude. In Claude Code you can also install it from this repository:

```bash
claude plugin marketplace add kwkrass/alldone-team-plugin
claude plugin install alldone-team@alldone
```

## Connect

The first time Claude uses the plugin, connect your account: the host opens
alldone.team, you sign in and approve access. In Claude Code, run `/mcp`, select
the alldone-team server and choose **Authenticate**. Access uses OAuth with
PKCE, and you can disconnect it in Claude at any time.

## Example prompts

- "Help me create a two-minute narrated video that explains our new onboarding
  flow."
- "Show me my open job applications in Judy Job and which ones need a follow-up
  this week."
- "Prepare an application for the newest matching job, using my current CV, and
  put it in a Gmail draft for me to review."
- "Compare my saved apartment analysis at the asking price and at 10% less, and
  explain the cash flow difference."

## Skills

| Skill | Use it for |
| --- | --- |
| `alldone-team` | Choosing the right app, connecting, and general rules |
| `story-builder` | Stories, pitches and narrated videos |
| `judy-job` | Job matches, applications, CVs and tracking |
| `property-screener` | Property calculations, scenarios and reports |

## Troubleshooting

- **No alldone.team tools available:** connect the account as described above,
  then start a new conversation.
- **"insufficient_scope" or sign-in errors:** reconnect the server and approve
  all requested permissions.
- **Not enough credits:** top up credits on alldone.team, then retry the action.
- **A long job seems stuck:** ask Claude to check the job's status instead of
  starting it again; generation and exports run as background jobs.

## Privacy, terms and support

Claude sends your requests to the alldone.team MCP server, which processes them
under the alldone.team [privacy policy](https://alldone.app/privacy/) and
[terms](https://alldone.app/terms/). Contact and support:
[alldone.app/impressum](https://alldone.app/impressum/).

## License

The plugin files are licensed under the [Apache License 2.0](LICENSE). The
alldone.team name and logo are not licensed under it (see section 6 of the
license).
