---
title: Installation
---

[Intro](index.md) · **[Install]** · [Guide](guide.md) · [Voices & Models](voices.md) · [FAQ](faq.md) · [Privacy](privacy.md) | [简体中文](../zh/install.md)

> ### 🍎 Install from the App Store (Coming Soon)
>
> Soon you'll be able to download **Auroravoice** directly from the **Apple App Store / Mac App Store** — just search for "Auroravoice" and install with one click. No need to manually set up Python, uv, or other dependencies. This will replace all manual steps below.
>
> **Currently under Apple review — stay tuned!**

## Requirements

| Item | Requirement |
|---|---|
| OS | macOS (Apple Silicon required for the local engine) |
| Python | ≥ 3.13 |
| Tooling | [uv](https://docs.astral.sh/uv/) |
| ffmpeg | Optional — needed to import non-WAV reference audio |

## Manual Installation · Three Steps

> *Before the App Store release, use the manual method below (for developers / early access).*

```bash
git clone <repository-url>
cd <project-directory>
uv run python main.py
```

Dependencies are synced automatically on first run and the desktop window opens.

## Launch modes

```bash
uv run python main.py                      # Desktop window (default)
uv run python main.py --gui browser        # Open in system browser (fallback/debug)
```

## Common options

| Option | Description |
|---|---|
| `--port 8765` | Server port (default 8765) |
| `--book /path/to/book` | Auto-open a book folder on startup |
| `--model-path /path/to/model` | Use a specific local model directory |
| `--reference-wav /path/a.wav` | Use a specific reference audio |

## First-run wizard

On first launch a setup wizard appears:

1. Pick a data directory (default `~/.Auroravoice`)
2. Download the default model, or point to an existing model folder on disk

Downloads use a mirror endpoint by default; change it via the `HF_ENDPOINT` environment variable.

Next: [User Guide →](guide.md)
