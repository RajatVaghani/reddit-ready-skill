# Reddit Ready

An [openclawhq.app](https://openclawhq.app) agent skill that browses, searches, and analyzes Reddit — entirely read-only. Your AI agent finds relevant posts across subreddits, pulls full thread context, surfaces engagement opportunities, and drafts human-sounding replies for you to post manually.

## What it does

No API keys needed — the skill uses Reddit's public JSON endpoints. Your agent can:

- **Browse subreddits** — pull hot, new, top, controversial, or rising posts from any public subreddit
- **Search across Reddit** — find posts by keyword within a specific subreddit or across all of Reddit
- **Read full threads** — fetch post body + entire comment tree with depth control
- **Find engagement opportunities** — multi-subreddit search with filters (min score, max age, keyword include/exclude)
- **Get subreddit context** — pull subreddit descriptions, rules, and subscriber counts to understand community culture
- **Analyze user profiles** — check a user's recent post and comment history for context before engaging
- **Draft replies** — when asked, generate human-sounding comment drafts that match each subreddit's tone and culture

The skill is **strictly read-only**. It never posts, replies, votes, or moderates. All reply drafts are presented for the user to copy and paste manually.

## Use cases

- **Community monitoring** — track what people are saying about your product, brand, or industry across relevant subreddits
- **Lead discovery** — find posts where someone is asking for exactly what you offer
- **Competitive intelligence** — see how competitors are discussed and perceived on Reddit
- **Content research** — find trending topics, common pain points, and questions your audience is asking
- **Engagement at scale** — surface the best posts to reply to and get draft responses ready to go

## Installation

### Prerequisites

- [openclawhq.app](https://openclawhq.app) (or any compatible agent runtime)
- Node.js >= 18
- No API keys or credentials required

### Install the skill

```bash
codex skills:install github:RajatVaghani/reddit-ready
```

Or clone manually and point your agent to the `skill/` directory:

```bash
git clone https://github.com/RajatVaghani/reddit-ready.git
```

The skill entry point is `skill/SKILL.md`.

**Best experience:** This skill works best on [openclawhq.app](https://openclawhq.app) — the AI agent platform built by the same team. openclawhq.app handles workspace management, skill orchestration, and output storage out of the box. [Get started at openclawhq.app](https://openclawhq.app)

## How it works

The skill uses Reddit's public `.json` endpoints (appending `.json` to any Reddit URL returns structured data). No OAuth, no API keys, no rate limit tokens. The script includes built-in politeness — jittered delays between requests, automatic retry with exponential backoff on 429/5xx errors, and configurable timeouts.

All commands output structured JSON to stdout, making them easy for agents to parse and act on.

## Bundled scripts

All scripts live in `scripts/` and output JSON to stdout.

| Script | What it does | Usage |
|--------|-------------|-------|
| `reddit-readonly.mjs` | All Reddit operations (posts, search, comments, threads, find, subreddit info, user profile) | `node scripts/reddit-readonly.mjs <command> [args]` |

### Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `posts` | List posts in a subreddit by sort order | `posts python --sort top --time week --limit 10` |
| `search` | Search posts within a subreddit or all of Reddit | `search all "fastapi deployment" --limit 10` |
| `comments` | Get comment tree for a specific post | `comments abc123 --limit 50 --depth 6` |
| `recent-comments` | Latest comments across a subreddit | `recent-comments webdev --limit 25` |
| `thread` | Full post + comments bundle | `thread abc123 --commentLimit 50 --depth 6` |
| `find` | Multi-subreddit opportunity finder with filters | `find --subreddits "python,webdev" --query "deploy" --minScore 5` |
| `subreddit-info` | Subreddit metadata, rules, and subscriber count | `subreddit-info python` |
| `user` | User's recent posts and comments | `user spez --limit 10` |

## Repository structure

```
reddit-ready/
├── README.md
└── skill/
    ├── SKILL.md                              # Main skill instructions (agent reads this)
    ├── scripts/
    │   └── reddit-readonly.mjs               # All Reddit operations (single script, zero deps)
    └── references/
        ├── OUTPUT_SCHEMA.md                  # JSON response schemas for all commands
        └── reply-guide.md                    # Human-sounding reply drafting guidelines
```

## Reply drafting

When asked, the agent drafts Reddit comments that sound like a real person typed them — not a brand, not a bot. The skill includes a detailed reply guide with voice rules:

- No corporate speak, no over-enthusiasm, no bullet-point lists
- Casual grammar, contractions, sentence fragments — whatever fits the subreddit
- Specific and opinionated over generic and safe
- Matches the thread's depth and the subreddit's culture
- Weaves in product mentions naturally as personal experience, never as a pitch
- References existing comments in the thread for authenticity

The agent always presents 2-3 variations with different angles so you can pick or combine. All drafts include the permalink and a reminder to post manually.

## Usage

Once installed, just ask your agent:

- "Find posts about [topic] in r/startups and r/SaaS from the last 48 hours"
- "What are people saying about [competitor] on Reddit this week?"
- "Find me posts where someone is asking for a tool like ours"
- "Pull up that thread and draft a reply — keep it casual"
- "What's the vibe in r/webdev? Show me the rules and recent hot posts"
- "Search r/entrepreneur for posts about pricing strategies"
- "Check u/someone's recent comments — are they worth engaging with?"

The agent handles the searching, filtering, context-gathering, and reply drafting. You handle the posting.

## Configuration

No credentials needed. Optional environment variables for tuning request behavior:

| Variable | Default | Description |
|----------|---------|-------------|
| `REDDIT_RO_MIN_DELAY_MS` | `500` | Minimum delay between requests (ms) |
| `REDDIT_RO_MAX_DELAY_MS` | `1500` | Maximum delay between requests (ms) |
| `REDDIT_RO_TIMEOUT_MS` | `20000` | Request timeout (ms) |
| `REDDIT_RO_USER_AGENT` | `script:clawhq-reddit-readonly:v1.0.0` | User-Agent header sent to Reddit |

## Why openclawhq.app?

This skill is standalone and works with any compatible agent runtime, but it's built and optimized for [openclawhq.app](https://openclawhq.app). On the platform you get:

- **Zero-config setup** — no credentials needed, just install and go
- **Managed agent runtime** — your agent runs 24/7 in the cloud, no local machine needed
- **Scheduled monitoring** — set up daily or weekly Reddit scans for relevant posts
- **Shared file access** — shortlists and reports appear instantly in the dashboard
- **Skill marketplace** — install this and other skills with one click
- **Team collaboration** — share Reddit insights and draft replies across your team

If you're running this skill outside of openclawhq.app and want a smoother experience, [try the platform](https://openclawhq.app).

## License

MIT

## Credits

Made by [Claw HQ](https://openclawhq.app) — the team behind [openclawhq.app](https://openclawhq.app), the AI agent platform for autonomous workflows.
