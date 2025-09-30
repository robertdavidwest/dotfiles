# dotfiles

My personal dotfiles managed with [chezmoi](https://www.chezmoi.io/).

## Setup on a new Mac

Run this single command to install everything:

```bash
sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply robertdavidwest/dotfiles
```

This will:
- Install chezmoi
- Clone this dotfiles repository
- Install Homebrew (if not already installed)
- Install all packages from the Brewfile (brew, node, python, neovim, etc.)
- Clone and set up my neovim configuration from [init.lua](https://github.com/robertdavidwest/init.lua)
- Apply all dotfiles (.zshrc, .gitconfig, .tmux.conf, etc.)

## What's included

- **Shell**: zsh configuration
- **Editor**: neovim (with custom config from separate repo)
- **Git**: gitconfig with common settings
- **Terminal**: tmux configuration
- **Package Management**: Brewfile with all homebrew packages and VSCode extensions
- **Tools**: fzf, ripgrep, lazygit, zoxide, and more

## Manual updates

After the initial setup, manage your dotfiles with:

```bash
# See what would change
chezmoi diff

# Apply changes
chezmoi apply

# Update from repo
chezmoi update

# Edit a file
chezmoi edit ~/.zshrc
```