# MacOS Environment setup guide: Xcode + Homebrew + Git + SSH key

Covers the process of installing Homebrew, Git, Xcode CLT, creating SSH keys, and wiring GitHub.

## What this repo contains
- `macOS_setup_guide.md`: step by step instructions with command structures 

## Quick start
- Install Homebrew using the official installer script.
- Add Homebrew to your shell `PATH` (Apple Silicon uses `/opt/homebrew`, Intel uses `/usr/local`).
- Install Git via Homebrew and configure your global username, email, and default branch.
- Generate an SSH key pair and add it to the macOS agent.
- Upload the public key to GitHub and verify with `ssh -T git@github.com`.

## Requirements
- macOS with internet access.
- Terminal access (tested with zsh).

## Status
More info, tooling recommendations, and automation scripts coming soon.
