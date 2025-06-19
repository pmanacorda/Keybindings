# Keybindings
- C stands for CTRL

# Chrome
- / Focus Search
- <C-L> Highlight Url
- <C-Tab> New Tab
- <C-W> Close Tab
- <C-/Shft/-Tab> Next/Prev Tab
- F11 FullScreen

# Windows
- Win Search File
- </C/-Alt-Tab> Next/Previous Window
- <Win-Tab> Window View
- <Win-C-Left/Right> Next/Previous Desktop
- <Win-Up/Left/Right> Desktop Window Split
- <Alt-D> Show Desktop
- <Alt-F4> Kill Process

# Terminal
- <Alt-Enter> FullScreen
- <C-Shft-Tab> New Tab
- <C-Shft-W> Close Tab
- `explorer .` Launch explorer
- `code .` Launch VSCode
- <C-Shft-Space> Open New Tab Options

# Git
`
gcm() { git commit -m "$*" }
gf() {
    if [ -z "$1" ]; then echo "Usage: gf <search_term>"; git branch -a; return 1; fi
    git branch -a | grep -i "$1"
}
gnb() {
    if [ -z "$1" ]; then echo "Usage: gnb <new_branch_name>"; return 1; fi
    git checkout -b "$1"
    git push -u origin "$1"
}
gb() {
    if [ -z "$1" ]; then echo "Usage: gb <existing_branch_name>"; return 1; fi
    git checkout "$1"
    gp
}
gp() { git fetch --all --prune && git pull --rebase }
gd() {
  if [ -z $1 ]; then
    git diff --staged
  else
    git diff --staged "$1"
  fi
}`


# Bash
set -eou pipe
$variable = {expr}
$({expr})
if [ $? neq 0 ]; then
  {expr}
fi
if [ -z "$VAR" ];  then
  {expr}
fi

# Curl
`curl -sSL -X <Method> <Url> -H @headers.json -d @data.json`

# Pipe Grep
-i case insensitive
-A/B {num} include top, bottom rows
-E {pattern} match pattern (useful for | condition)
-| xargs to feed output to next command

# Jq
jq -r '.field.subfield[x:y]'

# VSCode
- <C-P> Fuzzy Search
- <C-Shft-P> Command Palette
<C-/Shft/-F> Find in File(s)
<C-/Shft/-H> Replace in Files(s)
<C-/Shft/-B> Toggle Left/Right Nav
<C-J> Toggle bottom Nav
<C-E> Solution Explorer
<C-D> Debugger
F9 Add Breakpoint
F5 Run & Debug
F10 Step Over
F11 Step Into
F12 Go to definition
<Ctrl+F12> Go to implementation
<Shft+F12> Find References
<C-B> Build Task
<C-Shft-`> New Terminal
<C-I> Inline Copilot
<C-Shft-I> Copilot Chat
<C-D> MultiSelect
<C-W> Close Tab
<Alt-{num}> Jump to Tab
<Shft-/> Trigger Copilot Suggestion
<Shft-[]> Next/Prev Suggestion
<C-.> Quick Action
<C-Space> Intellisense Suggestion

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
    "terminal.integrated.defaultProfile.linux": "zsh",
}