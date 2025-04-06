# Dotfiles

This repository contains my personal dotfiles, managed using GNU Stow for easy deployment across different machines. This setup allows for consistent configurations and easy updates.

## Included Configurations

### Core Dotfiles
- **zsh**: Shell configuration files (`.zshrc`, `.zshenv`, etc.)
- **git**: Git configuration (`.gitconfig`)
- **iTerm2**: iTerm2 integration scripts

### Config Directory Files
- **starship**: Terminal prompt configuration
- **bat**: A `cat` clone with syntax highlighting
- **eza**: A modern replacement for `ls`
- **kitty**: Terminal emulator configuration
- **yazi**: File manager configuration

## Prerequisites

- [GNU Stow](https://www.gnu.org/software/stow/): A symlink farm manager used to manage dotfiles
  - Install with Homebrew on macOS: `brew install stow`
  - Install on Linux: `apt install stow` (Debian/Ubuntu) or `yum install stow` (Red Hat/Fedora)

## Installation

1. Clone this repository to your home directory or preferred location:
   ```bash
   git clone https://github.com/Yashasewi/dotfiles.git ~/dotfiles
   cd ~/dotfiles
   ```

2. Backup your existing dotfiles (optional but recommended):
   ```bash
   mkdir -p ~/.dotfiles_backup
   cp ~/.zshrc ~/.gitconfig ~/.config/starship.toml ~/.dotfiles_backup/ 2>/dev/null
   ```

3. Use Stow to create symlinks:
   ```bash
   # For core dotfiles (zsh, git, etc.)
   stow zsh git iterm2

   # For config directory files
   stow -t ~/.config config
   ```

## Directory Structure

```
dotfiles/
├── zsh/
│   └── .zshrc
├── git/
│   └── .gitconfig
├── iterm2/
│   └── [iterm2 integration files]
├── config/
│   ├── starship.toml
│   ├── bat/
│   ├── eza/
│   ├── kitty/
│   └── yazi/
└── .gitignore
```

## Usage

### Adding New Configurations

1. Create a new directory for the application
2. Place configuration files in the directory, maintaining the same structure as in your home directory
3. Run `stow [directory_name]` to create symlinks

### Updating Configurations

1. Make changes to the files in the dotfiles repository
2. The changes will automatically be reflected in your home directory due to the symlinks
3. Commit and push changes to keep your backup current:
   ```bash
   git add .
   git commit -m "Update [configuration] settings"
   git push
   ```

### Removing Configurations

To remove symlinks for a specific package:
```bash
stow -D [directory_name]
```

## Customization

Feel free to fork this repository and customize it to your needs. The modular structure makes it easy to add or remove configurations as needed.
