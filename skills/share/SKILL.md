---
name: share
description: Share the current Claude Code conversation via a link
---

# Share This Conversation

Upload the current conversation to CC Share and return a shareable URL.

## Config

- Token: !`grep CC_SHARE_TOKEN ~/.cc-share 2>/dev/null | cut -d= -f2 || echo "NOT_SET"`
- URL: !`grep CC_SHARE_URL ~/.cc-share 2>/dev/null | cut -d= -f2 || echo "NOT_SET"`

## Instructions

If Token is "NOT_SET", tell the user:
> To use /share, you need to set up your token first:
> 1. Go to https://cc-share.onrender.com and login with GitHub
> 2. Copy the config command from your dashboard
> 3. Run it in your terminal — it creates `~/.cc-share` with your token
> Then try `/share` again.

Then stop. Do not proceed.

If Token is set, do the following:

1. Find the current conversation JSONL. List `~/.claude/projects/` and find the directory matching the current project. CC converts paths like `E:/drafts/my_project` → `E--drafts-my-project` (`:` removed, `/` and `_` replaced by `-`). Pick the most recent `.jsonl` file in that directory.

2. Upload it:
```bash
curl -s -X POST "<URL>/api/upload" \
  -H "Authorization: Bearer <TOKEN>" \
  -F "file=@<JSONL_PATH>"
```

3. Show the user the returned `url` field. Done.

Do NOT parse the JSONL. Do NOT ask questions. Just find the file, curl it, show the URL.
