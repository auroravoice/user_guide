---
title: User Guide
---

[Intro](index.md) · [Install](install.md) · **[Guide]** · [Voices & Models](voices.md) · [FAQ](faq.md) · [Privacy](privacy.md) · [Changelog](changelog.md) | [简体中文](../zh/guide.md)


## 1. Open a book

- Click **Open Book** in the sidebar and choose a folder — its `.txt` files become your reading list
- The **Recent** list gives one-click access to previously opened books
- Or launch with `--book /path/to/book`

## 2. Generate speech

1. Pick a file from the list
2. Choose an engine and a voice in the sidebar
3. Click **Start** — the text is split into chunks and synthesized one by one
4. Watch the progress bar; finished chunks are **playable immediately**

> Clicking Start again after an interruption resumes from where it stopped — completed chunks are reused, never re-generated.
> In fact you usually don't need to click at all: just **play** a partially generated chapter and the app keeps generating the rest in the background, playing what's ready while the remainder catches up.

## 3. Playback

| Action | Effect |
|---|---|
| Play / Pause | Control the current paragraph |
| Single-click text | Mark it with an underline |
| Double-click text | Start playback from that spot |
| Speed slider | 0.5x – 2.0x |

The sentence being read is highlighted; a paragraph number turns green once all of its chunks are ready.

## 4. Full regeneration

After switching voices, generation normally **continues** (existing audio kept). To redo everything with current settings, check **Regenerate all** before starting.

## 5. Automatic progress saving

Progress is remembered **per file (chapter)**: position, in-chunk offset, and bookmark are saved every 5 seconds — plus immediately on pause, stop, or file switch.

- Returning to a chapter restores your last position, scrolled into view with a brief flash
- Reopening the app reopens the last book and resumes playback
- Auto chapter advance is the exception: a new chapter starts from the beginning (continuous with the previous one), with missing audio generated automatically

## 6. Settings

The settings dialog offers:

- **Language / Theme / Font / Size / Line height** (preview instantly; applied on Save)
- **Model location** — use another model already on disk (takes effect immediately)
- **About** — version info

Next: [Voices & Models →](voices.md)
