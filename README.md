## **README.md - Guide to a Windsurf-like IDE with VSCodium and DeepSeek**

# AI-Powered Development Environment with VSCodium and DeepSeek

This guide walks you through setting up a privacy-focused, AI-powered Integrated Development Environment (IDE) using **VSCodium** and **DeepSeek**. Inspired by tools like Windsurf, this setup integrates a multi-agent AI coding assistant directly into your editor without telemetry.

---

## 🎯 What You'll Build

A VSCodium-based IDE with the **Continue** extension, powered by the **DeepSeek** large language model. This setup gives you:
*   A powerful, chat-based AI assistant in your sidebar.
*   Specialized "agents" for code review, debugging, and testing via slash commands.
*   Full codebase awareness and inline code completion.
*   A private, open-source alternative to cloud-based AI coding tools.

## 📋 Prerequisites

Before you begin, ensure you have:
*   A **DeepSeek API Key** from [platform.deepseek.com](https://platform.deepseek.com).
*   **Git** installed.
*   **Node.js 16+** (required for some extensions).

---

## 🚀 Step 1: Install VSCodium

VSCodium is a community-driven, telemetry-free distribution of VS Code. Choose the installation method for your distribution.

### For Debian-based Systems (Debian, Ubuntu, Mint)
Add the official repository and install:
```bash
# Install prerequisites
sudo apt update && sudo apt install curl gpg -y

# Import the repository GPG key
curl -fsSL https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg | sudo gpg --dearmor -o /usr/share/keyrings/vscodium-archive-keyring.gpg

# Add the repository (for Debian 13 / Ubuntu 24.04+)
echo -e 'Types: deb\nURIs: https://download.vscodium.com/debs\nSuites: vscodium\nComponents: main\nArchitectures: amd64 arm64\nSigned-by: /usr/share/keyrings/vscodium-archive-keyring.gpg' | sudo tee /etc/apt/sources.list.d/vscodium.sources

# Update and install VSCodium
sudo apt update && sudo apt install codium -y
```

### For Arch-based Systems (Arch, Manjaro)
Install from the AUR using your preferred helper:
```bash
# Using yay
yay -S vscodium-bin

# Using aura
sudo aura -A vscodium-bin
```

---

## 🧩 Step 2: Install the Continue Extension

The Continue extension acts as the interface for the AI assistant within VSCodium.

1.  Open VSCodium.
2.  Go to the **Extensions** view (`Ctrl+Shift+X`).
3.  Search for and install the extension named **"Continue"** by **Continue.dev**.

---

## 🔑 Step 3: Configure Continue with DeepSeek

The core of the setup is a YAML configuration file that tells Continue to use your DeepSeek API key and defines your AI agents.

1.  In VSCodium, open the command palette (`Ctrl+Shift+P`).
2.  Type `Continue: Open Config` and run it. This creates/opens `~/.continue/config.yaml`.
3.  Replace the file's contents with the configuration below. **Remember to paste your actual DeepSeek API key** where indicated.

```yaml
name: Windsurf-like AI Assistant
version: 1.0.0
schema: v1

models:
  - name: DeepSeek Coder
    provider: openai
    model: deepseek-coder
    apiKey: "sk-your-actual-deepseek-api-key-here" # REPLACE THIS
    apiBase: https://api.deepseek.com

contextProviders:
  - name: diff
  - name: github
  - name: terminal
  - name: codebase

slashCommands:
  - name: review
    description: "Code review agent - analyzes for bugs and improvements"
    prompt: |
      As a Code Review Agent, analyze this code:
      **Critical Issues**: Security vulnerabilities, crash risks.
      **Improvements**: Performance, clarity, best practices.
      Code: {{input}}

  - name: debug
    description: "Debugging agent - finds and fixes errors"
    prompt: |
      As a Debugging Agent:
      1. **Error Analysis**: {{input}}
      2. **Root Cause**:
      3. **Fix**:
      4. **Prevention**:

  - name: explain
    description: "Explanation agent - breaks down complex code"
    prompt: |
      As an Explanation Agent:
      1. **Purpose**: What this code does
      2. **Key Components**: Main functions/classes
      3. **Flow**: How data moves through
      Code: {{input}}

systemMessage: |
  You are an expert AI coding assistant in VSCodium.
  Provide clear, actionable responses with properly formatted code.
```

4.  Save the file. Continue will automatically reload the new configuration.

---

## ✅ Step 4: Test Your Setup

1.  **Restart VSCodium** to ensure all changes are loaded.
2.  Click the **Continue icon** (blue paper airplane) or just the "Continue" button in the activity bar to open the chat sidebar.
3.  Type a greeting like "Hello" or ask a simple coding question to test the connection to DeepSeek.
4.  Try the slash commands:
    *   Select some code in the editor.
    *   Type `/review` in the Continue chat and press Enter to see the review agent in action.

---

## ⚙️ (Optional) Advanced Customization

### Move the Continue Sidebar
By default, the sidebar is on the left. To move it to the right side:
1.  Click and hold the **Continue icon** in the activity bar.
2.  Drag it to the right side of the window and release.

### Use Environment Variables
For better security, store your API key as an environment variable.
1.  Add this line to your shell profile (`~/.bashrc` or `~/.zshrc`):
    ```bash
    export DEEPSEEK_API_KEY="sk-your-key-here"
    ```
2.  In your `config.yaml`, reference it like this:
    ```yaml
    apiKey: "${DEEPSEEK_API_KEY}"
    ```

### Cost Management
A small initial credit (e.g., €1.23) is sufficient for extensive testing, as DeepSeek's API is very affordable. Monitor your usage on the [DeepSeek platform dashboard](https://platform.deepseek.com).

---

## 🤝 Contributing & Issues

If you encounter issues:
*   Ensure your `config.yaml` file has correct **YAML syntax** (no tabs, proper indentation).
*   Verify your **API key is correct and active**.
*   Check that the Continue extension is the latest version.

For deeper troubleshooting, visit the [Continue documentation](https://docs.continue.dev).

---

## 📄 License
This guide is provided under the MIT License. VSCodium is licensed under MIT.

I hope this guide helps others build their own powerful, private AI development environment. 

DTM

<img width="1918" height="1034" alt="image" src="https://github.com/user-attachments/assets/d96f7f93-fe65-4696-94fa-4ca402c734ff" />

