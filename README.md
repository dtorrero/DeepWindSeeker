# 🌟 Beginner's Guide: Build Your AI Coding Assistant with VSCodium

This guide will help you set up a powerful AI coding assistant right inside your editor. We'll use **VSCodium** (a privacy-focused version of VS Code) and connect it to **DeepSeek AI**.

---

## 📋 What You'll Need Before Starting

**Cline includes some free to use models, and some limited models (when you create your cline account)**   

In this guide we will configure it to use a DeepSeek API. 

1.  **A DeepSeek Account and API Key**
    *   Go to [platform.deepseek.com](https://platform.deepseek.com)
    *   Sign up (it's free to start)
    *   Find your **API Key** in your account settings. It will look like `sk-` followed by a long string of letters and numbers.
    *   **Important:** You get a small free credit (around €1). This is plenty for testing!

2.  **A Computer** running Linux (like Ubuntu, Mint, Manjaro, or Arch).

---

## 🚀 Part 1: Installing the Editor (VSCodium)

First, we'll install the editor where everything will run.

### **Easy Method: Install with a Click (Recommended for Beginners)**
**Always try with your package manager if possible**

If not, this is the simplest way, just like installing any other program.

1.  **Go to the VSCodium website:** [vscodium.com](https://vscodium.com)
2.  Click on **"Download"**.
3.  Choose the correct package for your system:
    *   If you use **Ubuntu, Linux Mint, or Debian**, download the **`.deb`** file.
    *   If you use **Manjaro, EndeavourOS, or Arch**, download the **`.rpm`** file (or use the AUR method below).
4.  Open your **Downloads** folder, find the file (e.g., `codium_x.x.x_amd64.deb`), and double-click it.
5.  Your system's software installer will open. Click **"Install"** and enter your password when asked.
6.  Once installed, search for and open **"VSCodium"** from your application menu.

**Troubleshooting:** If the double-click doesn't work, you can install from the terminal:
```bash
# For .deb files (Ubuntu/Mint/Debian)
sudo apt install ~/Downloads/codium_*.deb

# For .rpm files (Fedora/openSUSE)
sudo dnf install ~/Downloads/codium-*.rpm
```

### **Alternative Method: Using the Terminal (For Manjaro/Arch Users)**
If you're comfortable with the terminal, this is often easier on Arch-based systems.

1.  Open your terminal.
2.  Use `yay` (or your favorite AUR helper) to install VSCodium:
    ```bash
    yay -S vscodium-bin
    ```
3.  Type `y` and press Enter to confirm. The installation will run automatically.
4.  When it's done, you can launch VSCodium by typing `codium` in the terminal or finding it in your app menu.

---

## 🔌 Part 2: Installing the AI Extension (Cline)

Now, we'll add the "brain" – the Cline extension that connects VSCodium to DeepSeek AI.

1.  **Open VSCodium**.
2.  Look at the left sidebar and click on the **Extensions icon** (it looks like four squares, or press `Ctrl+Shift+X`).
    ![Extensions Icon](https://code.visualstudio.com/assets/docs/getstarted/tips-and-tricks/Extensions_view_icon.png)
3.  In the search bar at the top, type **`Claude Dev`** and press Enter.
    *   *Note: The extension is called "Claude Dev" but works perfectly with DeepSeek.*
4.  The first result should be **"Claude Dev - Cline"** by Saoud Rizwan. Click the **"Install"** button on its card.
5.  Wait for the installation to finish. You might need to **reload VSCodium** when prompted.

**What to do if you can't find it?**
Sometimes the extension isn't in VSCodium's default store. Don't worry! Just:
1.  Visit this link in your web browser: [Cline on Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev)
2.  Click the large green **"Download Extension"** button.
3.  Go back to VSCodium's Extensions view.
4.  Click the **`...`** (more actions) menu at the top and choose **"Install from VSIX..."**.
5.  Find the `.vsix` file you just downloaded (usually in your `Downloads` folder) and select it.

---

## ⚙️ Part 3: Connecting to DeepSeek AI (The Easy Way)

Let's tell Cline to use your DeepSeek API key. We'll do this through VSCodium's settings menu – no code editing needed!

1.  Open VSCodium's **Settings**:
    *   On Linux: Go to **File > Preferences > Settings**.
    *   Quick Keyboard Shortcut: Press **`Ctrl + ,`** (Control and comma).
2.  In the search bar at the top of the Settings tab, type **`cline`**.
3.  You'll see all of Cline's settings. We need to change four of them:

    **a) Set the Provider:**
    *   Find the setting called **`Cline > Provider`**.
    *   Click into the box and type **`openai`**.
    *   **Why `openai`?** DeepSeek's system is built to work exactly like OpenAI's, so tools like Cline can connect to it easily. This is correct!

    **b) Enter Your API Key:**
    *   Find **`Cline > Api Key`**.
    *   Paste the API key you copied from [platform.deepseek.com](https://platform.deepseek.com) (the one that starts with `sk-`).

    **c) Set the AI Model:**
    *   Find **`Cline > Model`**.
    *   Type **`deepseek-chat`**. (You can also try `deepseek-coder` later for more code-focused answers).

    **d) Point to DeepSeek's Servers:**
    *   Find **`Cline > Api Base Url`**.
    *   Make sure it says **`https://api.deepseek.com`**.

4.  **You're connected!** The settings save automatically. You can close the Settings tab.

---

## ✨ Part 4: Using Your New AI Assistant

Time to test it out! Your AI assistant is now built into VSCodium.

1.  **Open the Cline Chat Panel:**
    *   Look at the very left sidebar of VSCodium. You should see a new icon (a speech bubble).
    *   Click it! If you don't see it, press **`Ctrl+Shift+P`**, type **`Cline: Focus Chat`**, and press Enter.

2.  **Have Your First Conversation:**
    *   A panel will open on the right. Type a greeting like **"Hello!"** and press Enter.
    *   You should get a friendly reply from DeepSeek.

3.  **Make It Write Code:**
    *   Try asking it to create a file. Type: **"Create a Python file called hello.py that prints 'Hello World'"**.
    *   Cline will write the code and show you a preview.
    *   **To accept the change:** Press **`Ctrl+Enter`** on your keyboard (this is the shortcut since the "Accept" button can be buggy in VSCodium).

4.  **Ask It to Explain or Fix Code:**
    *   Open any code file.
    *   Select a piece of code with your mouse.
    *   Right-click on the selected code and look for a **"Cline"** menu option, like **"Ask Cline"** or **"Explain This"**.
    *   You can also just paste code directly into the chat and ask questions about it!

---

## 🛠️ Part 5: Tips & Troubleshooting

### **The "Accept" Button is Missing!**
This is a common visual bug. **Don't panic!** Just use the keyboard shortcut **`Ctrl+Enter`** whenever Cline shows you a code preview that needs approval.

### **To Make Changes Automatic (Advanced):**
If you don't want to press `Ctrl+Enter` every time, you can change a setting:
1.  Open Settings again (`Ctrl+,`).
2.  Search for **`cline.autoApplyChanges`**.
3.  Check the box. Now Cline will apply changes after a short pause without asking.

### **Saving Your API Key More Securely**
Instead of pasting your key directly into the settings, you can save it as a system variable:
1.  Open your terminal and type:
    ```bash
    echo 'export DEEPSEEK_API_KEY="sk-your-key-here"' >> ~/.bashrc
    source ~/.bashrc
    ```
    *(Replace `sk-your-key-here` with your actual key)*
2.  In the VSCodium setting for **`Cline > Api Key`**, simply type **`${DEEPSEEK_API_KEY}`**. It will use the key from your system.

### **It's Not Responding**
*   **Check your key:** Make sure the API key in the settings is correct.
*   **Check the model:** Ensure the model is `deepseek-chat`.
*   **Check the URL:** Ensure the base URL is `https://api.deepseek.com`.

---

## 🎉 Congratulations!

You've successfully built your own AI-powered development environment. You now have a coding assistant that can:
*   Write new code from descriptions.
*   Explain code you don't understand.
*   Find and fix bugs.
*   Answer programming questions.

Start by asking it to help with a small project or to explain a concept you're learning. Enjoy your new superpower!

**Remember:** You started with a small free credit. You can monitor your usage and add more funds anytime at [platform.deepseek.com](https://platform.deepseek.com).
