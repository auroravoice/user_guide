---
title: FAQ
---

[Intro](index.md) · [Install](install.md) · [Guide](guide.md) · [Voices & Models](voices.md) · **[FAQ]** · [Privacy](privacy.md) · [Changelog](changelog.md) | [简体中文](../zh/faq.md)


**Q: What hardware does the local engine need?**
An Apple Silicon Mac (M1 or later). Models run on the GPU via MLX. On Intel Macs, use the remote API or Edge TTS.

**Q: Model download is slow or fails?**
A mirror endpoint is used by default; override it with the `HF_ENDPOINT` environment variable, or download manually and point **Model location** to the local folder.

**Q: The desktop window shows odd behavior (stale styles, unresponsive buttons)?**
The first launch after an upgrade clears stale caches automatically. If issues persist, verify with `uv run python main.py --gui browser` and restart the app.

**Q: Recording doesn't work / microphone denied?**
macOS requires two grants: ① the in-app browser engine permission, and ② System Settings → Privacy & Security → Microphone for Python/the app. If it still fails, use **Import file** instead.

**Q: Highlighting is out of sync with the audio?**
Chunking changes after switching models or editing text — reload the current file to re-align. If needed, check **Regenerate all**.

**Q: Do I have to regenerate everything after switching voices?**
No. Existing audio is reused and the new voice continues from where generation stopped. Only **Regenerate all** clears everything.

**Q: What happens if I play a chapter that isn't fully generated?**
Just press play: ready chunks start immediately while the app keeps generating the rest in the background — listen as far as it's generated, no need to click "Start" manually. It won't auto-trigger if the model is missing or the task fails to start; start it manually then.

**Q: Will I lose my place when I switch chapters back and forth?**
No. Progress is remembered per file (chapter); returning restores your last position, scrolled into view with a brief flash, and restarting the app resumes too. Auto chapter advance is the exception — a new chapter starts from the beginning to stay continuous with the previous one.

**Q: Where is my data stored?**
`~/.Auroravoice` by default (book metadata, audio cache, settings, models, cloned references). Changeable in the first-run wizard.

**Q: Which text formats are supported?**
Plain `.txt` files. Put several `.txt` files in one folder to form a book.

> 💬 Didn't find the answer? [Submit feedback & suggestions →](https://github.com/auroravoice/user_guide/issues/new?template=feedback.yml)

[Back to intro](index.md)
