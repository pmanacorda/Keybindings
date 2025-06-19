# Keyboard Shortcuts & Commands Reference

## Chrome

| Shortcut | Action |
|----------|---------|
| `/` | Focus Search |
| `Ctrl+L` | Highlight URL |
| `Ctrl+T` | New Tab |
| `Ctrl+W` | Close Tab |
| `Ctrl+Tab` / `Ctrl+Shift+Tab` | Next/Previous Tab |
| `Ctrl+1-8` | Jump to Tab by Number |
| `Ctrl+R` | Refresh Page |
| `Ctrl+Shift+R` | Hard Refresh |
| `Ctrl+D` | Bookmark Page |
| `F5` | Refresh |
| `F11` | Full Screen |
| `F12` | Developer Tools |

## Windows

| Shortcut | Action |
|----------|---------|
| `Win` | Search Files |
| `Win+R` | Run Dialog |
| `Win+X` | Power User Menu |
| `Win+E` | File Explorer |
| `Win+L` | Lock Screen |
| `Win+D` | Show Desktop |
| `Win+M` | Minimize All Windows |
| `Win+V` | Clipboard History |
| `Win+H` | Voice Typing |
| `Alt+Tab` / `Ctrl+Alt+Tab` | Next/Previous Window |
| `Win+Tab` | Task View |
| `Win+Ctrl+Left/Right` | Next/Previous Desktop |
| `Win+Ctrl+D` | Create New Desktop |
| `Win+Ctrl+F4` | Close Current Desktop |
| `Win+Up/Down/Left/Right` | Snap Window |
| `Alt+D` | Show Desktop |
| `Alt+F4` | Close Application |
| `Ctrl+Shift+Esc` | Task Manager |

## Terminal

| Shortcut | Action |
|----------|---------|
| `Ctrl+C` | Interrupt/Cancel Command |
| `Ctrl+L` | Clear Screen |
| `Ctrl+A` | Move to Beginning of Line |
| `Ctrl+E` | Move to End of Line |
| `Up Arrow` | Previous Command |
| `Down Arrow` | Next Command |
| `Alt+Enter` | Full Screen |
| `Ctrl+Shift+T` | New Tab |
| `Ctrl+Shift+W` | Close Tab |
| `Ctrl+Shift+Space` | Open New Tab Options |
| `Ctrl+Tab` | Switch Tabs |

### Terminal Commands

| Command | Description |
|---------|-------------|
| `explorer .` | Launch File Explorer |
| `code .` | Launch VS Code |
| `ls -la` | List all files with details |
| `cd ..` | Go to previous directory |
| `mkdir -p path/to/dir` | Create nested directories |
| `cp -r source dest` | Copy directory recursively |
| `mv source dest` | Move/rename file |
| `rm -rf directory` | Remove directory and contents |
| `find . -name "*.txt"` | Find files by pattern |
| `grep -r "pattern" .` | Search text in files |
| `ps aux` | Find running processes |
| `kill -9 PID` | Force kill process |
| `top` / `htop` | System monitor |
| `history` | Command history |
| `!!` | Repeat last command |
```bash
alias ll='eza -la --git --group --time-style=long-iso --icons'
alias tree='eza --tree --level=2'
```

## Bash

```bash
# Exit on error, undefined variables, and pipe failures
set -eou pipefail

# Variable assignment and command substitution
variable=$(expression)
$(command)

# Error checking
if [ "$?" -ne 0 ]; then
  # Handle error
fi

# Check if variable is empty
if [ -z "$VAR" ]; then
  # Variable is empty
fi

# Get input params
while getopts a:b:c option
do
    case "${option}"
        in
            a) AppName=${OPTARG};;
            b) OtherVar=${OPTARG};;
            c) AnotherVar=${OPTARG};;
            *) echo "Invalid option: -$OPTARG" >&2 ;;
    esac
done

output > json (Redirection)
output >> json (Appending)
```

## Git

### Custom Git Functions

