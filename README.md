<div align="center">
<img src="https://github.com/lllyasviel/Fooocus/assets/19834515/483fb86d-c9a2-4c20-997c-46dafc124f25">

<div align="center">

<img src="https://github.com/lllyasviel/Fooocus/assets/19834515/483fb86d-c9a2-4c20-997c-46dafc124f25">

# ✨ AI Image Generation & Cartoonization ✨

**Offline text-to-image generation and cartoon/anime-style stylization, built on Fooocus (Stable Diffusion XL).**

![Version](https://img.shields.io/badge/Version-Modified-blue)
![Platform](https://img.shields.io/badge/Platform-Windows%20|%20Linux%20|%20Colab-brightgreen)
![Model](https://img.shields.io/badge/Model-Stable%20Diffusion%20XL-orange)
![UI](https://img.shields.io/badge/UI-Gradio-ff7c00)
![License](https://img.shields.io/badge/License-Open--Source-green)

</div>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [How It Works](#-how-it-works)
- [Style Presets & Models](#-style-presets--models)
- [Quick Start](#-quick-start)
  - [Windows](#windows)
  - [Google Colab](#google-colab)
  - [Linux](#linux)
  - [Docker](#docker)
- [System Requirements](#-system-requirements)
- [Usage Tips](#-usage-tips)
- [Advanced Features](#-advanced-features)
- [Configuration](#-configuration)
- [Project Structure](#-project-structure)
- [What I Worked On](#-what-i-worked-on)
- [Credits & Attribution](#-credits--attribution)
- [License](#-license)

---

## 🚀 Overview

This project is an **offline, GPU-accelerated image generation app** that turns plain text prompts into high-quality images and supports **cartoon/anime-style** and **realistic** outputs through dedicated preset modes. It is built on **[Fooocus](https://github.com/lllyasviel/Fooocus)**, an open-source image generator based on the **Stable Diffusion XL (SDXL)** architecture with a simple **Gradio** web interface.

The goal is a *Midjourney-like* experience that runs entirely on your own machine — no API keys, no cloud cost, and almost no manual parameter tuning. You type a prompt, pick a style, and generate. This build runs with a cleaner, distraction-free interface (Gradio footer/analytics disabled) and ships with one-click launchers and a Google Colab notebook for users without a local GPU.

> Built on the open-source Fooocus by **lllyasviel**, starting from the customized base by **Abhiram** ([abhi963007/Fooocus](https://github.com/abhi963007/Fooocus)). See [Credits & Attribution](#-credits--attribution).

---

## ✨ Key Features

- 🖼️ **High-quality text-to-image** — SDXL results without heavy prompt engineering or parameter tweaking.
- 🎨 **Cartoon / anime stylization** — dedicated anime preset for stylized, illustration-like output.
- 📸 **Realistic mode** — a photorealistic preset for natural-looking images.
- 🔍 **Clean interface** — Gradio footer/analytics disabled for a distraction-free UI.
- 🧩 **Full image toolkit** — variations, upscaling, inpainting/outpainting, image prompting, and FaceSwap.
- 🧠 **Smart prompting** — offline GPT-2-based prompt expansion ("Fooocus V2") for richer results from short prompts.
- ☁️ **Runs anywhere** — one-click `.bat` launchers on Windows, a Google Colab notebook, Linux support, and Docker.

---

## 🔧 How It Works

```
            ┌──────────────┐     ┌───────────────────────┐     ┌──────────────────┐
  Prompt →  │  Gradio Web  │ →   │  Prompt Expansion     │ →   │  SDXL Pipeline   │ →  Image
            │     UI       │     │  (Fooocus V2, GPT-2)  │     │  + sampler/styles│
            └──────────────┘     └───────────────────────┘     └──────────────────┘
                                                                        │
                                                          Style preset (Standard / Anime / Realistic)
```

1. **Enter a prompt** in the Gradio UI and choose a style preset.
2. **Prompt expansion** (Fooocus V2) enriches short prompts for better composition.
3. The **SDXL pipeline** generates the image using tuned samplers and the selected style.
4. Optionally **refine** with upscaling, variations, inpainting/outpainting, or FaceSwap.

---

## 🎭 Style Presets & Models

| Mode | Launcher | Preset Arg | Default Model | Best For |
|------|----------|-----------|---------------|----------|
| **Standard** | `run.bat` | *(none)* | juggernautXL | General-purpose images |
| **Anime / Cartoon** | `run_anime.bat` | `--preset anime` | animaPencilXL | Cartoon & anime stylization |
| **Realistic** | `run_realistic.bat` | `--preset realistic` | realisticStockPhoto | Photorealistic images |

> Models download **automatically** on first launch (no manual setup needed). You can also switch presets directly in the browser.

---

## ⚡ Quick Start

### Windows

```bash
run.bat              # Standard mode
run_anime.bat        # Anime / cartoon style
run_realistic.bat    # Realistic style
run_public.bat       # Generate a shareable public link
```

Unzip the package and run the desired `.bat`. The app opens in your browser; models download automatically the first time.

### Google Colab

Open **`fooocus_colab_no_footer.ipynb`** in Google Colab to run on a free cloud GPU (footer/analytics disabled). For a style preset, set the launch line to:

```bash
!python entry_with_update.py --share --always-high-vram --preset anime
```

### Linux

```bash
git clone https://github.com/Axwathy/ai-image-cartoonization.git
cd ai-image-cartoonization
python3 -m venv fooocus_env
source fooocus_env/bin/activate
pip install -r requirements_versions.txt
python entry_with_update.py            # add --preset anime / --preset realistic as needed
```

### Docker

See [`docker.md`](docker.md) for containerized setup with `docker-compose.yml`.

---

## 💻 System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| GPU | 4 GB NVIDIA VRAM | 8 GB+ VRAM (RTX series) |
| RAM | 8 GB system RAM | 16 GB+ system RAM |
| GPU support | NVIDIA (full) · AMD (beta, DirectML/ROCm) | NVIDIA RTX |
| OS | Windows / Linux / macOS (M1/M2) | Windows or Linux + NVIDIA |

> System swap is required on the minimum spec. Performance scales strongly with VRAM.

---

## 💡 Usage Tips

- 🎯 Try the built-in styles under the **Styles** tab; **Fooocus V2** gives strong results with minimal prompting.
- 🎨 Use **`run_anime.bat`** (or the anime preset) for cartoon-style stylization.
- 🚫 Use **negative prompts** to exclude unwanted elements (e.g., `low quality`).
- 📐 Try different **aspect ratios** for different compositions.
- 🖌️ For edits, use **Inpaint/Outpaint**; for references, use **Image Prompt**.

---

## 🧰 Advanced Features

- **Variations & upscaling** — subtle/strong variations and 1.5×/2× upscale.
- **Inpainting & outpainting** — Fooocus's own inpaint models for cleaner edits.
- **Image prompting** — use reference images to guide generation.
- **FaceSwap** — via InsightFace under Image Prompt → Advanced.
- **Inline prompt tools** — wildcards (`__color__ flower`), array processing (`[[red, green, blue]] flower`), and inline LoRAs (`flower <lora:sunflowers:1.2>`).
- **Authentication & sharing** — `--listen` for LAN, `--share` for a public Gradio link, and `auth.json` for basic auth.

---

## ⚙️ Configuration

A `config.txt` is generated after the first launch and can be edited to change model paths and defaults (sampler, CFG scale, default styles, negative prompt, etc.). If anything breaks, delete `config.txt` to restore defaults. A safer route is simply switching between the Standard / Anime / Realistic launchers.

---

## 📂 Project Structure

```
ai-image-cartoonization/
├── modules/               # Core generation pipeline
├── ldm_patched/           # Patched latent diffusion backend
├── models/                # Checkpoints, LoRAs, inpaint, etc. (auto-downloaded)
├── presets/               # Standard / anime / realistic preset configs
├── sdxl_styles/           # Style template definitions
├── language/              # UI translations (i18n)
├── wildcards/             # Wildcard prompt files
├── run.bat / run_anime.bat / run_realistic.bat
├── fooocus_colab_no_footer.ipynb
├── entry_with_update.py   # Launcher
└── webui.py               # Gradio app
```

---

## 🙋 What I Worked On

<!--
  IMPORTANT — replace these with YOUR real contributions so the repo honestly reflects your work.
  Keep only true lines; delete the rest.
-->
- Deployed and configured the Fooocus / SDXL pipeline locally (Windows) and on Google Colab for text-to-image generation and cartoon-style stylization.
- Worked with the anime/realistic style presets and sampling settings to produce consistent cartoon and photorealistic outputs.
- _(Add any code or config you changed — files, features, fixes. If you only set up and used it, keep this to deployment, experimentation, and usage.)_

---

## 🏆 Credits & Attribution

- **Original project:** [Fooocus](https://github.com/lllyasviel/Fooocus) by **lllyasviel** (open source).
- **Customized base** (footer removal, preset launchers, Colab notebook): **Abhiram** — [abhi963007/Fooocus](https://github.com/abhi963007/Fooocus).
- The project starts from a mixture of the [Stable Diffusion WebUI](https://github.com/AUTOMATIC1111/stable-diffusion-webui) and [ComfyUI](https://github.com/comfyanonymous/ComfyUI) codebases.
- This repository is a fork I use and build on for AI image generation and cartoon-style stylization.

---

## 📄 License

This project follows the license of the upstream Fooocus project. See [LICENSE](LICENSE).

<div align="center">

### Create images and cartoon-style art — fully offline. 🎨

</div>
