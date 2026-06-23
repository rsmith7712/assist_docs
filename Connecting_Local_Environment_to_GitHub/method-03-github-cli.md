# Method 3: GitHub CLI (`gh`)

## Best for Terminal-Comfortable Developers

---

The [GitHub CLI](https://cli.github.com/) (`gh`) lets you create, clone, and manage GitHub repositories entirely from the terminal — no browser required after initial authentication. It works on Linux, macOS, and Windows, and integrates cleanly with VS Code's integrated terminal.

This method is particularly well-suited to developers who prefer keyboard-driven workflows, work frequently over SSH on remote machines, or want to script and automate repository setup.

> **Part of a series.** See the [README](README.md) for all available methods.

---

## Prerequisites

- [Git](https://git-scm.com/downloads) is installed (`git --version` to verify)
- You have a [GitHub](https://github.com) account

---

## Step 1 — Install the GitHub CLI

**Debian / Ubuntu:**
```bash
sudo apt update
sudo apt install gh
```

**Fedora / RHEL / CentOS:**
```bash
sudo dnf install gh
```

**Arch Linux:**
```bash
sudo pacman -S github-cli
```

**macOS (Homebrew):**
```bash
brew install gh
```

**Windows (winget):**
```bash
winget install --id GitHub.cli
```

Verify the installation:
```bash
gh --version
```

---

## Step 2 — Authenticate with GitHub

```bash
gh auth login
```

Follow the interactive prompts:
- Select **GitHub.com**
- Select **HTTPS** or **SSH** (SSH is recommended on Linux — see [Method 4](method-04-terminal-ssh-linux.md))
- Choose to authenticate via browser or paste a token
- If using a browser, a one-time code is displayed — open the URL, enter the code, and authorize

Confirm authentication status at any time:
```bash
gh auth status
```

---

## Step 3 — Create and Clone a New Repository in One Command

Navigate to the parent directory where you want the project folder created, then run:

```bash
gh repo create your-repo-name --public --clone --add-readme
```

| Flag | Purpose |
|---|---|
| `--public` | Creates a public repository (use `--private` for private) |
| `--clone` | Clones the new repo into a local folder immediately after creation |
| `--add-readme` | Initializes the repo with a README so it has a first commit |

This single command creates the repository on GitHub, initializes it with a README, and clones it to your current directory. You will have a fully linked local repository without touching a browser.

---

## Step 4 — Open in VS Code (Optional)

```bash
cd your-repo-name
code .
```

The `code .` command opens the current directory in VS Code. The Source Control panel will recognize the repository immediately.

---

## Publishing an Existing Local Repository via GitHub CLI

If you already have a local folder with code that is not yet on GitHub:

```bash
cd /path/to/your/project
git init
git add .
git commit -m "Initial commit"
gh repo create your-repo-name --public --source=. --remote=origin --push
```

| Flag | Purpose |
|---|---|
| `--source=.` | Points `gh` at the current directory as the source |
| `--remote=origin` | Sets the new GitHub repo as the `origin` remote |
| `--push` | Pushes the existing commits to GitHub immediately |

---

## Common Issues

**`gh: command not found`**
- The GitHub CLI is not installed — follow Step 1 above for your platform

**Authentication fails during `gh auth login`**
- If using a Personal Access Token, confirm it has the `repo` scope enabled
- Tokens are managed at [github.com/settings/tokens](https://github.com/settings/tokens)

**`code .` is not recognized**
- The VS Code `code` command is not in your PATH
- In VS Code, open the Command Palette and run **Shell Command: Install 'code' command in PATH**, then restart your terminal

**Push is rejected**
- Usually means the remote has commits your local copy does not have
- Run `git pull` first to sync, then push again

---

## Additional Resources

- [GitHub CLI Home](https://cli.github.com/)
- [GitHub CLI Manual](https://cli.github.com/manual/)
- [GitHub CLI: `gh repo create`](https://cli.github.com/manual/gh_repo_create)
- [GitHub: Creating a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

---

*Contributions and corrections welcome. Open an issue or submit a pull request.*