```bash
alias gs="git status"
alias gt="git log --all --graph --decorate --oneline --simplify-by-decoration"
alias gl="git log --oneline"
alias gnuke="git reset --hard && git clean -dfx"

# Commit with message
gcm() { git commit -m "$*" }

# Find branches
gf() {
    if [ -z "$1" ]; then echo "Usage: gf <search_term>"; git branch -a; return 1; fi
    git branch -a | grep -i "$1"
}

# Create new branch and push
gnb() {
    if [ -z "$1" ]; then echo "Usage: gnb <new_branch_name>"; return 1; fi
    git checkout -b "$1"
    git push -u origin "$1"
}

# Switch to existing branch and pull
gb() {
    if [ -z "$1" ]; then echo "Usage: gb <existing_branch_name>"; return 1; fi
    git checkout "$1"
    gp
}

# Fetch and pull with rebase
gp() { git fetch --all --prune && git pull --rebase }

# Show staged diff
gd() {
  if [ -z $1 ]; then
    git diff --staged
  else
    git diff --staged "$1"
  fi
}
```

## Curl

```bash
# Pattern
curl -sSL -X <METHOD> <URL> -H @headers.json -d @data.json
```

## Grep

| Option | Description |
|--------|-------------|
| `-i` | Case insensitive |
| `-n` | Show line numbers |
| `-c` | Count matches |
| `-C {num}` | Include lines around match |
| `-E {pattern}` | Extended regex |

## jq (JSON Processor)

```bash
# Basic usage
jq '.field.subfield.array[x:y]' file.json     # Pretty print JSON
jq -r '.' file.json                           # Raw output (no quotes)
jq 'keys' file.json                           # Object keys
jq 'values' file.json                         # Object values
jq '.[] | select(.age > 25)' file.json        # Filter by condition
jq '.[] | {name: .name, age: .age}' file.json # Project
```

## VS Code

### Navigation & Search

| Shortcut | Action |
|----------|---------|
| `Ctrl+P` | Fuzzy Search |
| `Ctrl+Shift+P` | Command Palette |
| `Ctrl+F` / `Ctrl+Shift+F` | Find in File(s) |
| `Ctrl+H` / `Ctrl+Shift+H` | Replace in File(s) |
| `Ctrl+B` / `Ctrl+Shift+B` | Toggle Left/Right Nav |
| `Ctrl+J` | Toggle Bottom Nav |

### Panels & Views

| Shortcut | Action |
|----------|---------|
| `Ctrl+E` | Solution Explorer |
| `Ctrl+D` | Debugger |
| `Ctrl+Shift+\`` | New Terminal |

### Debugging

| Shortcut | Action |
|----------|---------|
| `F9` | Add Breakpoint |
| `F5` | Run & Debug |
| `F10` | Step Over |
| `F11` | Step Into |
| `F8` | Next Problem |

### Code Navigation

| Shortcut | Action |
|----------|---------|
| `F12` | Go to Definition |
| `Ctrl+F12` | Go to Implementation |
| `Shift+F12` | Find References |
| `Ctrl+.` | Quick Action |
| `Ctrl+Space` | IntelliSense Suggestion |

### GitHub Copilot

| Shortcut | Action |
|----------|---------|
| `Ctrl+I` | Inline Copilot |
| `Ctrl+Shift+I` | Copilot Chat |
| `Shift+/` | Trigger Copilot Suggestion |
| `Shift+[` / `Shift+]` | Next/Previous Suggestion |

### Editing & Tabs

| Shortcut | Action |
|----------|---------|
| `Ctrl+D` | Multi-Select |
| `Ctrl+W` | Close Tab |
| `Alt+{num}` | Jump to Tab |
| `Ctrl+B` | Build Task |

## VS Code Settings

```json
{
    "git.autofetch": true,
    "git.confirmSync": false,
    "git.enableSmartCommit": true,
    "extensions.ignoreRecommendations": true,
    "git.ignoreRebaseWarning": true,
    "vim.useSystemClipboard": true,
    "vim.handleKeys": {
        "<C-b>": false,
        "<C-j>": false,
        "<C-p>": false,
        "<C-w>": false,
        "<C-i>": false,
        "<C-n>": false,
        "<C-f>": false,
        "<F9>": false,
        "<C-h>": false,
        "<C-l>": false,
        "<C-k>": false,
        "<C-d>": false,
        "<C-u>": false,
        "<C-e>": false,
        "<C-y>": false,
        "<C-o>": false,
        "<C-a>": false,
        "<C-t>": false,
        "<C-s>": false,
        "<C-q>": false
    },
    "workbench.iconTheme": "vscode-icons",
    "github.copilot.enable": {
        "*": false,
        "plaintext": false,
        "markdown": false,
        "scminput": false
    },
    "remote.autoForwardPortsSource": "hybrid",
    "terminal.integrated.defaultProfile.linux": "zsh"
}
```