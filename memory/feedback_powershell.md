---
name: PowerShell command syntax
description: User is on Windows PowerShell — avoid ! prefix and Unix-style quoting
type: feedback
---

Do NOT suggest commands with `!` prefix (Claude Code shell escape) or Unix-style `< file` input redirection — they don't work in the user's PowerShell terminal.

**Why:** PowerShell uses `&` to call executables with spaces in path, and `Get-Content file | & exe` instead of `< file` redirection. The `!` prefix causes syntax errors in PowerShell.

**How to apply:**
- Use `& "C:\Program Files\...\exe.exe"` instead of just running the exe
- Use `Get-Content "file" | & "exe"` instead of `exe < file`
- Use `& "C:\Program Files\GitHub CLI\gh.exe"` for gh CLI commands
- Never suggest `! command` syntax for commands the user needs to run manually
- When giving copy-paste terminal commands, always use PowerShell syntax
