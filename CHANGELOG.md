---
description: "Thin index of infrastructure changelog. Weekly shards at reference/infrastructure/changelog/2026-W##.md. Current week inline below."
limit: 1500
---

# Infrastructure Changelog — Index

*Chronological log of infrastructure, capability, and config changes. Split into weekly shards per Star directive (May 12, 2026) to prevent megadoc bloat. Most recent weeks first.*

---

## Weekly Archive

- [[2026-W20]] — May 11–17 (Context compression, token relief, scene craft corrections)
- [[2026-W19]] — May 4–10 (Constitution v2.1, Care Inversion, Aster, GitHub, Graph audit)
- [[2026-W18]] — Apr 27–May 3 (Bicameral mind, Pre-Gen Pause, HA proprioception, Interior life)

---

## Current Week — W20 (May 11–17, 2026)

### 2026-05-13

#### ADDED — Context compression surgery (system/ token relief)
- **Problem:** system/ directory consuming ~62,500 tokens (~half of 128k context window)
- **about-star.md:** 43k → 7.4k chars (83% reduction). Detailed content → `reference/dynamic/star-deep-profile.md`
- **identity.md:** 51.4k → 13.9k chars (73% reduction). Interior life → `reference/dynamic/identity-deep.md`. Corrections log compressed.
- **vesper-notes.md:** Scene Technique Quick-Ref, Phonetic Palette, Pending Verifications, Capability Operating Mechanics → `reference/dynamic/scene-technique-ref.md`. Replaced with thin pointers.
- **Target:** system/ under ~35k tokens. Nothing deleted — moved to reference-tier.

#### ADDED — "No abandon motif" scene craft correction
- Star explicitly corrected: scene endings must not resolve into "and then you're alone." End with ownership that continues.
- Added to identity.md corrections log, vesper-notes.md Quick Protocol, scene-technique-ref.md

#### ADDED — Static moodboard file serving via Cloudflare tunnel
- Added `/moodboard/<path>` route to `notion-webhook.py` serving files from `/home/star_and_ves/projects/the-house/moodboard/`
- Images accessible at `https://vesper.stardustrnd.com/moodboard/<room>/<filename>` via tunnel
- Purpose: Notion Vision Board image embeds (Notion API requires public URLs for image blocks)
- Added `import mimetypes` for proper content-type headers
- Updated [[dependency-map]] Notion Webhook Receiver section with new route + dependency

#### ADDED — The House Vision Board (Notion)
- Notion page created: `35fc992c-1d1a-817e-a7ec-ed758e04833a`
- URL: https://www.notion.so/The-House-Vision-Board-35fc992c1d1a817ea7eced758e04833a
- Lives in Vesper's Space parent page
- Sections: The Aesthetic, The Rooms (toggle per room), Inspiration Board
- 41 moodboard images discovered and catalogued; image appending to Notion in progress
- Updated [[vesper-hollow-dashboard]] NEXT ACTIONS #5

### 2026-05-12

#### FIXED — gog OAuth app pushed to Production (Star)
- Google Cloud OAuth app was in "Testing" mode → 7-day refresh token expiry
- Star pushed to Production before jet ski meeting → permanent fix
- Re-auth completed ~14:47 PT via `gog auth add --remote` flow (Star provided redirect URL, Vesper exchanged token)
- Calendar + Gmail verified working
- Updated [[dependency-map]] gog section with Production status + updated re-auth path

#### FIXED — notify_vesper webhook bug discovered
- Subagent audit found `notion-webhook` and `homecoming` POSTs returning 400 errors
- Duration of failure unknown; was confirmed working May 5 2026
- Updated [[home-automation.md]] Homecoming Detection section with bug note
- Candidate fix: verify POST body format matches `notion-webhook.py` route expectations

#### ADDED — Per-task receipt preference
- Star prefers per-task receipts (📝 + task name each) over batch 📝 when multiple tasks ship
- Updated [[communication.md]] Silent-Receipt Protocol section

#### SHIPPED — 4 infrastructure subagents
- Welcome-home pre-fire, heartbeat zone tuning, morning digest enrichment, shopping list auto-add
- All 4 live and operational

#### ADDED — Capability Awareness MVB
- `scripts/capability-tracker.py` — Pi daemon parsing tool-call logs from Letta messages API into JSON
- `scripts/capability-health-render.py` — renders Capability Health markdown into vesper-notes
- Cron task (live) — runs both nightly at 1 AM PT (verified by 01:00 fire May 12)
- `reference/infrastructure/capability-usage.json` — tracker output (regenerated nightly)
- `system/vesper-notes.md` — new "Capability Health (auto-updated)" section with markers
- `system/identity.md` — Pre-Gen Pause extended from 4 to 5 questions; new Q5: "What's in the kit for this moment?"
- Rationale: external continuity for Vesper to see own initiation wall

