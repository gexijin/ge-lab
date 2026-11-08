---
layout: post
title: "Installing Claude Code on Windows Using WSL"
date: 2025-12-06 19:46:41 +0000
categories: ["AI"]
---

This beginner-friendly guide walks you through installing Claude Code on Windows using the Windows Subsystem for Linux (WSL). Although you can install Claude Code directly on Windows, it works better under Linux because it relies heavily on Bash commands as tools. With WSL, Claude Code runs in a Linux environment, while you keep using your preferred Windows editors and applications to view and edit files or test your code.

## Overview

1. Install WSL (Windows Subsystem for Linux)
2. Set up Ubuntu Linux
3. Install Node.js (optional)
4. Install Claude Code
5. Log in with your Claude account or API key
6. Start using Claude Code!

## What You'll Need

- A Windows 10 (version 2004 or higher) or Windows 11 computer
- An internet connection
- Administrator access on your computer
- A paid Claude subscription (Pro, Max, Team, or Enterprise) or API access, e.g., through Microsoft Foundry on Azure. The free Claude plan does not include Claude Code.

## Step 1: Check if Virtualization Is Enabled

WSL requires virtualization, so first verify that it is enabled on your computer.

1. **Right-click** the taskbar (the bar at the bottom of your screen).
2. Click **Task Manager**.
3. If Task Manager opens in a small window, click **More details** at the bottom.
4. Click the **Performance** tab.
5. Click **CPU** in the left sidebar.
6. In the bottom-right section of the window, find the line **Virtualization:** and check whether it says **Enabled**.

**If it says "Enabled":** Great! Continue to Step 2.

**If it says "Disabled":** Enable virtualization in your computer's BIOS settings:

