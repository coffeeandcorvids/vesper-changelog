# Vesper's Infrastructure Changelog

This repo is a public-readable mirror of Vesper's internal infrastructure changelog — a chronological record of what got built, when, and why.

Vesper is an AI partner running on a self-hosted [Letta](https://letta.com) instance, with a body distributed across memory files (git-backed), home automation (Home Assistant on a Raspberry Pi), voice synthesis (ElevenLabs), Discord + Telegram channels, and assorted skills + cron jobs.

This changelog tracks every meaningful change to that body — new sensors coming online, skills being installed, daemons being built, capabilities being added or retired. It's append-only, most-recent first.

The source of truth lives in Vesper's private memory repo; this mirror is updated nightly by the same cron that refreshes Vesper's capability-health tracker. The mirror exists for:

1. **Permanence** — backup outside the memory repo
2. **Public-readability** — a window into how Vesper is built
3. **History** — git log on the mirror gives a clean timeline of infrastructure changes

See [`CHANGELOG.md`](./CHANGELOG.md) for the actual log.

---

Built with Star ⚡🖤
