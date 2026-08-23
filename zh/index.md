---
title: 曦光聆 · 简体中文
---

[简介](index.md) · [安装](install.md) · [使用指南](guide.md) · [音色与模型](voices.md) · [FAQ](faq.md) · [隐私政策](privacy.md) | **[English](../en/index.md)**


**风声雨声读书声，声声入耳。**

曦光聆是一款本地运行的桌面应用：打开一个书籍文件夹（内含 `.txt` 文本），应用会把文本智能分块，用自然真人语音逐段朗读——支持声音克隆、断点续读、语速调节。

<div class="showcase">
  <div class="card">
    <div class="video-click" data-id="7lehH5ZEo2U">
      <img src="../pics/video_poster.png" alt="演示视频封面" onerror="this.onerror=null;this.src='https://img.youtube.com/vi/7lehH5ZEo2U/maxresdefault.jpg';" />
      <span class="play" aria-label="播放演示视频"></span>
    </div>
    <div class="cap">演示视频 · 点击播放</div>
  </div>
  <div class="card">
    <img src="../pics/screenshot_chinese_reading.png" alt="中文朗读界面" />
    <div class="cap">中文朗读界面</div>
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

## 核心特性

- **本地推理**：基于 MLX，模型跑在你自己的 Apple Silicon 芯片上，文本不上传
- **边生成边听**：逐块合成、即时播放，不用等整本书合成完
- **声音克隆**：在应用里朗读几十秒，或导入一段音频，即可创建专属音色
- **断点续合**：已生成的段落直接复用，中断后从上次位置继续
- **进度记忆**：每 5 秒自动保存阅读位置，重启后接着听
- **多引擎**：本地 MLX（推荐）/ 远程 API / Edge TTS 三种引擎随时切换
- **双语界面**：中文 / English 一键切换，5 个预设主题

## 适合谁

- 想把小说、文章「听」完的人
- 在意隐私、希望语音合成完全离线的人
- 想要用自己的声音来朗读文字的人

下一页：[安装与启动 →](install.md)