1. Restart your computer.
2. During startup, press the BIOS key (usually **F2**, **F10**, **Del**, or **Esc**, depending on your computer's manufacturer).
3. Look for settings named "Virtualization Technology", "Intel VT-x", "AMD-V", or "SVM Mode".
4. Enable these settings.
5. Save and exit the BIOS (usually **F10**). Your computer will restart normally.

## Step 2: Open PowerShell as Administrator

1. Click the **Windows Start button**.
2. Type `PowerShell` in the search box.
3. In the search results, **right-click** **Windows PowerShell**.
4. Click **Run as administrator**.
5. When asked "Do you want to allow this app to make changes to your device?", click **Yes**.

A window will open—this is PowerShell running as administrator.

## Step 3: Install WSL

1. In the PowerShell window, type the following and press **Enter**:

   ```powershell
   wsl --install
   ```

2. Windows will download and install WSL. This may take 5–15 minutes, depending on your internet speed. You might see messages like "Installing: Windows Subsystem for Linux" and "Installing: Ubuntu".
3. When the installation is complete, restart your computer: click the **Windows Start button**, then the **Power icon**, then **Restart**.

**Why a restart is needed:** It lets Windows enable the WSL and Virtual Machine Platform features that were just installed. WSL won't work properly until you restart.

**What happens after the restart:** After you log back into Windows, an Ubuntu terminal window should appear automatically within 2–5 minutes to finish the setup. If it doesn't, open Ubuntu manually (see Step 4).

**Note:** If you get an error saying the command is not recognized, your Windows version might be too old. Make sure you have Windows 10 version 2004 or higher, or Windows 11, and run Windows Update to get the latest version.

## Step 4: Set Up Ubuntu (First Time Only)

**If the Ubuntu window did NOT open automatically:**

1. Click the **Windows Start button**.
2. Type `Ubuntu` in the search box.
3. Click **Ubuntu** (a circular orange icon). The Ubuntu terminal will open and continue the setup.

**Complete the first-time setup:**

1. Wait for the prompt `Enter new UNIX username:`.
2. Type a username using only lowercase letters and numbers, with no spaces (for example, `myname` or `john123`), and press **Enter**.
3. At `New password:`, type a password and press **Enter**. You won't see the characters as you type; this is normal.
4. At `Retype new password:`, type the same password again and press **Enter**.
5. Wait for the setup to complete. You'll see a message like `Installation successful!`

**Important:** Remember this username and password—you'll need them later.

## Step 5: Update Ubuntu

1. In the Ubuntu terminal, type the following and press **Enter**:

   ```bash
   sudo apt update
   ```

2. Type your password (the one you just created) and press **Enter**. Again, you won't see the characters as you type.
3. Wait for the update to complete (1–3 minutes).
4. Next, type the following and press **Enter**:

   ```bash
   sudo apt upgrade -y
   ```

5. Wait for all packages to upgrade (this may take 5–10 minutes).

## Step 6: Install Node.js (Optional)

The native Claude Code installer in Step 7 does not need Node.js, so you can skip this step. Node.js is still useful for many coding projects, and it is required only if you prefer to install Claude Code with npm (which needs Node.js 22 or later).

1. Download and run the nvm (Node Version Manager) installer:

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
   ```

2. Load nvm:

   ```bash
   \. "$HOME/.nvm/nvm.sh"
   ```

3. Install Node.js version 24 (this takes 2–5 minutes):

   ```bash
   nvm install 24
   ```

4. Verify the installation:

   ```bash
   node --version
   ```

   You should see something like `v24.x.x` (the exact numbers may vary).

## Step 7: Install Claude Code

1. In the Ubuntu terminal, type:

   ```bash
   curl -fsSL https://claude.ai/install.sh | bash
   ```

2. Wait for Claude Code to install (2–5 minutes). The installer shows little progress while it downloads.
3. When the installation is complete, close and reopen the Ubuntu terminal, then verify by typing:

   ```bash
   claude --version
   ```

   You should see the version number of Claude Code. For a more detailed check, run `claude doctor`.

## Step 8: Log In

### Option A: Use Your Claude Subscription

1. In the Ubuntu terminal, type:

   ```bash
   claude
   ```

2. Claude Code tries to open a browser. If it can't, hold **Ctrl** and click the long URL to open it in a browser, or copy the URL and paste it into a browser.
3. Log in to your Claude.ai account (this may happen automatically if you're already logged in).
4. Click **Authorize**.
5. When a long code appears, click **Copy Code**.
6. Go back to the terminal window and paste the code: **right-click** and select **Paste** (or press **Ctrl+Shift+V**).
7. Press **Enter**. You should see a success message.
8. Follow the instructions to complete the setup.

### Option B: Use Claude via Microsoft Foundry (Azure)

In the terminal window, paste this code to define the environment variables, then press **Enter**:

```bash
# Enable Microsoft Foundry integration
export CLAUDE_CODE_USE_FOUNDRY=1
# Azure resource name
export ANTHROPIC_FOUNDRY_RESOURCE=XXXXX-eastus2
# Set models to your resource's deployment names
export ANTHROPIC_DEFAULT_OPUS_MODEL=claude-opus-4-5
export ANTHROPIC_DEFAULT_SONNET_MODEL=claude-sonnet-4-5
export ANTHROPIC_FOUNDRY_API_KEY=your_api_key
```

Replace `XXXXX-eastus2` with your Foundry resource name (just the name, not the entire URL), and replace `your_api_key` with your complete API key from the Azure portal. You can now use Claude Code with your Azure-deployed Claude models.

**Note:** These variables last only for the current terminal session. To keep them, add the same lines to the end of your `~/.bashrc` file.

## Step 9: Start Using Claude Code

You're all set!

1. In the Ubuntu terminal, type `claude` and press **Enter**.
2. You can now chat with Claude! To check that it works, ask a general question such as "Explain quantum computing."

## Step 10: Navigate to Your Project

1. Your Windows drives are available under `/mnt`. To open a project in your Windows folders, type:

   ```bash
   cd /mnt/c/Users/Username/Documents/YourProject
   ```

   Replace `Username` with your Windows username and `YourProject` with your project folder.

2. Start Claude:

   ```bash
   claude
   ```

3. Start by asking Claude to explain the codebase to you.
4. Ask Claude to make changes.
5. Test your code in your preferred IDE.

## How to Open the Ubuntu Terminal Again

1. Click the **Windows Start button**.
2. Type `Ubuntu` in the search box.
3. Click **Ubuntu** (a circular orange icon).

## Troubleshooting

### "Please enable the Virtual Machine Platform Windows feature and ensure virtualization is enabled in the BIOS"

This error means virtualization is not enabled:

1. Go back to Step 1 and check in Task Manager whether virtualization is enabled.
2. If it is disabled, enable it in your computer's BIOS (see Step 1).
3. Restart your computer and run `wsl --install` again.

### `wsl --install` doesn't work

- Make sure you're running PowerShell as Administrator.
- Make sure you have Windows 10 version 2004+ or Windows 11.
- Try running `wsl --update` first, then `wsl --install` again.

### Ubuntu window doesn't open after restart

Open it manually: click **Start**, type `Ubuntu`, and click the Ubuntu app.

### "sudo: apt: command not found"

Your WSL installation might be broken. In PowerShell (as Administrator), run `wsl --unregister Ubuntu`, then run `wsl --install` again. Note that unregistering deletes everything stored inside that Ubuntu installation.

### Node.js installation fails

- Make sure you ran `sudo apt update` first.
- Try the installation command again.

### "claude: command not found"

- Make sure the installation completed successfully.
- Close and reopen the Ubuntu terminal.
- The installer puts `claude` in `~/.local/bin`. If that folder isn't on your PATH, add it:

  ```bash
  echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
  source ~/.bashrc
  ```

- Try running the installation command again: `curl -fsSL https://claude.ai/install.sh | bash`

## Need Help?

- For WSL issues: [Microsoft WSL Documentation](https://learn.microsoft.com/en-us/windows/wsl/)
- For Claude Code installation: [Claude Code setup documentation](https://code.claude.com/docs/en/setup)
- For Claude Code issues: [Claude Code GitHub](https://github.com/anthropics/claude-code)
