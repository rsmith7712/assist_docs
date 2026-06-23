# Method 1: GitHub First

## Recommended for New Projects

---

Start on GitHub, then bring the repository down to your machine. This is the cleanest approach when starting from scratch because the repository is initialized in one place and then replicated locally — no merge conflicts, no manual initialization required.

> **Part of a series.** See the [README](README.md) for all available methods.

---

## Prerequisites

- [Git](https://git-scm.com/downloads) is installed (`git --version` to verify)
- [VS Code](https://code.visualstudio.com/) is installed
- You have a [GitHub](https://github.com) account
- You are authenticated with GitHub via HTTPS (username + personal access token) or SSH key

---

## Step 1 — Create the Repository on GitHub

1. Log in to [github.com](https://github.com)
2. Click the **+** icon in the upper-right corner and select **New repository**
3. Enter a repository name (lowercase, hyphens instead of spaces is conventional)
4. Optionally add a description
5. Set visibility to **Public** or **Private**
6. Check **Add a README file** — this initializes the repo with a commit, which is required before cloning
7. Click **Create repository**

---

## Step 2 — Copy the Repository URL

1. On the repository page, click the green **Code** button
2. Select the **HTTPS** tab (or **SSH** if you have a key configured)
3. Copy the URL shown — it will look like:
   ```
   https://github.com/your-username/your-repo-name.git
   ```

---

## Step 3 — Clone the Repository in VS Code

1. Open VS Code
2. Open the Command Palette:
   - **Windows/Linux:** `Ctrl+Shift+P`
   - **macOS:** `Cmd+Shift+P`
3. Type `Git: Clone` and press `Enter`
4. Paste the GitHub URL you copied and press `Enter`
5. Browse to a local folder where you want the project to live and select it
6. When VS Code prompts *"Would you like to open the cloned repository?"* — click **Open**

VS Code will clone the repository, check out the default branch, and open the project folder. The `.git` directory is created automatically, and VS Code's Source Control panel (the branch icon in the left sidebar) will reflect the repository state immediately.

You are ready to write code, commit, and push.

---

## Common Issues

**VS Code does not show Git options**
- Confirm Git is installed: run `git --version` in a terminal
- Restart VS Code after installing Git

**Push is rejected**
- Usually means the remote has commits your local copy does not have
- Run `git pull` first to sync, then push again

**Authentication fails on push**
- GitHub no longer accepts plain passwords over HTTPS
- Use a [Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) in place of your password, or configure SSH keys

---

## Additional Resources

- [GitHub Docs — Create a Repo](https://docs.github.com/en/get-started/quickstart/create-a-repo)
- [VS Code: Working with GitHub](https://code.visualstudio.com/docs/sourcecontrol/github)
- [GitHub: Creating a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

---

*Contributions and corrections welcome. Open an issue or submit a pull request.*
