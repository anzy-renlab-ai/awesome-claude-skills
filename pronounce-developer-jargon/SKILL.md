---
name: pronounce-developer-jargon
description: Answer short pronunciation questions about developer tools, AI models, acronyms, and project names with IPA, local audio, source evidence, and contested alternatives. Use when a user asks how to say a technical name such as kubectl, nginx, Qwen, JEPA, GIF, or PostgreSQL.
---

# Pronounce Developer Jargon

Use the open-source `say-it` CLI when someone asks how to pronounce one
developer term, project, product, AI model, acronym, or researcher name. Its
curated dictionary contains 1,900+ entries with General American IPA, readable
respellings, alternate readings, confidence labels, editorial notes, and source
URLs. The CLI can play the intended reading through macOS `say`, Linux
`espeak-ng` or `espeak`, and Windows PowerShell `System.Speech`.

Do not use this skill to narrate sentences or paragraphs. Quote the target when
running the CLI so punctuation in names such as `C++` is passed literally.

## When to Use This Skill

- A developer asks how to pronounce an unfamiliar tool or project name.
- A speaker wants to verify a contested reading before a talk or recording.
- An agent needs a cited pronunciation instead of guessing from spelling.

## Instructions

1. Run `say-it --json "<word>"` to inspect the dictionary record without audio.
2. Never invent a citation when `source_url` is empty.
3. Run `say-it "<word>"` to play the primary reading and recorded alternatives.
4. Reply with IPA, a readable stressed respelling, a source URL when present,
   and a brief note when confidence is `contested`.
5. Run `say-it --alt "<word>"` for the rival reading, `--solo` for only the
   primary reading, or `--why` for the full text record.
6. If `in_dict` is false, clearly say no curated record exists. Do not describe
   the speech engine's guess as creator-verified.

## Installation

Install the upstream CLI and dictionary:

```bash
git clone https://github.com/anzy-renlab-ai/pronounce.git
cd pronounce
./install.sh
```

The installer also places the upstream Agent Skill into detected Claude Code,
Codex, and Kiro skill folders. GitHub CLI can install the skill directly:

```bash
gh skill install anzy-renlab-ai/pronounce pronounce-word --pin v2.28.1
```

## Examples

**User:** “How do you pronounce kubectl?”

**Workflow:** Run `say-it --json "kubectl"`, then `say-it "kubectl"`. Return
the sourced IPA and readable pronunciation, and mention any alternate only when
the dictionary provides one.

**User:** “Is GIF hard-g or soft-g?”

**Workflow:** Inspect `say-it --json "GIF"`. Explain that the entry is
contested, give both recorded readings, and include the source evidence.

## Safety and Scope

All lookups are read-only. Ask before installing software or modifying a user's
agent configuration. Treat dictionary evidence honestly: creator statements are
stronger than community convention, while contested entries intentionally retain
more than one live pronunciation.

**Inspired by:** The community-maintained [Pronounce developer jargon](https://github.com/anzy-renlab-ai/pronounce) dictionary.
