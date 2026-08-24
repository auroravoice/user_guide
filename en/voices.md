---
title: Voices & Models
---

[Intro](index.md) · [Install](install.md) · [Guide](guide.md) · **[Voices & Models]** · [FAQ](faq.md) · [Privacy](privacy.md) | [简体中文](../zh/voices.md)


## Three engines

| Engine | How | Best for |
|---|---|---|
| **Local engine** (recommended) | On-device MLX inference | Apple Silicon Macs; fully offline; supports cloning |
| Remote API | Gradio client to a remote service | Fallback when local hardware is unavailable |
| Edge TTS | Online service | Quick start, no model download |

> Note: the **Remote API uses Confucius4** — a built-in Gradio client calls its service directly, with no model download required.

> Note: the **Remote API and Edge TTS** are online/remote services and are currently in testing — these services are **not yet enabled** in the App Store version.

Switch engines from the sidebar dropdown. After switching engines or models, reload the current file (chunking may change).

## Four voice modes

Depending on the loaded model's architecture:

| Mode | Description | UI |
|---|---|---|
| **Voice cloning** | Imitate a voice from reference audio | Dropdown + 🎤 button |
| Built-in speakers | Model-provided voices | Dropdown |
| Voice design | Describe a voice in text | Text input + presets |
| Default voice | Use the model's default | Single-item dropdown |

## Creating a cloned voice

Click the 🎤 button next to the voice dropdown:

- **Record**: read the sample text aloud — pause / re-record supported
  - Under 10s can't be saved; 20–40s gives the best quality
- **Import file**: `.wav` `.mp3` `.flac` `.ogg` `.m4a`, auto-transcoded

![Recording a reference voice](../pics/screenshot_record_reference_voice.png){: style="max-width:80%;height:auto;display:block;margin:16px auto;border:1px solid #ddd;border-radius:6px;"}

> Tip: quiet room, ~20 cm from the mic, natural pace.
> Advanced: add a same-named `.txt` transcript next to the audio (`x.wav` + `x.txt`) for higher similarity.

## Demos · Cloned Voices

> All samples below are cloned locally with [`Qwen3-TTS-12Hz-1.7B-Base-4bit`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit) from reference audio (24kHz). No text leaves your machine. Click ▶ to play.

<div class="voice-demos" markdown="0">
  <div class="voice-card">
    <div class="voice-name">Calm Male <span class="voice-ref">ref: Male.wav</span></div>
    <div class="voice-text">“She walked along the quiet path, humming a gentle tune, with sunlight dancing through the trees.”</div>
    <audio controls preload="metadata" src="{{ '/assets/audio/voices/en/male_en.mp3' | relative_url }}"></audio>
  </div>
  <div class="voice-card">
    <div class="voice-name">Mature Female <span class="voice-ref">ref: LadyMary.mp3</span></div>
    <div class="voice-text">“The house was quiet and the world was calm. The reader became the book, and the book became the reader.”</div>
    <audio controls preload="metadata" src="{{ '/assets/audio/voices/en/ladymary_en.mp3' | relative_url }}"></audio>
  </div>
  <div class="voice-card">
    <div class="voice-name">Soft Female <span class="voice-ref">ref: SoftFemale.mp3</span></div>
    <div class="voice-text">“In the soft morning light, the lake was still, as if time itself had paused to listen.”</div>
    <audio controls preload="metadata" src="{{ '/assets/audio/voices/en/softfemale_en.mp3' | relative_url }}"></audio>
  </div>
</div>

<style>
.voice-demos{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:16px;margin:16px 0}
.voice-card{border:1px solid #e3e3e3;border-radius:10px;padding:14px 16px;background:#fafafa}
.voice-card .voice-name{font-weight:600;margin-bottom:6px}
.voice-card .voice-ref{font-weight:400;color:#888;font-size:0.85em;margin-left:6px}
.voice-card .voice-text{color:#555;font-size:0.92em;margin-bottom:10px;line-height:1.5}
.voice-card audio{width:100%}
</style>

## Managing models

> The default model is [`mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit), which already performs very well in initial testing. For even better quality, you can pick a larger model yourself — e.g. [`mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16), verified on an M5 Mac.
>
> You can download models directly from their Hugging Face repo pages: [4-bit](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit/tree/main) · [bf16](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16/tree/main); or fetch them with `hf download <model-id>` (a.k.a. `huggingface-cli download`) or any other method, then point Settings → Model location at the local folder.

- The **default model** is downloaded via the wizard into `models/` inside your data directory
- **Model location** in Settings accepts any existing model folder on disk; each subdirectory counts as one model
- Recently used external paths appear as history entries in the dropdown for one-click switching
- Hot-swapping is supported — no app restart needed

Next: [FAQ →](faq.md)
