---
title: 音色与模型
---

[简介](index.md) · [安装](install.md) · [使用指南](guide.md) · **[音色与模型]** · [FAQ](faq.md) · [隐私政策](privacy.md) | [English](../en/voices.md)


## 三种引擎

| 引擎 | 方式 | 适用 |
|---|---|---|
| **本地引擎**（推荐） | MLX 本地推理 | Apple Silicon Mac，完全离线，支持克隆 |
| 远程 API | Gradio Client 调用远程服务 | 没有合适本地硬件时备用 |
| Edge TTS | 在线服务 | 免下载模型，快速试听 |

> 具体说明：远程 API 使用的是 **Confucius4** 服务——应用内置 Gradio Client 直接调用，无需下载本地模型。

> 说明：远程 API 与 Edge TTS 都属于远程 / 在线服务，目前正处于测试阶段，**上述服务在 App Store 版本中尚未开通**。

在侧栏的引擎下拉框中切换。切换引擎或模型后请重新载入当前文件（分块方式可能变化）。

## 四种音色模式

取决于当前加载的模型架构：

| 模式 | 说明 | 界面形态 |
|---|---|---|
| **声音克隆** | 用参考音频模仿音色 | 下拉框 + 🎤 按钮 |
| **内置音色** | 模型自带说话人 | 下拉框 |
| **文本造音色** | 用一段描述文字生成音色 | 输入框 + 预设列表 |
| 默认音色 | 使用模型默认 | 单项下拉 |

## 创建克隆音色

点击音色下拉框旁的 🎤 按钮，两种方式入库：

- **录音**：照着样本文本朗读即可，支持暂停 / 重录
  - 不足 10 秒无法保存；20~40 秒效果最佳（甜区）
- **导入文件**：支持 `.wav` `.mp3` `.flac` `.ogg` `.m4a`，自动转码

![录制参考音色](../pics/screenshot_record_reference_voice.png){: style="max-width:80%;height:auto;display:block;margin:16px auto;border:1px solid #ddd;border-radius:6px;"}

> 建议：安静环境、离麦克风 20cm 左右、自然语速。
> 进阶：为音频准备同名 `.txt` 转写文件（如 `x.wav` + `x.txt`），可提升克隆相似度。

## 试听 · 克隆音色展示

> 以下试听均由本地模型 [`Qwen3-TTS-12Hz-1.7B-Base-4bit`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit) 基于参考音频克隆生成（24kHz），文本未出本机。点击 ▶ 试听。

<div class="voice-demos" markdown="0">
  <div class="voice-card">
    <div class="voice-name">沉稳男声 <span class="voice-ref">参考：Male.wav</span></div>
    <div class="voice-text">“夜色已深，窗外的雨轻轻敲着屋檐。她合上书，轻声说，明天又是新的一天。”</div>
    <audio controls preload="metadata" src="{{ '/assets/audio/voices/zh/male_zh.mp3' | relative_url }}"></audio>
  </div>
  <div class="voice-card">
    <div class="voice-name">温柔女声 · 瓦尔登湖 <span class="voice-ref">参考：温柔瓦尔登湖.mp3</span></div>
    <div class="voice-text">“瓦尔登湖的清晨，薄雾在湖面上缓缓浮动，时间在这里变得很慢很慢。”</div>
    <audio controls preload="metadata" src="{{ '/assets/audio/voices/zh/walden_gentle.mp3' | relative_url }}"></audio>
  </div>
  <div class="voice-card">
    <div class="voice-name">清新少女 <span class="voice-ref">参考：蔡紫小小姑娘.mp3</span></div>
    <div class="voice-text">“小小的姑娘踮起脚尖，在洒满阳光的小路上哼着歌，向着远方跑去。”</div>
    <audio controls preload="metadata" src="{{ '/assets/audio/voices/zh/caizi_girl.mp3' | relative_url }}"></audio>
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

## 模型管理

> 默认模型为 [`mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit)，初步测试效果已经很好。如需更好的效果，也可以自行选择更大的模型——例如 [`mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16`](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16) 已在 M5 芯片上实测通过。
>
> 模型可从 Hugging Face 仓库页面直接下载：[4bit 版](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-4bit/tree/main) · [bf16 版](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-bf16/tree/main)；也可以用 `hf download <模型名>`（即 `huggingface-cli download`）或其他任意方式下载，放到本地后在设置「模型位置」中指定即可。

- **默认模型**首次使用时按向导下载到数据目录 `models/`
- 设置对话框「模型位置」可选择本机已有模型目录；多个模型时数据目录下每个子目录算一个
- 最近用过的外部模型路径会出现在下拉历史里，直接切换无需重新找路径
- 模型支持热切换，无需重启应用

下一页：[FAQ →](faq.md)
