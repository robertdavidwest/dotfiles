# dotfiles

My personal dotfiles managed with [chezmoi](https://www.chezmoi.io/).

## Setup on a new Mac

First, install Xcode Command Line Tools (required for git and Homebrew):

```bash
xcode-select --install
```

Wait for the installation to complete, then run this single command to install everything:

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

**Note**: If the script encounters errors during package installation, you may need to manually apply the dotfiles:

```bash
chezmoi apply
```

### Setup SSH Keys for GitHub

Generate and add SSH keys to your GitHub account:

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Copy public key to clipboard
cat ~/.ssh/id_ed25519.pub | pbcopy
```

Then add the key to GitHub at https://github.com/settings/keys

Test the connection:
```bash
ssh -T git@github.com
```

### Complete Neovim Setup

The neovim config has been cloned to `~/.config/nvim`, but requires additional setup. Follow the instructions in the [init.lua README](https://github.com/robertdavidwest/init.lua) to install Packer and plugins.

If the `markdown-preview.nvim` plugin fails to install during `:PackerSync`, run this in neovim:
```vim
:call mkdp#util#install()
```

### Configure Warp Terminal Background

Set the terminal background image in Warp:
1. Open Warp settings (Cmd+,)
2. Navigate to Appearance → Background
3. Set background image path to: `~/.config/nvim/terminal_backgrounds/triforce_background.jp`

### Set up Homerow

Homerow preferences are synced via chezmoi, but you need to grant it accessibility permissions:
1. Open Homerow (it should be installed via Brewfile)
2. When prompted, grant Accessibility permissions in System Settings → Privacy & Security → Accessibility
3. Your keyboard shortcuts will be automatically configured

## What's included

- **Shell**: zsh configuration
- **Editor**: neovim (with custom config from separate repo)
- **Git**: gitconfig with common settings
- **Terminal**: tmux configuration
- **Package Management**: Brewfile with all homebrew packages and VSCode extensions
- **Tools**: fzf, ripgrep, lazygit, zoxide, and more

## Manual installations

After running the automated setup, install these manually:

- **[Magnet](https://apps.apple.com/us/app/magnet/id441258766)** - Window management (Mac App Store)

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

### Installing new packages after initial setup

If you add new packages to the Brewfile and have already run the initial setup on a machine, install them with:

```bash
brew bundle --file=~/.local/share/chezmoi/Brewfile
```