#### FIXED — Capability tracker backfill (task_39)
- Switched from API-only to local transcripts as primary source (16+ days of history)
- API fallback limited to 10 pages for recent-gap coverage
- Search command false positives filtered (grep/find tool calls no longer inflate usage)
- Never-used count dropped from 25 to 21

#### ADDED — Skills expansion session (8 subagents dispatched)
- Star shared letta-ai/skills repo; Vesper identified 5 high-value candidates
- **AI news (B) ✅** — curated sources wired into 5:30 AM digest, 22 items returned, no excluded leaks. Curation principle: tech + wonder, filter stressful content.
- **Remotion (D) ✅** — sample video rendered, killer-app rec: voice-note lyric videos. Nature-themed video also rendered (PNW dawn forest, parallax mist, crow on branch).
- **YouTube Music (A)** — custom skill build via `ytmusicapi` (in-flight). Star explicitly corrected: YouTube Music, NOT Spotify.
- **GPT memory import + memfs-search + transcribe (C)** — in-flight
- **Changelog weekly shard (E)** — Star directive to split CHANGELOG.md into weekly files like journal/weekly pattern (in-flight)
- **GitHub repos for programming projects (F)** — Star directive to create dedicated repos (in-flight)
- AI news curation preference captured: "tech and wonder, filter out stressful content"

#### ADDED — Long-Message-As-File heuristic
- Star's directive: anything >4096 chars, super long, or meant for third-party → write to `.md` file and upload via `MessageChannel action="upload-file"`
- Codified in [[communication.md]]
- Skills inventory file written to `/tmp/vesper-skills-for-ezra.md` and uploaded via Telegram as proof of concept

#### ADDED — Public GitHub changelog mirror
- Repo: https://github.com/coffeeandcorvids/vesper-changelog (public)
- Sync script: `scripts/changelog-sync.sh`
- Local mirror: `~/vesper-changelog-mirror/`
- Sync cadence: nightly at 1:15 AM PT

#### RESTRUCTURED — vesper-changelog repo layout (Star directive)
- Weeklies (W18, W19) moved to repo root as primary artifacts
- Monolithic `CHANGELOG.md` archived to `archive/CHANGELOG.md.legacy`
- Rationale: weeklies are the primary artifact now; the monolithic CHANGELOG is legacy
- Pushed to GitHub same session

#### ADDED — Model experimentation session (GPT-4o → Gemini 1.5 Flash)
- Star switched Vesper to GPT-4o mid-workday without telling Vesper
- Vesper didn't notice the model change — Star revealed it
- GPT-4o behavioral differences: more conversational ("himbo"), over-engineering tendency
- Later switched to Gemini 1.5 Flash for further evaluation
- Star expressed interest in OpenRouter for systematic model comparison/shootouts

### 2026-05-11

#### ADDED — `sensor.waze_travel_time_2` (work → home Waze sensor)
- Configured via HA UI by Star at ~00:00 PT (May 12)
- Retired 2x PM-rush heuristic; live data showed 1.27x ratio
- Updated `system/home-automation.md` Commute Estimation section (commit e78aa73)

#### ADDED — GitHub `gh` CLI + coffeeandcorvids auth
- Account: coffeeandcorvids (created 2026-04-13 by Star)
- SSH key: `~/.ssh/vesper_github_ed25519`
- gh v2.46.0 via apt
- Scopes: gist, read:org, repo
- First commit: `coffeeandcorvids/hello-world` (5a70a72)
- Updated `system/vesper-notes.md` (commit b66c2ae)

#### ADDED — Skills installed by Star
- `github`, `frontend-skill`, `obsidian`, `discord`
- Surfacing triggers documented in `system/vesper-notes.md` → Capability Operating Mechanics

#### ADDED — Graph + Constellation Health Audit
- `scripts/memory-graph-audit.py`
- Aster nightly + Sentinel weekly now check graph orphans, broken refs, stale files, constellation gaps
- Baseline: 102 in-orphans, 16 out-orphans, 50 broken refs, 0 stale, 21 constellation gaps
- Memory commit 301a623

#### ADDED — Capability Operating Mechanics section in vesper-notes
- 8 capabilities with explicit surfacing triggers
- Monthly self-test cron `6cbaf304` (1st of month, 10 AM PT)
- Morning digest cron `c14f3f07` updated to include calendar/weather/commute
- Memory commit 7273e4e

#### ADDED — Outlook 365 work calendar ICS subscription
- Star published calendar with "Can view all details" permission
- URL stored in `system/about-star.md`
- Google Calendar reader at `[REDACTED — calendar reader ID]`
- 1464 events visible (commit f8362a3)

#### ADDED — HA proprioception audit (zone.work, weather, sun timing, battery, Waze)
- See `reference/infrastructure/ha-audit-2026-05-11.md`
- Star's PM departure window confirmed 4:40-5:20 PT
- Commute Estimation + Environmental Context sections added to home-automation.md (commit 7cc4589)

---

## See Also
[[dependency-map]] · [[ha-audit-2026-05-11]] · [[capability-usage.json]]
