# Method 4: Terminal-Only with SSH Authentication

## Linux — No GUI Required

---

This method uses only Git and a terminal — no browser interface, no GUI, no VS Code required. It is the standard approach on Linux servers, headless environments, and for developers who want full control over their configuration. SSH key authentication replaces passwords entirely, meaning no tokens to rotate and no credentials to store in plaintext.

> **Part of a series.** See the [README](README.md) for all available methods.

---

## Prerequisites

- A Linux system with terminal access
- A [GitHub](https://github.com) account
- Sudo / root access for package installation

---

## Step 1 — Install Git

**Debian / Ubuntu:**
```bash
sudo apt update && sudo apt install git -y
```

**Fedora / RHEL / CentOS:**
```bash
sudo dnf install git -y
```

**Arch Linux:**
```bash
sudo pacman -S git
```

Verify:
```bash
git --version
```

---

## Step 2 — Configure Git Identity

These values are embedded in every commit you make. Set them once globally:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Set your preferred default branch name (GitHub uses `main` by default):
```bash
git config --global init.defaultBranch main
```

Confirm your configuration:
```bash
git config --global --list
```

---

## Step 3 — Generate an SSH Key

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

- When prompted for a file path, press `Enter` to accept the default (`~/.ssh/id_ed25519`)
- Set a passphrase when prompted (recommended), or press `Enter` to skip

> **Note:** If you are on an older system that does not support Ed25519, use `ssh-keygen -t rsa -b 4096 -C "your-email@example.com"` instead.

---

## Step 4 — Add the SSH Key to the SSH Agent

Start the agent and add your key:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

To persist the key across reboots without manually running `ssh-add` each time, add the following block to your `~/.bashrc` or `~/.bash_profile`:

```bash
# Start SSH agent and add key automatically
if [ -z "$SSH_AUTH_SOCK" ]; then
  eval "$(ssh-agent -s)"
  ssh-add ~/.ssh/id_ed25519
fi
```

Apply the change to your current session:
```bash
source ~/.bashrc
```

---

## Step 5 — Add the Public Key to GitHub

Copy your public key to the clipboard:

```bash
cat ~/.ssh/id_ed25519.pub
```

Then in GitHub:
1. Go to **Settings → SSH and GPG keys**
2. Click **New SSH key**
3. Give it a descriptive title (e.g., `dev-laptop-ubuntu`)
4. Paste the public key into the **Key** field
5. Click **Add SSH key**

Test the connection:
```bash
ssh -T git@github.com
```

A successful response looks like:
```
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## Step 6 — Create a Repository on GitHub

**Option A — GitHub CLI (no browser):**

If you have the GitHub CLI installed (see [Method 3](method-03-github-cli.md)):
```bash
gh repo create your-repo-name --public --clone --add-readme
```

**Option B — Web UI:**

1. Log in to [github.com](https://github.com)
2. Click **+** → **New repository**
3. Name the repo, check **Add a README file**, and click **Create repository**
4. On the repository page, click the green **Code** button
5. Select the **SSH** tab and copy the URL — it will look like:
   ```
   git@github.com:your-username/your-repo-name.git
   ```

---

## Step 7 — Clone Using SSH

```bash
git clone git@github.com:your-username/your-repo-name.git
cd your-repo-name
```

All subsequent `git push` and `git pull` operations will authenticate via SSH automatically — no tokens, no passwords.

---

## Starting From a Local Directory (Terminal-Only)

If you already have local code and want to push it to a new GitHub repository:

```bash
cd /path/to/your/project
git init
git add .
git commit -m "Initial commit"
git remote add origin git@github.com:your-username/your-repo-name.git
git branch -M main
git push -u origin main
```

The `-u` flag on the push sets `origin/main` as the upstream tracking branch, so future pushes and pulls can be run as simply `git push` and `git pull` without specifying the remote and branch each time.

---

## Common Issues

**`ssh -T git@github.com` returns "Permission denied (publickey)"**
- The public key was not added to GitHub, or the wrong key is being offered
- Run `cat ~/.ssh/id_ed25519.pub` and verify it matches what is in GitHub under **Settings → SSH and GPG keys**
- Run `ssh-add -l` to confirm the key is loaded in the agent — if the output is `The agent has no identities`, run `ssh-add ~/.ssh/id_ed25519`

**SSH agent is not running after reboot**
- Run `eval "$(ssh-agent -s)"` and `ssh-add ~/.ssh/id_ed25519` manually
- Or add the auto-start block from Step 4 to your `~/.bashrc`

**Push is rejected**
- Usually means the remote has commits your local copy does not have
- Run `git pull` first to sync, then push again

**Remote URL is HTTPS but you want to switch to SSH**
- Update the remote in place without re-cloning:
  ```bash
  git remote set-url origin git@github.com:your-username/your-repo-name.git
  ```

**Multiple SSH keys on the same machine**
- If you have keys for multiple GitHub accounts or services, configure `~/.ssh/config` to map hostnames to specific keys:
  ```
  Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519
  ```

---

## Additional Resources

- [Git Documentation](https://git-scm.com/doc)
- [Pro Git Book (free)](https://git-scm.com/book/en/v2)
- [GitHub: Generating an SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [GitHub: Adding an SSH Key to Your Account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- [GitHub: Testing Your SSH Connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

---

*Contributions and corrections welcome. Open an issue or submit a pull request.*
