# CC Share Plugin

Share your Claude Code conversations via a link.

## Install

```bash
claude plugin marketplace add Xiaooolong/cc-share-plugin
claude plugin install cc-share@cc-share-plugin
```

Then create `~/.cc-share` with your config (get your token at [cc-share.onrender.com](https://cc-share.onrender.com)):

```
CC_SHARE_TOKEN=your_token
CC_SHARE_URL=https://cc-share.onrender.com
```

## Usage

In any Claude Code session, run:

```
/share
```

You'll get a shareable URL. Your collaborator can open it to browse the conversation, or download the JSON to import into their own tools.

## How it works

1. `/share` finds the current conversation's JSONL file
2. Uploads it to the CC Share server (server-side parsing, no local dependencies)
3. Returns a shareable link

No Node.js, Python, or any local tools required — just `curl`.
