---
name: handover
description: Create a portable handoff for another agent.
version: 0.1.0
author: Matt Pocock, adapted for Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [handoff, session, portability]
    related_skills: []
---

Only create a handoff when the user explicitly invokes `/handover` or otherwise asks for a portable handoff. Create one Markdown document so a fresh agent can continue the work. Save it in the operating system's temporary directory, not the current workspace, and return the exact path. The value is portability, not compression.

## When to use

Use `/handover` when context must travel to a different harness, directory or repository, a colleague, or a parallel side task. If the work stays in the same session, prefer `/compact`; use `/clear` only when prior context is disposable. For a parallel fork that can share the same harness and directory, a session fork may be simpler than a file.

## Handoff contents

- State the active task, what is in flight, why it matters, and the next concrete steps. If the user supplied a focus, tailor the handoff to it.
- Add a **Suggested skills** section naming Hermes skills the next agent should load when useful.
- Reference existing specs, plans, ADRs, issues, commits, diffs, and other durable artifacts by path or URL; do not copy their contents.
- Distinguish verified facts from assumptions. The next agent may treat the handoff as a contract, so do not present guesses as facts.
- Redact secrets and sensitive personal information, including API keys, passwords, and tokens.
- Keep the original session untouched when the handoff is for a side task; a handoff file is a portable copy, not a command to end this session.

Before returning, read the document once to confirm it is concise, actionable without the original conversation, references existing artifacts instead of duplicating them, and contains no secrets. Give the user its full path.