# T8Star Suno Generation Archive SOP

## Purpose

Generate AI music through T8Star/Suno and archive the outputs without version confusion, broken downloads, or missing metadata.

## Default Assumptions

1. T8Star base URL is `https://ai.t8star.org`
2. Submit endpoint is `/suno/submit/music`
3. Poll endpoint is `/suno/feed/{task_id}`
4. One generation task normally returns two result variants
5. Those two variants must be treated as separate asset versions, not as two files inside one shared audio folder
6. Unless the user explicitly asks for instrumental music, AI music must be generated as a vocal song with usable lyrics
7. Preferred target duration is between 2 and 6 minutes
8. Each Suno music generation call has real per-run cost, so duplicate submits must be treated as a cost bug

## Required Output Structure

Each generation must create one root folder for the task.

Example:

```text
t8star-music-sample/
  20260622_030743_split/
    README.md
    generation-metadata/
    V1/
      01-audio/
      02-lyrics-text/
      03-cover-visuals/
      04-task-metadata/
      05-other-files/
    V2/
      01-audio/
      02-lyrics-text/
      03-cover-visuals/
      04-task-metadata/
      05-other-files/
```

Rule:

1. Root folder represents one generation task
2. `V1/` and `V2/` each represent one Suno result variant
3. Do not put both music files into one shared `01-audio/` folder at the root

## Generation Procedure

1. Create a new timestamped root folder before generation
2. Prepare title and lyric text in UTF-8 before request serialization
3. Confirm lyric text is readable Chinese text, not `????`, before submit
4. Save the request payload first
5. Submit generation through `/suno/submit/music`
6. Save the raw submit response and extract `task_id`
7. Poll `/suno/feed/{task_id}` until both variants expose usable media URLs
8. Create `V1/` from the first returned clip and `V2/` from the second returned clip
9. Save each clip's raw JSON independently inside that version folder

## Cost Control Rule

Default rule:

1. Treat every music submit as billable work
2. Do not submit the same theme again just because the first poll window was too short
3. If a task has already been submitted and has a valid `task_id`, continue polling that task first
4. A second submit for the same theme on the same day must be justified in metadata as `retry-after-failed-archive`, `retry-after-bad-audio`, `retry-after-instrumental-output`, or a similarly explicit reason
5. If a duplicate submit happens by mistake, record it as a cost mistake rather than silently hiding it

## Polling Rule

Default rule:

1. Prefer longer polling over repeat submission
2. Minimum default polling window should be at least 10 minutes for a normal music task unless the provider clearly reports terminal failure earlier
3. Recommended baseline is 15-second intervals with enough total attempts to cover that window
4. Do not classify a task as failed only because the first 1 to 3 minutes did not produce archive-grade mp3 files
5. Before any retry submit, verify that the existing `task_id` is recorded
6. Before any retry submit, save the latest feed snapshot locally
7. Before any retry submit, check local download attempts for existing clips
8. Before any retry submit, write the retry reason into metadata

## Lyrics Workflow Preference

Preferred rule:

1. If a usable Suno lyrics-generation endpoint is available, prefer a two-step workflow for lyric songs:
   `lyrics generation -> lyric review -> music generation`
2. The local model inventory has shown `suno_lyrics`, so this should remain on the shortlist for future testing
3. Even when using a lyrics endpoint, the reviewed local lyric file remains the canonical text source for archiving
4. Do not block music generation on this endpoint until it has been verified in real local use

## Lyric Requirement

Default rule:

1. AI music must include lyrics unless the user explicitly asks for instrumental output
2. `make_instrumental: false` is required but not sufficient
3. The submitted lyric field must contain intact human-readable text
4. If the request payload, local lyric file, or task summary already shows `????` or other corruption, stop and fix encoding before generation

## Duration Preference

Preferred rule:

1. Aim for 2 to 6 minutes when the provider supports duration control or when prompt phrasing can influence structure
2. If exact duration cannot be forced, still record the duration target in metadata and review the result against that target
3. If the generated audio is clearly outside the 2 to 6 minute range, mark it in review notes

## Audio Download Rule

Never trust the bare `audio_url` filename shape for local extension naming.

Required checks:

1. Prefer `media_urls` entries where `content_type = mp3`
2. Prefer the URL containing `format=mp3`
3. Save local audio explicitly as `.mp3`
4. Verify the response `Content-Type` is audio-like before treating it as a finished music file

Anti-patterns:

1. Inferring extension from a URL that has no filename suffix
2. Saving audio as `.ai`
3. Saving HTML or redirect payload as fake `.wav` or `.mp3`

## Per-Version Required Files

Each of `V1/` and `V2/` should include:

1. `01-audio/`
   One playable `.mp3`
2. `02-lyrics-text/`
   Prompt or lyric text used for that output
3. `03-cover-visuals/`
   Cover image if available
4. `04-task-metadata/`
   Raw clip JSON and task summary
5. `05-other-files/`
   URL trace file with local file paths

## Root-Level Required Files

The generation root should include:

1. `README.md`
   Explains that this root is one generation task with separate `V1` and `V2`
2. `generation-metadata/request_payload.json`
3. `generation-metadata/submission_response.json`
4. `generation-metadata/poll_history.json`
5. `generation-metadata/feed_result.json`
6. `generation-metadata/collection_manifest.json`
7. `generation-metadata/download_audit.json`
   Records whether every expected asset was actually downloaded to local disk

## Naming Rule

Use stable technical names for local files, but allow theme-based delivery names when the title source is stable.

Recommended audio file names:

1. If no separate song title is intentionally provided, use the music theme as the delivery filename
2. Example: `theme-v1.mp3`
3. Example: `theme-v2.mp3`
4. Keep technical identifiers such as `clip_id` in metadata even when the audio filename uses the theme

Do not depend on provider-returned generated titles as the primary identifier because titles may be empty, duplicated, or encoding-damaged.

## Database Writeback Rule

After each generation, update the music asset database or index immediately.

Minimum writeback:

1. `task_id`
2. generation root path
3. `V1` clip id and local paths
4. `V2` clip id and local paths
5. prompt title
6. tags
7. generation date
8. tool/provider
9. status
10. retry reason if applicable

## Failure Handling

If one artifact fails:

1. keep the successful files
2. record the failure in metadata
3. do not fake completion
4. mark the missing artifact clearly
5. keep polling if the provider task is still live and the failure is only incomplete asset readiness

Examples:

1. `wav unavailable`
2. `cover missing`
3. `download returned non-audio payload`

## Stable Lessons From This Session

1. `.org` is the correct T8Star base URL for this workflow
2. `/suno/submit/music` and `/suno/feed/{task_id}` worked in real use
3. Suno returns version pairs that must be archived as `V1` and `V2`
4. Audio should be downloaded from explicit mp3 media URLs, not guessed from the default URL shape
5. A lyric-generation request can still turn into effectively instrumental output if the submitted lyric text is already corrupted before the request reaches the provider
6. Encoding integrity must be checked before submit, not only after files are archived
7. On 2026-06-22, repeated submits for similar themes exposed a real cost issue, so longer polling must be preferred over duplicate generation
8. Asset collection is not finished when the task shows success in the provider UI; local download and archive verification are mandatory
