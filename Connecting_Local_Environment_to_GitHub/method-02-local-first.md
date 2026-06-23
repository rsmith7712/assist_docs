# Method 2: Local First

## Best When You Already Have Existing Code

---

Start with a local folder — whether it already contains code or is newly created — and publish it to GitHub from within VS Code. This is the right approach when you have been working on a project locally and are now ready to put it under version control.

> **Part of a series.** See the [README](README.md) for all available methods.

---

## Prerequisites

- [Git](https://git-scm.com/downloads) is installed (`git --version` to verify)
- [VS Code](https://code.visualstudio.com/) is installed
- You have a [GitHub](https://github.com) account
- VS Code is authorized to connect to your GitHub account (you will be prompted on first use)

---

## Step 1 — Open Your Local Folder in VS Code

1. Open VS Code
2. Go to **File → Open Folder** and select the folder you want to track
   - If the folder does not exist yet, create it first in your file system, then open it

---

## Step 2 — Initialize a Git Repository

1. Open the Command Palette:
   - **Windows/Linux:** `Ctrl+Shift+P`
   - **macOS:** `Cmd+Shift+P`
2. Type `Git: Initialize Repository` and press `Enter`
3. Select the current folder when prompted

This creates a `.git` directory in your folder, making it a local Git repository. VS Code's Source Control panel will now show all untracked files.

---

## Step 3 — Stage and Commit Your Files

1. Click the **Source Control** icon in the left sidebar (or press `Ctrl+Shift+G`)
2. Hover over **Changes** and click the **+** icon to stage all files, or stage files individually
3. Enter a commit message in the text box at the top (e.g., `Initial commit`)
4. Click the checkmark icon or press `Ctrl+Enter` to commit

---

## Step 4 — Publish to GitHub

1. In the Source Control panel, click **Publish Branch**
   - If prompted, authorize VS Code to connect to GitHub
2. Choose **Publish to GitHub Public Repository** or **Private Repository**
3. Confirm the repository name (VS Code pre-fills it from your folder name)
4. Click **OK / Publish**

VS Code will create the repository on GitHub and push your initial commit. Your local folder is now linked to the remote repository.

---

## Common Issues

**"Publish Branch" button is not visible**
- Confirm the repository was initialized in Step 2 — look for a branch name in the VS Code status bar at the bottom
- If no branch is shown, re-run `Git: Initialize Repository` from the Command Palette

**VS Code does not show Git options**
- Confirm Git is installed: run `git --version` in a terminal
- Restart VS Code after installing Git

**Push is rejected after initial publish**
- Run `git pull` first to sync any remote changes, then push again

**Authentication fails**
- GitHub no longer accepts plain passwords over HTTPS
- Use a [Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) in place of your password

---

## Additional Resources

- [VS Code: Initialize a Repository](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_initialize-a-repository)
- [VS Code: Publishing to GitHub](https://code.visualstudio.com/docs/sourcecontrol/github#_publishing-repositories)
- [GitHub: Creating a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

---

*Contributions and corrections welcome. Open an issue or submit a pull request.*
