---
title: Changelog
---

[Intro](index.md) · [Install](install.md) · [Guide](guide.md) · [Voices & Models](voices.md) · [FAQ](faq.md) · [Privacy](privacy.md) · **[Changelog]** | **[简体中文](../zh/changelog.md)**


Major updates (new features and fixes), newest first.

## v1.0.7 · 2026-09-06

"Uninterrupted listening" — this release focuses on resuming playback of unfinished chapters and per-file progress memory.

### Added

- **Auto-resume generation**: when you play a chapter whose audio isn't fully generated yet, the app keeps generating the remaining chunks in the background while playing what's already ready — listen as far as it's generated, no manual "Start generation" needed. A short toast confirms the background task has started
- **Auto chapter advance also resumes generation**: after continuous playback rolls into a new chapter, any missing audio there is generated automatically as well
- **Per-file progress memory**: playback position, in-chunk offset, and bookmark are now saved for each chapter. Coming back to a chapter restores your last position, scrolls it into view with a brief flash; restarting the app resumes playback too. Auto chapter advance is the exception — a new chapter always starts from the beginning to keep continuous with the previous one

### Fixed

- Hitting an ungenerated chunk during playback no longer skips to the next chapter: the app waits, triggers generation, and resumes playback automatically once audio is ready (waiting is strictly distinguished from a user pause)
- Legacy audio files missing split records now self-heal on first synthesis: records are rebuilt from the current split and reused precisely afterwards
- After switching chapters, the text area scroll resets to top instead of keeping the previous chapter's bottom position (which showed a blank new chapter)

## v1.0.6 · 2026-08-25

### Added

- Model download now reports progress during the download
- Settings dialog is resizable by dragging
- Improved model-path settings UI and logic

### Fixed

- Toast notifications get backdrop adjustments for better visibility

## v1.0.4 · 2026-08-25

- Avoid scipy's use of private Accelerate LAPACK/BLAS symbols for App Store compliance

## v1.0.0 · 2026-08-22

First public release:

- **Local inference**: on-device speech synthesis via MLX on Apple Silicon — your text never leaves the machine
- **Voice cloning**: record in-app or import an audio clip; a few dozen seconds is enough to create your own voice
- **Listen while generating**: chunk-by-chunk synthesis with instant playback; resume generation reuses finished chunks
- **Multiple engines**: local MLX / remote API / Edge TTS
- **Bilingual UI & themes**: 中文 / English, 5 preset themes
- **Progress memory**: reading position saved automatically, resumed on restart

> Earlier development versions are not listed here.

> 💬 Ideas or issues? [Submit feedback →](https://github.com/auroravoice/user_guide/issues/new?template=feedback.yml)

[Back to intro](index.md)
