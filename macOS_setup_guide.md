# MacOS Environment Setup: Xcode + Homebrew + Git + SSH key

This guide walks you through the complete setup process for a macOS development environment, including Homebrew package manager, Git version control, SSH keys, and GitHub integration.

## Prerequisites

- macOS system (Apple Silicon or Intel)
- Internet connection
- Open the terminal 
- Make sure you are at the /root (or at the desired PATH location)

---

## 1. Install Homebrew

Homebrew is a package manager for macOS. If you don't have Xcode installed, this command will download it automatically before installing Homebrew.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

## 2. Add Homebrew to PATH

### For Apple Silicon Macs (M1 and above):

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

### For Intel Mac Users (skip if Apple Silicon):

```bash
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile

eval "$(/usr/local/bin/brew shellenv)"
```

---

## 3. Verify Homebrew Installation

```bash
brew --version
```

---

## 4. Install Git

```bash
brew install git
```

---

## 5. Verify Git Installation

```bash
git --version
```

---

## 6. Configure Git

Replace the name and email with your own information.

```bash
git config --global user.name "your_github_username"

git config --global user.email "your_email@gmail.com"

git config --global init.defaultBranch main
```

---

## 7. Create SSH Directory

Create the `.ssh` directory with correct permissions (or verify it exists).

```bash
mkdir -p ~/.ssh

chmod 700 ~/.ssh
```

---

## 8. Generate SSH Key

Generate a new SSH key using the ed25519 algorithm. When prompted to write a file name or to put a password press `ENTER` to use the default.

```bash
ssh-keygen -t ed25519 -C "your_email@gmail.com"
```

---

## 9. Start SSH Agent

```bash
eval "$(ssh-agent -s)"
```

---

## 10. Add SSH Key to SSH Agent

For macOS systems using the `--apple-use-keychain` option:

```bash
ssh-add --apple-use-keychain ~/.ssh/id_ed25519 2>/dev/null || ssh-add ~/.ssh/id_ed25519
```

---

## 11. Copy Public Key to Clipboard

Display your public key and copy it to your clipboard. This will be used to authenticate with GitHub.

```bash
cat ~/.ssh/id_ed25519.pub
```

**Next steps:**
1. Copy the entire output from the command above
2. Go to [GitHub Settings > SSH and GPG keys](https://github.com/settings/keys)
3. Click "New SSH key"
4. Paste your public key and give it a descriptive title
5. Click "Add SSH key"

---

## 12. Test SSH Connection to GitHub

Verify that your SSH key is correctly configured for GitHub:

```bash
ssh -T git@github.com
```

You should see a message like: `Hi <username>! You've successfully authenticated...`

---

## Troubleshooting

- **Homebrew not found after installation:** Close and reopen your terminal, or run the commands from Step 2 again.
- **SSH key permissions error:** Run `chmod 600 ~/.ssh/id_ed25519` and `chmod 644 ~/.ssh/id_ed25519.pub`
- **SSH connection fails:** Verify your public key is added to GitHub settings and check your internet connection.

---

## Additional Resources

- [Homebrew Documentation](https://docs.brew.sh/)
- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub SSH Documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
