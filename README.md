# Multi-thread Embroidery

A Codex skill for macro stop-motion embroidery videos: multiple colored thread ends rise, cross, and tighten as a character gradually forms on fabric.

The defining effect is **the relationship between moving threads and accumulating stitches**, rather than a single needle drawing, a scanning reveal, or a finished image fading in.

## What it does

- Uses motion footage and character images to constrain animation and identity separately.
- Provides prompt templates, generation routes, and frame-based acceptance criteria.
- Tracks asynchronous jobs to avoid duplicate paid submissions after delays or timeouts.
- Identifies common failures: thick yarn, whole-region fills, an already finished opening, and leftover features from the original character.

## Installation

Clone this repository into your Codex skills directory:

```bash
git clone https://github.com/fatelei/multi-thread-embroidery.git ~/.codex/skills/multi-thread-embroidery
```

If `CODEX_HOME` is set, use its `skills/` directory instead. If a skill with this name already exists, inspect it before updating to preserve local changes. Invoke the skill in a Codex session that has discovered it.

```text
multi-thread-embroidery/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── prompt.md
    ├── lessons.md
    └── provider.md
```

## Usage

Provide a reference video and a character image, then ask:

> Use $multi-thread-embroidery to create a fine stop-motion embroidery video of this character, following the reference video's interweaving and tightening threads. Generate one sample first and verify the progression from blank fabric to finished embroidery.

You can also provide only a motion reference and retain its character for a generative remaster.

## Requirements

This is a workflow skill, not a video model or standalone generator. The environment needs media inspection tools and an available video generation or editing service. The skill files alone cannot generate video.

The validated workflow used qwen-mm-plugins media tools and HappyHorse video editing. Check current tool interfaces and model availability at execution time. Paid services require your own credentials and incur generation costs. Never commit API keys.

## Validated scope and limitations

The workflow validated and accepted by the user is **a generative remaster of an input video that retains the same character**. It closely follows the source composition and motion; it is not generation from scratch.

Reliable arbitrary character replacement has not been established. A detailed finished reference image can improve character recognition, but does not guarantee convincing multi-thread motion. Deliveries should disclose their generation route and remaining differences.

## Files

- [Skill instructions](SKILL.md): route selection, production, and verification.
- [Prompt templates](references/prompt.md): same-character remastering and replacement constraints.
- [Observed lessons](references/lessons.md): actual outcomes and limitations.
- [Provider notes](references/provider.md): credentials, task recovery, and error handling.

This repository contains only skill documentation and interface metadata. It does not include source videos, character artwork, generated clips, account configuration, or credentials.
