---
layout: post
title: "Installing Claude Code on Mac for Beginners"
date: 2025-12-06 22:13:23 +0000
---

This guide walks you through installing Claude Code on your Mac. Each step includes detailed instructions for beginners.

## Overview

1. Open Terminal
2. Install Claude Code with the official installer
3. Log in with your Claude account or API key
4. Start using Claude Code!

Installing Node.js is optional; it's covered at the end of this guide, along with the npm install method.

## What You'll Need

- A Mac running macOS 13 (Ventura) or newer
- An internet connection
- A paid Claude subscription (Pro, Max, Team, or Enterprise) or API access, e.g., through Microsoft Foundry on Azure. The free Claude plan does not include Claude Code.
- Administrator access on your computer (only needed if you install Node.js)

## Step 1: Open Terminal

1. Press **Command (⌘) + Space** on your keyboard.
2. Type `Terminal` in the search box.
3. Click **Terminal** (a black square icon).
4. A window with a white or black background and text will open—this is Terminal.

**Tip:** Keep Terminal open for the next steps.

## Step 2: Install Claude Code

1. In Terminal, type the following and press **Enter**:

   ```bash
   curl -fsSL https://claude.ai/install.sh | bash
   ```

2. Wait for Claude Code to install (2–5 minutes). The installer shows little progress while it downloads. No password or `sudo` is needed.
3. When the installation is complete, close Terminal completely (**Command (⌘) + Q**) and open it again.
4. Verify the installation by typing:

   ```bash
   claude --version
   ```

5. Press **Enter**. You should see the version number of Claude Code. For a more detailed check, run `claude doctor`.

Prefer Homebrew? You can instead run `brew install --cask claude-code`. Note that Homebrew installations don't update automatically; run `brew upgrade claude-code` to update.

## Step 3: Log In

### Option A: Use Your Claude Subscription

1. In Terminal, type:

   ```bash
   claude
   ```

