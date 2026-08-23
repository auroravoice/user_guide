---
title: Auroravoice · English
---

[Intro](index.md) · [Install](install.md) · [Guide](guide.md) · [Voices & Models](voices.md) · [FAQ](faq.md) · [Privacy](privacy.md) | **[简体中文](../zh/index.md)**


*"The house was quiet and the world was calm. The reader became the book…"*

Auroravoice is a local desktop app for macOS that reads Chinese (and English) text files aloud with natural, human-like voices — fully offline, powered by on-device MLX inference.

<div class="showcase">
  <div class="card">
    <div class="video-click" data-id="7lehH5ZEo2U">
      <img src="../pics/video_poster.png" alt="Demo video cover" onerror="this.onerror=null;this.src='https://img.youtube.com/vi/7lehH5ZEo2U/maxresdefault.jpg';" />
      <span class="play" aria-label="Play demo video"></span>
    </div>
    <div class="cap">Demo video · click to play</div>
  </div>
  <div class="card">
    <img src="../pics/screenshot_english_reading.png" alt="English reading interface" />
    <div class="cap">English reading interface</div>
  </div>
</div>

<script>
  document.querySelectorAll('.video-click').forEach(function (el) {
    el.addEventListener('click', function () {
      var id = el.getAttribute('data-id');
      var wrap = document.createElement('div');
      wrap.className = 'video-wrap';
      wrap.innerHTML = '<iframe src="https://www.youtube.com/embed/' + id + '?autoplay=1&rel=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>';
      el.parentNode.replaceChild(wrap, el);
    });
  });
</script>

## Highlights

- **Local inference** — models run on your Apple Silicon Mac; your text never leaves the machine
- **Listen while generating** — chunk-by-chunk synthesis, playback starts immediately
- **Voice cloning** — read a sample in-app or import audio; a personal voice in under a minute
- **Resume anywhere** — progress auto-saved every few seconds; synthesis picks up where it stopped
- **Multi-engine** — local MLX (recommended), remote API, or Edge TTS
- **Bilingual UI** — 中文 / English, 5 preset themes

## Who it's for

- Anyone who'd rather *listen* to novels and articles
- Privacy-conscious users who want TTS fully offline
- People who want text read in their own voice

Next: [Installation →](install.md)
