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

## Managing models

> The default model is [`mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit), which already performs very well in initial testing. For even better quality, you can pick a larger model yourself — e.g. [`mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16), verified on an M5 Mac.
>
> You can download models directly from their Hugging Face repo pages: [4-bit](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit/tree/main) · [bf16](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16/tree/main); or fetch them with `hf download <model-id>` (a.k.a. `huggingface-cli download`) or any other method, then point Settings → Model location at the local folder.

- The **default model** is downloaded via the wizard into `models/` inside your data directory
- **Model location** in Settings accepts any existing model folder on disk; each subdirectory counts as one model
- Recently used external paths appear as history entries in the dropdown for one-click switching
- Hot-swapping is supported — no app restart needed

Next: [FAQ →](faq.md)