2. Press **Enter**.
3. Claude Code tries to open a browser. If it can't, hold **Command (⌘)** and click the long URL to open it in a browser, or copy the URL and paste it into your browser.
4. Log in to your Claude.ai account (this may happen automatically if you're already logged in).
5. Click **Authorize**.
6. When a long code appears, click **Copy Code**.
7. Go back to the Terminal window and paste the code: **right-click** and select **Paste** (or press **Command (⌘) + V**).
8. Press **Enter**. You should see a success message.
9. Follow the instructions to complete the setup.

### Option B: Use Claude via Microsoft Foundry (Azure)

In the Terminal window, paste this code to define the environment variables, then press **Enter**:

```bash
# Enable Microsoft Foundry integration
export CLAUDE_CODE_USE_FOUNDRY=1
# Azure resource name
export ANTHROPIC_FOUNDRY_RESOURCE=xxxx-eastus2
# Set models to your resource's deployment names
export ANTHROPIC_DEFAULT_OPUS_MODEL=claude-opus-4-5
export ANTHROPIC_DEFAULT_SONNET_MODEL=claude-sonnet-4-5
export ANTHROPIC_FOUNDRY_API_KEY=your_api_key
```

Replace `xxxx-eastus2` with your Foundry resource name (just the name, not the entire base URL), and replace `your_api_key` with your complete API key from the Azure portal. You can now use Claude Code with your Azure-deployed Claude models.

**Note:** These variables last only for the current Terminal session. To keep them, add the same lines to the end of your `~/.zshrc` file.

## Step 4: Start Using Claude Code

You're all set!

1. In Terminal, type `claude` and press **Enter**.
2. You can now chat with Claude! To check that it works, ask a general question such as "Explain quantum computing."

## Step 5: Navigate to Your Project

1. To work on a project in your Mac folders, navigate to it:

   ```bash
   cd ~/Documents/YourProject
   ```

   Replace `YourProject` with your project folder's name.

2. Start Claude:

   ```bash
   claude
   ```

3. Start by asking Claude to explain the codebase to you.
4. Ask Claude to make changes.
5. Test your code in your preferred IDE.

## How to Open Terminal Again

1. Press **Command (⌘) + Space** (or open Finder and go to **Applications** > **Utilities**).
2. Type `Terminal`.
3. Click **Terminal**.

## Optional: Install Node.js

Claude Code itself doesn't need Node.js when installed with the official installer above. You only need Node.js for your own JavaScript projects or if you prefer to install Claude Code with npm, which requires Node.js 22 or later.

### Download Node.js

1. Open your web browser (Safari, Chrome, Firefox, etc.) and go to [https://nodejs.org/](https://nodejs.org/).
2. Click the green **Get Node.js** button.
3. Click the green **macOS Installer (.pkg)** button in the middle of the screen.
4. A file named something like `node-v24.x.x.pkg` will download to your Downloads folder (usually within 30–60 seconds).

### Install Node.js

1. Open **Finder** (the blue smiling face icon in your Dock).
2. Click **Downloads** in the left sidebar.
3. Double-click the file you just downloaded (`node-v24.x.x.pkg`).
4. When the installer window appears, click **Continue**.
5. Click **Continue** again on the License screen, then click **Agree**.
6. Click **Install**.
7. Enter your Mac password (the one you use to log in) and click **Install Software**.
8. Wait for the installation to complete (1–2 minutes).
9. Click **Close** when you see "The installation was successful". You can move the installer to the Trash if asked.

### Verify Node.js

1. In Terminal, type the following and press **Enter**:

   ```bash
   node --version
   ```

2. You should see something like `v24.x.x` (the exact numbers may vary). If so, Node.js is installed correctly.

**If you see "command not found":** Quit Terminal completely (**Command (⌘) + Q**), open it again, and retry the command.

### Alternative: Install Claude Code with npm

If you'd rather use npm than the official installer, run:

```bash
npm install -g @anthropic-ai/claude-code
```

Don't use `sudo` with this command: Anthropic advises against `sudo npm install -g` because it causes permission problems and prevents automatic updates. If npm reports permission errors, use the official installer in Step 2 instead.

## Troubleshooting

### Node.js installer won't open

- Make sure you downloaded the `.pkg` file from nodejs.org.
- Try right-clicking the file and selecting **Open** instead of double-clicking.
- Go to **System Settings** > **Privacy & Security** and click **Open Anyway**.

### "node: command not found" after installation

- Quit Terminal completely (**Command (⌘) + Q**), open it again, and retry `node --version`.
- If it still doesn't work, restart your Mac and try again.

### npm installation fails with permission errors

- Don't retry with `sudo`. Install Claude Code with the official installer instead:

  ```bash
  curl -fsSL https://claude.ai/install.sh | bash
  ```

### "claude: command not found"

- Make sure the installation completed successfully.
- Quit and reopen Terminal.
- The installer puts `claude` in `~/.local/bin`. If that folder isn't on your PATH, add it:

  ```bash
  echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
  source ~/.zshrc
  ```

- Run `claude doctor` to diagnose the installation, or run the install command again.

### "Cannot find module" errors (npm installs)

- Make sure Node.js is properly installed: `node --version`
- Reinstall Claude Code: `npm uninstall -g @anthropic-ai/claude-code`, then `npm install -g @anthropic-ai/claude-code`

## Tips for Mac Users

### Finding Project Paths

To find the path to a folder:

1. Open Finder.
2. Navigate to your project folder.
3. Drag and drop the folder into Terminal—the full path will appear!

### Keyboard Shortcuts

- **Command (⌘) + T**: Open a new Terminal tab
- **Command (⌘) + N**: Open a new Terminal window
- **Command (⌘) + K**: Clear the Terminal screen
- **Control + C**: Stop a running command

### Using Different Terminal Apps

You can also use other terminal apps, such as:

- iTerm2 (popular alternative with more features)
- Warp (modern terminal with AI features)
- Hyper (cross-platform terminal)

Claude Code works with all of them!

## Need Help?

- For Claude Code installation: [Claude Code setup documentation](https://code.claude.com/docs/en/setup)
- For Claude Code issues: [Claude Code GitHub](https://github.com/anthropics/claude-code)
- For Node.js download: [Node.js Official Website](https://nodejs.org/)
- For Node.js issues: [Node.js Documentation](https://nodejs.org/docs/)
- For npm issues: [npm Documentation](https://docs.npmjs.com/)
