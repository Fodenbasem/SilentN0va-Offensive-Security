# Linux Terminal Customization & Productivity Hacks

This guide covers advanced terminal configuration, session management using TMUX, keyboard shortcuts, and custom shell aliases to maximize productivity during penetration testing.

---

## 1. Shell Aliases & Customization (.bashrc / .zshrc)

Custom aliases save time by replacing long, repetitive commands with short triggers.

### Adding Permanent Aliases
Open your shell configuration file (`~/.bashrc` or `~/.zshrc`):
```bash
nano ~/.zshrc
```

Add useful offensive security aliases at the end of the file:
```bash
# Quick IP check
alias myip="ip -br a"

# Fast directory web server
alias pyserv="python3 -m http.server 8000"

# Common Nmap defaults
alias fastscan="nmap -sV -sC -T4"

# Quick netcat listener
alias ncl="nc -nvlp 4444"
```

Apply changes immediately without logging out:
```bash
source ~/.zshrc
```

---

## 2. Terminal Multiplexing with TMUX

TMUX allows you to run multiple terminal sessions inside a single window, split panes, and detach sessions in the background.

### Basic Management
- **Start new session:** `tmux`
- **Start named session:** `tmux new -s pentest`
- **Attach to session:** `tmux attach -t pentest`
- **List sessions:** `tmux ls`

### Essential Key Shortcuts (Prefix = `Ctrl + b`)
- **Split vertically:** `Ctrl + b` then `%`
- **Split horizontally:** `Ctrl + b` then `"`
- **Switch panes:** `Ctrl + b` then `Arrow Keys`
- **Close pane:** `Ctrl + d`
- **Detach session:** `Ctrl + b` then `d`

---

## 3. Command History Mastery

Efficiently searching and utilizing execution history speeds up multi-stage attacks.

### Navigation Shortcuts
- **Reverse search history:** `Ctrl + r` (type keyword to find past commands)
- **Clear screen:** `Ctrl + l`
- **Cancel current line:** `Ctrl + c`
- **Execute previous command as root:** `sudo !!`
- **Reuse last command argument:** `!$` (e.g., `mkdir test` then `cd !$`)

### History Cleaning for Operations
Clear command history for privacy or cleanup:
```bash
history -c
history -w
```
