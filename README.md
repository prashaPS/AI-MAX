# AI-MAX 🎙️⚡

**The Ultimate Offline AI Speech-to-Text & Voice Automation Engine.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-brightgreen.svg)]()
[![Built With](https://img.shields.io/badge/Stack-Rust%20%2B%20Tauri%20%2B%20TypeScript-orange.svg)]()
[![Privacy](https://img.shields.io/badge/Privacy-100%25%20Offline-blueviolet.svg)]()

> **Created & maintained by [prashaPS](https://github.com/prashaPS)**  
> *Transform your voice into text in any app, completely offline, with blazing speed and zero cloud dependencies.*

---

## 🌟 Why AI-MAX?

In a world where voice data is routinely uploaded to third-party servers, **AI-MAX** was created to bring voice-to-text power back into the user's hands.

- 🔒 **100% Private & Offline**: Audio processing and transcription happen entirely locally on your CPU or GPU. Nothing is sent to the cloud.
- ⚡ **Instant Global Dictation**: Press a shortcut, speak naturally, and watch your words typed directly into your active window—VS Code, Word, Chrome, Terminal, or Slack.
- 🎯 **State-of-the-Art Accuracy**: Powered by Whisper and Parakeet V3 neural network models with Voice Activity Detection (Silero VAD) to eliminate dead air.
- 🛠️ **Fully Hackable & Extensible**: Built on high-performance Rust and Tauri with a modern TypeScript frontend.

---

## 🚀 Key Features

### 🎙️ Effortless Voice Typing
- **Hold or Toggle Modes**: Hold a key to record and release to paste, or tap to toggle recording on and off.
- **Universal Input**: Injects transcribed text directly into any active desktop text field.
- **Smart Silence Trimming**: Silero VAD trims background noise and pauses before transcribing.

### 🧠 Cutting-Edge Local AI Models
- **Whisper Neural Models**: Supports Tiny, Base, Small, Medium, Turbo, and Large Whisper models.
- **Hardware Acceleration**: Automatic Vulkan GPU acceleration on supported hardware, plus multi-threaded CPU fallback.
- **Parakeet V3 Support**: High-speed, CPU-friendly alternative with automatic language identification.

### ✨ AI Post-Processing & Customization
- **LLM Cleanup**: Connect optional local or remote LLMs to fix grammar, remove filler words, summarize, or format text as code.
- **Custom Dictionary**: Add technical terms, names, and industry jargon to enhance recognition accuracy.
- **Multi-language Support**: Dictate in dozens of world languages with automatic script detection.

---

## 🏗️ Architecture

```
┌────────────────────────────────────────────────────────┐
│                   AI-MAX Desktop UI                    │
│           (React · TypeScript · Vite · Tailwind)       │
└───────────────────────────▲────────────────────────────┘
                            │ Tauri IPC Bridge
┌───────────────────────────▼────────────────────────────┐
│                   AI-MAX Core (Rust)                   │
│   ┌───────────────────────┬────────────────────────┐   │
│   │   Audio & Capture     │   Global Input Hook    │   │
│   │   (CPAL / Silero VAD) │   (Windows / Mac / X11)│   │
│   └───────────────────────┴────────────────────────┘   │
│   ┌────────────────────────────────────────────────┐   │
│   │          Local Inference Engine (C++)          │   │
│   │        Whisper.cpp / Vulkan Acceleration       │   │
│   └────────────────────────────────────────────────┘   │
└────────────────────────────────────────────────────────┘
```

---

## ⚡ Quick Start

### 1. Installation

#### Windows
You can install the desktop package via Windows Package Manager:
```powershell
winget install cjpais.Handy --accept-source-agreements --accept-package-agreements
```
Or download the latest release installer (`.exe` / `.msi`) from the [Releases](https://github.com/prashaPS/AI-MAX/releases) tab.

#### macOS
```bash
brew install --cask handy
```

#### Linux (Debian / Ubuntu)
```bash
sudo apt install ./Handy_*.deb
```

---

### 2. How to Use

1. **Launch AI-MAX**: Open the application from your launcher or tray.
2. **Set Your Shortcut**: Go to **Settings** and choose your preferred dictation hotkey (e.g. `Ctrl + Space` or `Alt + Shift`).
3. **Select Your Model**: Pick your desired model (Turbo or Parakeet recommended for optimal speed).
4. **Speak & Type**: Focus any application, press your shortcut, speak, and release to inject your text!

---

## 💻 Developer Setup & Building From Source

If you want to contribute, tweak models, or modify the interface:

### Prerequisites

| Tool | Minimum Version | Installation |
| :--- | :--- | :--- |
| **Rust** | Stable 1.80+ | [rustup.rs](https://rustup.rs) |
| **Bun** | 1.1+ | `winget install Oven-sh.Bun` or `curl -fsSL https://bun.sh/install \| bash` |
| **CMake** | 3.20+ | `winget install Kitware.CMake` |
| **Vulkan SDK** | Latest LunarG | [vulkan.lunarg.com](https://vulkan.lunarg.com/sdk/home) |
| **C++ Compiler** | MSVC 2022 / Clang / GCC | VS Build Tools with C++ Workload |

### Step-by-Step Build

1. **Clone the repository:**
   ```bash
   git clone https://github.com/prashaPS/AI-MAX.git
   cd AI-MAX
   ```

2. **Install frontend dependencies:**
   ```bash
   bun install
   ```

3. **Launch live development server:**
   ```bash
   bun run tauri dev
   ```

4. **Build production binaries:**
   ```bash
   bun run tauri build --no-bundle
   ```

---

## ⚙️ Configuration & CLI Controls

AI-MAX includes CLI integration to control the running instance from external scripts, Stream Decks, or window managers:

```bash
# Toggle recording on/off
ai-max --toggle-transcription

# Toggle recording with active LLM post-processing
ai-max --toggle-post-process

# Cancel active recording
ai-max --cancel

# Launch silently in the system tray
ai-max --start-hidden --no-tray
```

---

## 🛡️ Privacy Commitment

- **No Telemetry**: AI-MAX does not log your speech, monitor your keystrokes, or transmit usage analytics.
- **Local Storage**: Models and settings are saved locally on your device in your user directory.
- **Open Codebase**: Inspect every line of code to verify how your audio is processed.

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📜 Acknowledgements & License

This project is released under the **[MIT License](LICENSE)**.

AI-MAX is built upon and inspired by pioneering open-source projects including Whisper, transcribe.cpp, Silero VAD, and the Handy project. Special thanks to the open-source community for making offline local AI accessible to everyone.

---

<div align="center">
  <b>Built with ❤️ by <a href="https://github.com/prashaPS">prashaPS</a></b>
</div>
