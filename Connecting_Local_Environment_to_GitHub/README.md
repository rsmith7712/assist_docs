# GitHub + VS Code: Connecting Your Local Environment to the Cloud

## A Practical Guide for Getting Started with Version Control

## The Question

A common question from new to source control and ready to take their work beyond a local machine:

> *"Do I create a new repo in GitHub then figure out how to sync it with my local IDE — or do I create the folder locally, attach it to my IDE, and then how does GitHub even see it?"*

Both approaches are valid. The right choice depends on where you are in your workflow. 
This series covers four methods — from GUI-driven VS Code workflows to terminal-only SSH setups on Linux. 
Each method is its own standalone document so you can go directly to what applies to your situation.

## Choose Your Method

| Method | Best For | Document |
|---|---|---|
| **Method 1 — GitHub First** | New projects, cleanest starting point | [method-01-github-first.md](method-01-github-first.md) |
| **Method 2 — Local First** | Existing code you want to put on GitHub | [method-02-local-first.md](method-02-local-first.md) |
| **Method 3 — GitHub CLI** | Terminal-comfortable developers, automation | [method-03-github-cli.md](method-03-github-cli.md) |
| **Method 4 — Terminal + SSH** | Linux systems, servers, headless environments | [method-04-terminal-ssh-linux.md](method-04-terminal-ssh-linux.md) |

## Common Concepts

All four methods use the same underlying Git mechanics. If you run into unfamiliar terminology, this table covers the most common terms:

| Term | What It Means |
|---|---|
| **Repository (repo)** | A project folder with version history tracked by Git |
| **Clone** | Downloading a copy of a remote repository to your local machine, with the link to the remote already configured |
| **Remote** | The version of the repository hosted on GitHub (or another server) |
| **origin** | The default name Git gives to the remote repository you cloned from or published to |
| **Commit** | A saved snapshot of your changes |
| **Push** | Sending your local commits up to the remote (GitHub) |
| **Pull** | Downloading changes from the remote to your local machine |
| **SSH key pair** | A public/private key used for authentication — the public key lives on GitHub, the private key stays on your machine |
| **SSH agent** | A background process that holds your decrypted private key in memory so you do not re-enter your passphrase on every operation |
| **upstream** | The branch on the remote that your local branch tracks — set with `git push -u origin main` |
| **`gh`** | The official GitHub CLI tool — creates, clones, and manages repos from the terminal without a browser |

## Day-to-Day Workflow After Setup

Regardless of which method you used to get started, the ongoing workflow is the same:

1. **Pull** before you start work — picks up any changes from collaborators or other machines
2. **Write code**
3. **Stage** the files you changed
4. **Commit** with a clear, descriptive message
5. **Push** to GitHub

```bash
git pull                     # Fetch and merge changes from origin
git add .                    # Stage all changes
git commit -m "Your message" # Commit staged changes
git push                     # Push to origin
```

In VS Code, all of these operations are accessible from the Source Control panel (left sidebar, branch icon) without touching the terminal.

## Additional Resources

**Git**
- [Git Documentation](https://git-scm.com/doc)
- [Pro Git Book (free)](https://git-scm.com/book/en/v2)

**GitHub**
- [GitHub Docs — Getting Started](https://docs.github.com/en/get-started)
- [GitHub: Generating an SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [GitHub: Creating a Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

**GitHub CLI**
- [GitHub CLI Home](https://cli.github.com/)
- [GitHub CLI Manual](https://cli.github.com/manual/)

**VS Code**
- [VS Code Source Control Documentation](https://code.visualstudio.com/docs/sourcecontrol/overview)
- [VS Code Git Integration Overview](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git)

---

*Contributions and corrections welcome. Open an issue or submit a pull request.*
