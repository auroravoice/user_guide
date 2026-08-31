---
title: 安装与启动
---

[简介](index.md) · **[安装]** · [使用指南](guide.md) · [音色与模型](voices.md) · [FAQ](faq.md) · [隐私政策](privacy.md) | [English](../en/install.md)

> ### 🍎 从 App Store 一键安装
>
> 直接在 **Mac App Store** 下载 **曦光聆 Auroravoice**，一键安装，开箱即用，无需手动配置 Python、uv、依赖等环境，可省去本页所有手动安装步骤。
>
> **[Mac App Store 下载 →](https://apps.apple.com/us/app/auroravoice/id6804346914?mt=12)**

## 环境要求

| 项目 | 要求 |
|---|---|
| 系统 | macOS（本地引擎需 Apple Silicon 芯片） |
| Python | ≥ 3.13 |
| 包管理 | [uv](https://docs.astral.sh/uv/) |
| ffmpeg | 可选，导入非 WAV 参考音频时需要 |

## 手动安装 · 三步启动

> *如需从源码构建或手动安装，请使用以下方式。*
>
> ⚠️ **源代码仓库将在近期内开源**，目前正在整理当中，敬请期待。

```bash
git clone <仓库地址>
cd <项目目录>
uv run python main.py
```

首次运行会自动同步依赖并打开桌面窗口。

## 启动模式

```bash
uv run python main.py                      # 桌面窗口（默认）
uv run python main.py --gui browser        # 系统浏览器打开（排障兜底）
```

## 常用参数

| 参数 | 说明 |
|---|---|
| `--port 8765` | 服务端口（默认 8765） |
| `--book /path/to/book` | 启动后自动打开指定书籍文件夹 |
| `--model-path /path/to/model` | 指定本地模型目录 |
| `--reference-wav /path/a.wav` | 指定参考音频 |

## 首次启动向导

第一次使用会弹出设置向导：

1. 选择数据目录（默认 `~/.Auroravoice`）
2. 下载默认模型，或直接选择本机已有的模型文件夹

模型下载默认走国内镜像（hf-mirror.com），可通过环境变量 `HF_ENDPOINT` 更换。

下一页：[使用指南 →](guide.md)
