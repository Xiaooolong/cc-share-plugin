---
name: share
description: Share the current Claude Code conversation via a link
---

# Share This Conversation

Share the current conversation to CC Share and return a URL. Follow these steps in order.

## Step 1 — Read config

Read the file `~/.cc-share`. It should contain two lines:
```
CC_SHARE_TOKEN=xxx
CC_SHARE_URL=https://...
```

If the file doesn't exist or is missing either value, tell the user:

> Looks like /share isn't set up yet. Quick fix:
> 1. Open https://cc-share.onrender.com and sign in with GitHub
> 2. Copy the setup command from your dashboard and paste it in your terminal
> 3. Then run `/share` again

Then stop.

## Step 2 — Find the conversation file

List the directories in `~/.claude/projects/` and find the one matching the current project. CC converts project paths like `E:/drafts/my_project` to `E--drafts-my-project` (`:` removed, `/` and `_` replaced by `-`).

Find the most recent `.jsonl` file in that directory.

## Step 3 — Upload

Run this command (replace TOKEN, URL, and JSONL_PATH with actual values from steps 1 and 2):

```bash
curl -s -X POST "URL/api/upload" -H "Authorization: Bearer TOKEN" -F "file=@JSONL_PATH"
```

## Step 4 — Done

Show the user the `url` from the response. That's it.

**Important:** Do NOT parse the JSONL yourself. Do NOT ask any questions. Just read config, find file, curl, show URL.
