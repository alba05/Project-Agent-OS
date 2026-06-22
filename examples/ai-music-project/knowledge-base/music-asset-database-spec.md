# Music Asset Database Spec

## Purpose

Keep AI music generations queryable, auditable, and hard to misfile.

This is the minimum database or index spec for repeated T8Star/Suno generation work.

## Granularity

Use two levels of records:

1. Generation record
   One submit action, one `task_id`, one root folder
2. Version record
   One result variant such as `V1` or `V2`

Do not collapse both levels into one row without preserving the version split.

## Generation-Level Fields

Required fields:

1. `generation_id`
   Local stable ID, usually the root folder name
2. `task_id`
3. `provider`
   Example: `t8star-suno`
4. `base_url`
5. `submit_endpoint`
6. `poll_endpoint`
7. `created_at`
8. `prompt_title`
9. `prompt_text_path`
10. `lyrics_required`
11. `duration_target`
12. `submit_cost`
13. `poll_window_seconds`
14. `retry_of_task_id`
15. `retry_reason`
16. `tags`
17. `root_path`
18. `status`
   Example: `complete`, `partial`, `failed`
19. `notes`

## Version-Level Fields

Required fields:

1. `generation_id`
2. `version_name`
   `V1`, `V2`, or later extension if the provider changes
3. `clip_id`
4. `audio_url`
5. `image_url`
6. `local_audio_path`
7. `local_cover_path`
8. `local_clip_metadata_path`
9. `audio_format`
10. `has_cover`
11. `has_lyrics`
12. `lyrics_text_status`
13. `duration_seconds`
14. `display_audio_filename`
15. `all_expected_assets_downloaded`
16. `review_status`
   Example: `unreviewed`, `keep`, `revise`, `reject`
17. `delivery_status`
   Example: `internal-only`, `approved`, `packaged`

## Folder-to-Database Mapping

One generation root maps to one generation record.

Example:

1. `20260622_030743_split`
   generation record
2. `20260622_030743_split/V1`
   version record `V1`
3. `20260622_030743_split/V2`
   version record `V2`

## Invariants

These rules should always hold:

1. One `task_id` can own multiple version records
2. Each version record must point to exactly one version folder
3. `V1` and `V2` must never share the same local audio file path
4. A playable local `.mp3` path is required before a version can be marked complete
5. Missing artifacts must be recorded as missing, not silently omitted
6. Unless the generation is explicitly instrumental, `has_lyrics` must be true before a version can be approved
7. If lyric text is unreadable, set `lyrics_text_status` to `unrecoverable-text` or another explicit failure marker instead of guessing
8. Preferred review target is 2 to 6 minutes of audio duration
9. If no separately approved song title exists, `display_audio_filename` should use the theme naming pattern such as `theme-v1.mp3` and `theme-v2.mp3`
10. A repeated submit for the same theme should be traceable through `retry_of_task_id` and `retry_reason`
11. A generation is not fully archived until `all_expected_assets_downloaded` is true for both `V1` and `V2`

## Recommended Storage Format

For a lightweight local project, either of these is acceptable:

1. one JSON index file per generation plus a rollup manifest
2. one CSV or spreadsheet with one row per version
3. one SQLite table for generations and one SQLite table for versions

If choosing a spreadsheet or CSV, use one row per version, not one row per generation.

## Minimum Review Query Examples

The index should make it easy to answer:

1. Which generations used the same tags?
2. Which `V1` or `V2` outputs were kept?
3. Which versions are missing local audio?
4. Which generations used the wrong folder structure?
5. Which outputs were produced from one `task_id`?
6. Which approved outputs are missing lyrics?
7. Which generations failed because of text corruption or encoding damage?
8. Which outputs fall outside the preferred 2 to 6 minute range?
9. Which tasks were retried and what did the retry cost?
10. Which tasks were successful upstream but still missing local assets?

## Anti-Drift Rules

1. Update the database immediately after download, not later in memory
2. Do not rename version folders without updating the index
3. Do not overwrite old runs to "clean things up"
4. If a prior run is wrong, mark it as superseded and create a corrected run
5. Validate lyric readability in the request payload before submit, because corrupted text can cause a nominal lyric task to behave like an instrumental generation
6. Store the real polling window, because short polling can create accidental duplicate submit cost
7. Do not mark a task complete until local asset download has been audited, not just because the provider page shows success
