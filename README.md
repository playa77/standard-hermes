# Standard Hermes

A Hermes profile distribution built from the current default profile. Release `v1.0.0` packages the current profile configuration and personality, every installed Hermes skill, and the complete enabled Superpowers plugin.

## Installed skillset

Based on a Hermes fresh install, this profile includes:

- **Superpowers** — the complete plugin source (version 6.4.2), including hooks, documentation, scripts, assets, tests, and all 15 bundled skills.
- **Deep Research** skill.
- **Handover** skill.
- All other skills installed in the source profile. The list below is the complete 61-skill Hermes set; Superpowers skills are listed separately.

### Hermes skills (61)

- `apple/`: apple-notes, apple-reminders, findmy, imessage
- `autonomous-ai-agents/`: claude-code, codex, computer-use, hermes-agent, hermes-plugin-management, opencode
- `creative/`: architecture-diagram, ascii-video, baoyu-infographic, claude-design, design-md, humanizer, manim-video, p5js, popular-web-designs, songwriting-and-ai-music
- `deep-research` (top-level skill folder)
- `devops/`: sdlc-review
- `email/`: email-inbox-triage, himalaya
- `media/`: gif-search, songsee, youtube-content
- `note-taking/`: obsidian
- `productivity/`: airtable, box, document-to-action-items, docx, google-workspace, handover, maps, meeting-action-items, notion, pdf, powerpoint, product-price-monitor, teams-meeting-pipeline, weekly-review-planning, xlsx
- `research/`: arxiv, competitor-news-monitor, grounded-citations, llm-wiki
- `social-media/`: xurl
- `software-development/`: codebase-inspection, dogfood, github, hermes-agent-skill-authoring, inspecting-hermes-desktop-dom, node-inspect-debugger, python-debugpy, requesting-code-review, simplify-code, spike, systematic-debugging, test-driven-development
- `web/`: blocked-page-recovery

### Superpowers skills (15)

brainstorming, diagnosing-superpowers, dispatching-parallel-agents, executing-plans, finishing-a-development-branch, receiving-code-review, requesting-code-review, subagent-driven-development, systematic-debugging, test-driven-development, using-git-worktrees, using-superpowers, verification-before-completion, writing-plans, writing-skills.

## Install

```bash
hermes profile install github.com/playa77/standard-hermes --alias
```

The default model configuration is `openai/gpt-6-luna-pro` via OpenRouter. Bring your own `OPENROUTER_API_KEY`; the installer will generate `.env.EXAMPLE` from the manifest. Change the provider/model as needed for your setup. To update later, run `hermes profile update standard-hermes`.

## Secrets and local data

No API keys or secrets are included. `.env`, `auth.json`, memories, sessions, logs, caches, and runtime state are excluded. Credential-like examples in the bundled Hermes MCP reference were replaced with non-secret placeholders. Configure credentials locally after installation; do not commit your `.env`.

## Contents

- `distribution.yaml` — distribution metadata and owned paths.
- `config.yaml`, `SOUL.md` — current profile settings and personality (with credentials excluded).
- `skills/` — all 61 installed Hermes skills with their references, scripts, and assets.
- `plugins/superpowers/` — complete Superpowers plugin source.
