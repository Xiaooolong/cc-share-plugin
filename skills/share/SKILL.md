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
> Looks like /share isn't set up yet. Quick fix:
> 1. Open https://cc-share.onrender.com and sign in with GitHub
> 2. You'll see a setup command on your dashboard — copy and paste it in your terminal
> 3. Then run `/share` again and you're good to go!

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
