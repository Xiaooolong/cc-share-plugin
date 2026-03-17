# /share for Claude Code

One command to share any Claude Code conversation as a link.

```
> /share
Shared! https://cc-share.onrender.com/share/uPQhT3aweVIF
```

Your collaborator opens the link, reads the full conversation, and downloads it to import into their own CC or agent tools.

---

## Setup (2 min)

**1. Install the plugin**

```bash
claude plugin marketplace add Xiaooolong/cc-share-plugin
claude plugin install cc-share@cc-share-plugin
```

**2. Get your token**

Go to [cc-share.onrender.com](https://cc-share.onrender.com), login with GitHub, and copy the install command from your dashboard. It looks like:

```bash
printf "CC_SHARE_TOKEN=your_token\nCC_SHARE_URL=https://cc-share.onrender.com\n" > ~/.cc-share
```

That's it. Works in every project, on macOS, Linux, and Windows (Git Bash).

---

## Usage

In any Claude Code session:

```
/share
```

Done. No questions asked, no config prompts. Just a URL.

---

## What gets shared

- Your messages and the assistant's replies (full text, no summarization)
- Tool calls as one-line summaries (e.g. "Read file: src/app.ts", "Ran: npm test")
- **Not shared**: raw file contents, command outputs, environment variables, or system prompts

---

## FAQ

**Can my collaborator continue the conversation?**
Yes. They download the JSON and feed it into their own CC or agent tools as context.

**Is the link public?**
Anyone with the link can view it. No login required to read.

**Can I delete a shared conversation?**
Yes, from your [dashboard](https://cc-share.onrender.com/dashboard).

**Does it need Node.js or Python?**
No. The plugin uses `curl` to upload. Server handles all parsing.
