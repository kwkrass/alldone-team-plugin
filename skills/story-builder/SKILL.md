---
name: story-builder
description: Use when the user wants to create, edit, narrate, animate, caption, export, or deliver a story, pitch, or video in alldone.team Story Builder.
---

# Story Builder

Use connected alldone.team tools first. Call `story_capabilities` for current
schemas, defaults, costs, and workflow instructions. For an existing story, find
it with `story_list` or use its supplied canonical ID, then call `story_get`.
Read the latest revision before changes. Use stable scene IDs and a new UUID
`requestId` for each intended mutation; reuse it only for an identical retry.

## New story

1. Propose the goal, main message, title, and ordered scene outline in chat.
   Review and revise it with the user. Saving a draft storyline is allowed.
2. Wait for explicit approval of that storyline before generating visuals,
   narration, animations, exports, or Watch links. A general video request does
   not approve an outline the user has not reviewed. Reuse prior approval of a
   supplied or reviewed storyline without asking again.
3. After approval, continue through the requested deliverable. Use the current
   recommended defaults from the server unless the user specifies otherwise.
   By default, include a visible title scene first and later set its stable
   scene ID as `coverSceneId` before export.
4. Finalize each scene script, generate its voiceover, and wait for success
   before generating its visual. Use measured narration and word timings for
   reveals and beats. Skip this order for silent scenes, supplied visuals, or
   an explicit visuals-first request. Keep one job per scene running at a time.

`story_create` can save supplied scenes unchanged or generate a storyline from a
brief. Discover writing skills and templates with the current capabilities.
For private browser stories, follow `story_enable_mcp` guidance before remote
editing; do not create a duplicate just because the first list is paginated.

## Edit and finish

- Read the scene source before editing. For small narration changes, regenerate
  voiceover; existing visual playback automatically follows current narration.
  Different visual and voiceover durations are expected. Do not change trims,
  speed, or duration solely to make their numbers match.
- Captions show the script. Use `story_get_captions` and `story_edit_captions`
  for grouping, timing, position, and emphasis; edit the script to change words.
- Upload/import media through the supported tools and use their returned asset
  URLs. Website styling import alone does not import image bytes.
- Generation, rendering, and export return durable jobs. Poll `job_get` with the
  returned interval. A timeout is not permission to start another paid job.
  If `applied=false`, review the result before applying it to newer story state.
- Resolve actual export blockers, export the saved current content, and verify
  the export succeeded. An old MP4 can predate recent edits.
- Deliver the unlisted Watch link as the primary completed-video result and the
  editable `browserUrl` separately. After export, poll `watchLinkJobId`; if
  unavailable or failed, follow current `story_publication` guidance. Verify the
  saved publication result before reporting the link ready.

Creating/updating the unlisted Watch link for a requested completed video is
already authorized by that request after storyline approval. Anyone with that
link can watch without signing in. Respect explicit playback restrictions.
Deletion, collaborator changes, revoking links, and sending/posting to others
require the corresponding user authorization.

Do not claim a script or saved draft is a finished video.
