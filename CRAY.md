# CRAY.md — Project Context for Cray Code

## Conventions

- Always save conversation before exiting Cray Code
- Use descriptive names for backups (e.g., `before-refactor`, `day-end-jun15`)

## Conversation Save/Restore Mechanism

### 🔄 Save Before Exit
Run this command to save the current conversation before closing Cray Code:

**Windows (PowerShell):**
```powershell
.\scripts\save-conversation.ps1 save my-backup-name
```

**Linux/Mac (Bash):**
```bash
./scripts/save-conversation.sh save my-backup-name
```

### 📋 List Saved Conversations
```powershell
.\scripts\save-conversation.ps1 list
```

### ⏱️ Quick Auto-Save (timestamp-based)
```powershell
.\scripts\save-conversation.ps1 auto
```

### 🔁 Restore a Previous Conversation
```powershell
.\scripts\save-conversation.ps1 restore my-backup-name
```

### 🧠 Skill Command
You can also use the built-in skill within Cray Code:
```
/save-conversation --save my-backup-name
/save-conversation --list
/save-conversation --restore my-backup-name
```

## How It Works

The save mechanism backs up:
1. **Memory files** (`.cray/memory/`) — user memories, project memories
2. **Session info** (`.cray/session.json`) — current session state
3. **Settings** (`.cray/settings.json`) — tool configuration
4. **Full output log** (`full-output.txt`) — recent conversation output

All backups are stored in `.cray/memory/backups/` with timestamp or custom names.

To restore, simply pick a backup name and the script will swap it back into place.
Then restart Cray Code to load the restored context.

## Important Files

| File | Description |
|------|-------------|
| `scripts/save-conversation.sh` | Linux/Mac save/restore script |
| `scripts/save-conversation.ps1` | Windows save/restore script |
| `.cray/skills/save-conversation/skill.md` | Cray Code skill for save/restore |
| `.cray/settings.json` | Tool configuration |
| `full-output.txt` | Latest conversation output |
