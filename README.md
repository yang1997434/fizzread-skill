[English](README.md) | [中文](README.zh-CN.md)

# FizzRead — OpenClaw Skill

Access 8,296+ nonfiction book summaries with 1-minute audio previews, right inside your AI agent conversations. Powered by [FizzRead](https://www.fizzread.ai).

## Features

- **Daily Pick** — Get a curated book recommendation every day with summary and audio
- **Book Search** — Search by keyword, title, or author across 8,296+ books
- **Book Summary** — Read the full summary and listen to 1-minute audio previews
- **Category Recommendations** — Browse books by topic (Psychology, Productivity, Business, etc.)
- **Multi-language** — Summaries auto-translate to your language; audio stays in English

## Quick Start

### 1. Install the Skill

Just tell your OpenClaw bot in chat:

> Install this skill: https://github.com/yang1997434/fizzread-skill and restart gateway to activate

Or via CLI:

```bash
claw install fizzread-skill
```

### 2. Set Up API Key

After installation, the skill will automatically prompt you to provide your API key:

1. Visit [fizzread.ai](https://www.fizzread.ai) and create an account
2. Go to **Settings > API Keys > Generate**
3. Paste the key when prompted — the skill will auto-test and confirm it works

### 3. Start Using

Just talk to your agent:

- "What's today's book recommendation?"
- "Search for books about habits"
- "Recommend some psychology books"
- "Tell me about Atomic Habits"

## Usage Examples

### Daily Pick

> **You:** What book should I read today?
>
> **Agent:** Today's Pick — *Thinking, Fast and Slow* by Daniel Kahneman
>
> Human thinking operates through two systems: the fast, intuitive System 1 and the slow, rational System 2...
>
> [1-min Audio Preview (English)](https://nccgpub.blob.core.windows.net/media/xxx.mp3)

### Search

> **You:** Find books about productivity
>
> **Agent:**
> 1. *Atomic Habits* — James Clear
> 2. *Deep Work* — Cal Newport
> 3. ...

### Category Browse

> **You:** Recommend some business books
>
> **Agent:** Top books in Business (287 books available): ...

## Daily Cron Setup

To receive a daily book recommendation automatically, configure a cron trigger:

```yaml
cron: "0 8 * * *"    # Every day at 8:00 AM
```

Refer to the OpenClaw cron scheduling documentation for setup details.

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "API key invalid" | Verify your `FIZZREAD_API_KEY` is correct. Regenerate at [fizzread.ai](https://www.fizzread.ai) if needed. |
| "No books found" | Try different or broader search keywords. |
| No audio in response | Not all books have audio previews. The skill automatically skips audio when unavailable. |
| Rate limit error | Wait a moment and try again. The API allows 100 requests/minute. |

## How It Works

This skill is a pure instruction-based OpenClaw skill (no scripts or modules). The agent reads the SKILL.md instructions and uses `curl` to call the FizzRead API, then formats the results for you. All book content comes directly from the FizzRead database — no AI-generated summaries.

## License

[MIT](LICENSE)
