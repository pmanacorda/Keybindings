# Keyboard Shortcuts & Commands Reference

## Chrome

| Shortcut | Action |
|----------|---------|
| `/` | Focus Search |
| `Ctrl+L` | Highlight URL |
| `Ctrl+T` | New Tab |
| `Ctrl+W` | Close Tab |
| `Ctrl+Tab` / `Ctrl+Shift+Tab` | Next/Previous Tab |
| `F11` | Full Screen |

## Windows

| Shortcut | Action |
|----------|---------|
| `Win` | Search Files |
| `Alt+Tab` / `Ctrl+Alt+Tab` | Next/Previous Window |
| `Win+Tab` | Window View |
| `Win+Ctrl+Left/Right` | Next/Previous Desktop |
| `Win+Up/Left/Right` | Desktop Window Split |
| `Alt+D` | Show Desktop |
| `Alt+F4` | Kill Process |

## Terminal

| Shortcut | Action |
|----------|---------|
| `Alt+Enter` | Full Screen |
| `Ctrl+Shift+T` | New Tab |
| `Ctrl+Shift+W` | Close Tab |
| `Ctrl+Shift+Space` | Open New Tab Options |

### Terminal Commands

| Command | Description |
|---------|-------------|
| `explorer .` | Launch File Explorer |
| `code .` | Launch VS Code |

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

## Bash

### Common Patterns

```bash
# Exit on error, undefined variables, and pipe failures
set -eou pipefail

# Variable assignment and command substitution
variable=$(expression)
$(command)

# Error checking
if [ $? -ne 0 ]; then
  # Handle error
fi

# Check if variable is empty
if [ -z "$VAR" ]; then
  # Variable is empty
fi
```

## Curl

```bash
curl -sSL -X <METHOD> <URL> -H @headers.json -d @data.json
```

## Grep & Pipe Operations

| Option | Description |
|--------|-------------|
| `-i` | Case insensitive |
| `-A/B {num}` | Include top/bottom rows |
| `-E {pattern}` | Match pattern (useful for \| condition) |
| `\| xargs` | Feed output to next command |

## jq

```bash
jq -r '.field.subfield[x:y]'
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