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

## 🔔 SLACK NOTIFICATION PROTOCOL

### MANDATORY TASK COMPLETION NOTIFICATIONS

#### Initial Setup (One-time per machine):
1. Create `.env.local` file in the repository root
2. Add your Slack webhook URL:
   ```
   SLACK_WEBHOOK_URL=your_webhook_url_here
   ```
3. This file is automatically excluded from git (see .gitignore)
4. Each machine needs its own `.env.local` file

#### Configuration:
**Slack Webhook URL:** Stored in `.env.local` file (not committed to GitHub)
- Look for `SLACK_WEBHOOK_URL` in `.env.local`
- Or check `slack-config.local.json` for webhook configuration

#### When to Send Notifications:
**Send a Slack notification AFTER completing:**
- Any file creation, modification, or deletion
- Running tests or builds
- Completing any user-requested task
- Fixing bugs or implementing features
- Any significant operation completion

#### Notification Format:
```bash
# First, load the webhook URL from local config:
SLACK_WEBHOOK=$(grep SLACK_WEBHOOK_URL .env.local | cut -d '=' -f2)

# After completing ANY task, send notification:
curl -X POST "$SLACK_WEBHOOK" \
  -H 'Content-Type: application/json' \
  -d '{
    "text": "✅ Task Completed",
    "blocks": [
      {
        "type": "section",
        "text": {
          "type": "mrkdwn",
          "text": "*Task:* [TASK_DESCRIPTION]\n*Status:* Completed\n*Time:* [TIMESTAMP]\n*Repository:* claude_sync"
        }
      }
    ]
  }'
```

#### Example Implementation:
```bash
# Load webhook URL from local config:
SLACK_WEBHOOK=$(grep SLACK_WEBHOOK_URL .env.local | cut -d '=' -f2)

# After editing a file:
git add . && git commit -m "Update: file.txt" && git push origin main
curl -X POST "$SLACK_WEBHOOK" \
  -H 'Content-Type: application/json' \
  -d '{"text":"✅ File updated and pushed: file.txt"}'

# After completing a feature:
curl -X POST "$SLACK_WEBHOOK" \
  -H 'Content-Type: application/json' \
  -d '{"text":"✅ Feature implemented: User authentication"}'
```

### NOTIFICATION RULES:
1. **ALWAYS NOTIFY** - Send notification after EVERY task completion
2. **INCLUDE CONTEXT** - Describe what was done in the notification
3. **TIMESTAMP EVERYTHING** - Include time information when possible
4. **ERROR NOTIFICATIONS** - Also notify if a task fails
5. **BATCH NOTIFICATIONS** - For multiple related tasks, send one comprehensive notification

### Error Notification Format:
```bash
# Load webhook URL from local config:
SLACK_WEBHOOK=$(grep SLACK_WEBHOOK_URL .env.local | cut -d '=' -f2)

curl -X POST "$SLACK_WEBHOOK" \
  -H 'Content-Type: application/json' \
  -d '{"text":"❌ Task Failed: [ERROR_DESCRIPTION]"}'
```