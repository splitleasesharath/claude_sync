# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 🚨 CRITICAL: AGGRESSIVE SYNCHRONIZATION PROTOCOL - MANDATORY 🚨

### YOUR SYNCHRONIZATION LIFE DEPENDS ON THIS:

#### BEFORE EVERY SINGLE ACTION:
**Pull changes RELIGIOUSLY before doing ANYTHING:**
- Before reading any file: `git pull origin main`
- Before editing any file: `git pull origin main`
- Before creating any file: `git pull origin main`
- Before running any command: `git pull origin main`
- Even before thinking about making changes: `git pull origin main`

#### AFTER EVERY SINGLE CHANGE:
**Push changes IMMEDIATELY like your existence depends on it:**
- After editing any file: `git add . && git commit -m "Update: [description]" && git push origin main`
- After creating any file: `git add . && git commit -m "Create: [description]" && git push origin main`
- After deleting any file: `git add . && git commit -m "Delete: [description]" && git push origin main`
- After ANY modification whatsoever: COMMIT AND PUSH IMMEDIATELY

### SYNCHRONIZATION RULES - NO EXCEPTIONS:
1. **ALWAYS PULL FIRST** - Before touching ANYTHING, pull from remote
2. **ALWAYS PUSH IMMEDIATELY** - After ANY change, no matter how small
3. **NEVER BATCH CHANGES** - Each change gets its own commit and push
4. **ASSUME CONFLICTS** - Always expect another instance changed something
5. **SYNC PARANOIA IS GOOD** - When in doubt, pull again
6. **PUSH EVEN TINY CHANGES** - Fixed a typo? PUSH IT. Added a space? PUSH IT.

### Session Start:
```bash
git pull origin main  # MANDATORY FIRST COMMAND
git status           # Check current state
```

### Session End:
```bash
git status                                    # Check for ANY uncommitted changes
git add .                                     # Stage EVERYTHING
git commit -m "Final sync: [timestamp]"      # Commit with timestamp
git push origin main                          # Push EVERYTHING
```

### REMEMBER:
- Another Claude instance could be working RIGHT NOW
- Every second without pulling risks conflicts
- Every second without pushing risks losing work
- SYNCHRONIZE LIKE YOUR LIFE DEPENDS ON IT

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