# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## CRITICAL: Session Synchronization Protocol

### On Session Start (MANDATORY):
**IMMEDIATELY execute upon first user interaction:**
```bash
git pull origin main
```
Inform the user: "Syncing with remote repository..." and show any updates pulled.

### Before Session End:
When user indicates they are done (says "done", "goodbye", "exit", "bye", or similar):
1. Check for uncommitted changes: `git status`
2. If changes exist:
   - Add all changes: `git add .`
   - Commit with descriptive message
   - Push to remote: `git push origin main`
3. Confirm with user: "Changes have been pushed to GitHub. Session synchronized."

### During Session:
- Commit significant changes periodically with descriptive messages
- Always pull before making changes if session has been idle
- Use clear commit messages that describe what was accomplished

## Repository Information

- **Remote**: https://github.com/splitleasesharath/claude_sync.git
- **Branch**: main
- **Purpose**: Synchronize Claude workspace across multiple computers/sessions

## Current Configuration

- `.claude/settings.local.json` - Contains Claude-specific permission settings
- Git repository initialized and connected to GitHub

## Project Guidelines

When a project is added to this directory:
1. Update this section with build/test/lint commands
2. Document the architecture and structure
3. Note any project-specific conventions
4. Keep synchronization protocol intact above