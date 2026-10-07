---
name: reel-video-creator-sms
description: "Create short-form video scripts and production packages for Instagram Reels, TikTok, and YouTube Shorts, or produce the video when generation and editing tools are available. Use for reel scripts, storyboards, voiceovers, shot lists, video prompts, or turning an approved script into a finished short video. For captions alone, use caption-writer-sms."
metadata:
  version: "1.0.0"
---

# Reel Video Creator

Turn an idea or approved script into a filmable short-form video. When suitable tools are available, generate assets, assemble the video, and verify the exported artifact. Otherwise deliver an actionable production package and identify the remaining work accurately.

## Inputs and context

Read `.agents/social-media-context-sms.md` if present. Reuse the user's topic, audience, language, tone, and approved wording from the conversation; do not require profile setup before a one-off video.

Ask only for missing information that changes the result, especially the topic and audience. If length and style are unspecified, state a working default of a 30-second, vertical, voiceover-led video. Respect requests for talking-head, faceless, documentary, or other formats.

Determine the requested deliverable:
- **Script:** spoken lines, timing, on-screen text, and shot directions.
- **Production package:** script plus storyboard, voiceover direction, per-shot asset prompts, and editing notes.
- **Finished video:** the package plus execution through available tools and an exported video file.

An existing approved script is the source of truth. Expand its visuals without silently rewriting its message. Adjust wording only when needed for duration, accuracy, or a requested revision, and explain substantive changes.

## Workflow

### 1. Build a grounded story

Choose one audience-relevant tension and one payoff. Put a specific hook in the opening shot, deliver what it promises, and end with one relevant action or a natural closing thought. Use **hook-writer-sms** when hook variants are useful, rather than requiring a separate hook exercise for every video.

Do not promise virality or invent statistics, testimonials, personal experiences, or quotes. For factual, historical, or spiritual subjects, verify material claims and quotations using reliable sources when available. Distinguish documented teachings from original interpretation. Keep source notes outside the spoken script unless attribution belongs in the story.

For religious subjects, respect the user's tradition and framing. Label generated illustrative scenes as recreations; do not present synthetic footage of a historical figure as archival evidence or invent their speech.

### 2. Make timing executable

Produce a scene table:

| Time | Voiceover / dialogue | Visual / action | On-screen text | Audio / transition |
|---|---|---|---|---|

Use contiguous time ranges that cover the requested duration. Allocate time for pauses, reading, and actions. Estimate voiceover at roughly 130–160 words per minute as a planning heuristic; actual recorded or generated audio determines final timing. A calm 30-second script usually needs fewer words than an energetic one.

Keep overlays readable and separate from full subtitles. Choose transitions that support the story instead of adding an effect at every cut. Keep text away from likely platform controls; check the current target-platform overlay or preview when available rather than claiming one universal safe zone.

### 3. Expand into a production package

For each scene, provide:
- An asset ID and source: user footage, licensed stock, verified archival material, newly generated illustration, or footage to film.
- A filming direction or generation prompt specifying subject, action, framing, lighting, mood, aspect ratio, and duration for video generation.
- Continuity cues for recurring subjects, location, wardrobe, and palette.
- Audio direction: exact spoken wording, pronunciation notes where needed, delivery, pauses, and music mood.

Use one visual style across prompts. Prefer adding accurate text in the editor rather than asking an image/video generator to render long quotations. If only images can be generated, describe them as still assets and specify pan/zoom or cuts for assembly; images alone are not a finished video.

Include a cover-text suggestion and a supporting caption, using **caption-writer-sms** when appropriate. Use supplied or licensed audio/assets, or specify what the creator needs to source. Do not imply that selecting a music mood supplies a licensed track.

### 4. Execute when requested and supported

Inspect the actual available tools and their documented capabilities before choosing a pipeline. Read [tools/REGISTRY.md](../../tools/REGISTRY.md) for the distinction between production and publishing integrations. Do not invent tool names, assume provider access, or treat publishing tools as video generators.

If suitable generation, speech, and editing tools are available, use the subset needed for the requested format. Reuse supplied assets and actual tool schemas. Check any usage cost or external upload requirements against the user's authorization before proceeding where necessary.

Generate or record voiceover, create/source shots, assemble the timeline, add corrected subtitles and overlays, and export using the user's settings. A reasonable working export default is a 1080 × 1920, 9:16 MP4 with H.264 video and AAC audio when supported. Verify current platform requirements before promising upload compatibility.

If tools are unavailable or a step fails, deliver the completed package or partial assets, name the unavailable step, and provide concrete editor handoff instructions. Stop after a bounded retry for transient failures; do not repeatedly submit paid generation requests without checking whether the previous job succeeded.

Creating a video does not authorize publishing it. Use a supported publishing integration only when the user requests publishing or scheduling.

### 5. Verify the result

Before handing off a package, check that the hook's promise is fulfilled, narration fits the timeline, each scene has an asset source, and factual claims have appropriate support.

For a finished video, inspect the export's duration, dimensions, and audio presence. Watch the full video with sound when playback is available; otherwise inspect frames at every scene change and check audio separately, and disclose the playback limitation. Check caption synchronization, spelling, clipping, visual continuity, and the final frame. Correct material defects before delivery.

## Outputs

For a script or package, return the scene table and requested supporting material, stating assumptions briefly. For a finished video, link the actual exported file and summarize verification. List missing assets or uncompleted steps specifically. Never describe a storyboard, prompt set, silent clip, or failed export as a completed narrated video.

## Example

**Request:** “Expand my approved 30-second English Reel about Neem Karoli Baba for ages 18–24 into a faceless production package.”

Keep the approved narration. Verify attributed teachings, separate modern commentary from quotations, and plan a coherent sequence of a young adult putting down their phone, listening to a friend, helping someone, and a quiet devotional moment. Specify whether Baba's portrait is supplied/licensed or still needs sourcing. Provide timed shots, consistent visual prompts, calm voiceover direction, subtitles, and editor instructions. If no video tools are connected, deliver this as a production package and explain that rendering remains to be done.

## Boundaries and related skills

- Does not guarantee views, virality, or engagement.
- Long-form films and live streaming are outside this short-form workflow.
- **hook-writer-sms** — opening lines and hook variants.
- **caption-writer-sms** — supporting platform captions.
- **content-repurposer-sms** — adapt existing source content before production.
- **social-media-context-sms** — persistent voice and audience preferences.
