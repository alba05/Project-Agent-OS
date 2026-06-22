# Decision Log

## 2026-06-22

- Decision: Use a project-scoped agent model instead of generic chat behavior.
- Why: AI music work accumulates prompts, assets, and review logic that need durable local memory.
- Impact: Future threads must read local project context before acting.

- Decision: Treat one T8Star/Suno `task_id` as one generation record with separate `V1` and `V2` version records.
- Why: Suno returns version pairs, and collapsing them into one shared audio bucket causes archive ambiguity and delivery mistakes.
- Impact: Future archive logic must create a generation root plus per-version folders and metadata.

- Decision: Download audio from explicit mp3 media URLs instead of inferring extension from the default `audio_url`.
- Why: The default URL shape can produce wrong local file naming and broken playback assumptions.
- Impact: Future download logic must prefer `media_urls` entries with `content_type = mp3`.
