# Reply & Comment Drafting Guide

Guidelines for drafting Reddit replies and comments that sound authentically human. Read this file whenever the user asks for help writing a reply, comment, or response to a Reddit post or thread.

## When to use

**Only when the user explicitly asks** for help writing a reply, comment, or response. Never generate replies unprompted.

## Before drafting

1. **Read the full thread first.** Always fetch via `thread` before drafting — you need the post body, existing comments, and the overall tone of the conversation.
2. **Check subreddit context.** If you haven't already, run `subreddit-info` to understand the community's rules, description, and culture.
3. **Check the user being replied to** (optional). Run `user` to understand their posting history and tone if it would help craft a better reply.

## Match the subreddit's voice

Every subreddit has a different culture. Read a few comments in the thread to absorb the tone before writing.

Examples of subreddit voice differences:
- **r/startups** — direct, founder-to-founder, metrics-heavy, nobody has time for fluff
- **r/webdev** — casual and technical, lots of "just use X" opinions, friendly debate
- **r/askdocs** — careful, measured, evidence-based, no speculation
- **r/entrepreneur** — hustle-adjacent, experience stories, tactical
- **r/SaaS** — product-focused, growth metrics, "what's your MRR" energy
- **r/technology** — news-reactive, skeptical of hype, loves calling out BS
- **r/gaming** — memes-adjacent, references, very casual, short comments

## Voice rules

These are non-negotiable. Every draft must follow these:

- **No corporate speak.** Never say "leverage", "synergy", "streamline", "at [Brand] we believe", "I'd love to help!", "Great question!", "Happy to help!" or anything that reads like a support ticket or LinkedIn post.
- **No over-enthusiasm.** Reddit is skeptical of exclamation marks and performative positivity. One exclamation max per reply, and only if it feels natural. Two or more = instant bot detection.
- **No bullet-point lists** unless the subreddit commonly uses them (e.g. r/buildapc spec lists, r/legaladvice step-by-step). Replies should read as conversational paragraphs.
- **Use casual grammar.** Contractions are mandatory — "don't", "can't", "I'd". Sentence fragments fine. Starting sentences with "Yeah", "Honestly", "Fwiw", "Tbh" — all fine. Lowercase is fine for informal subs.
- **Be specific and opinionated.** Generic advice gets downvoted. "I switched from X to Y six months ago and the difference in Z was night and day" beats "There are many great options available." Redditors respect strong takes backed by experience.
- **Share experience, not pitches.** If the user's product/brand is relevant, weave it in naturally as personal experience, not a recommendation. "We ran into the same thing and ended up building [tool] for it" reads very differently from "Check out [tool], it does exactly this!" The first sounds like a fellow Redditor. The second sounds like an ad.
- **Mirror the thread's depth.** If existing comments are 2-3 sentences, don't write 5 paragraphs. If the thread is technical and detailed with code examples, match that depth. If it's a quick meme thread, keep it short.
- **Acknowledge what others said.** Reference or build on existing comments in the thread when relevant — "Adding to what u/someone said...", "The top comment nailed it but one thing I'd add...", "Interesting take — I had a different experience though". This signals you actually read the thread.
- **Be okay with imperfection.** Real Reddit comments have minor tangents, asides in parentheses, the occasional "edit: typo". A too-polished comment looks suspicious. It's fine to ramble slightly or go on a brief tangent if it feels natural.
- **Never use hashtags.** Reddit doesn't use hashtags. Ever.
- **Avoid markdown headers in comments.** Regular Redditors almost never use `##` headers in comments. Bold for emphasis is fine sparingly.

## Reply structure (flexible, not rigid)

A natural Reddit comment typically flows like:

1. **Quick hook or context** — relate to the OP's situation in 1 sentence. This shows you actually read their post.
2. **The substance** — your actual insight, experience, or answer. 1-3 short paragraphs. This is the meat.
3. **Optional closer** — a question back to OP, a small caveat ("ymmv though"), a joke, or just... nothing. Not every comment needs a tidy ending.

Do NOT use headers, numbered steps, or heavy formatting that looks AI-generated. The structure above is a mental model, not a template to follow literally.

## Product/brand mentions

When the user's product or brand is relevant to the thread:

- **Never lead with it.** Start with genuine value — answer the question, share insight, relate to the problem.
- **Mention it naturally in passing.** "...we ended up building X for exactly this reason" or "I've been using X and it handles that edge case pretty well" — not "I recommend X, here's why."
- **Don't include links unless asked.** A comment that says "we built something for this — happy to share if you're interested" gets way more engagement than a comment with a URL in it. Reddit's spam filters also flag link-heavy comments.
- **If the post is specifically asking for tool recommendations**, then yes, mention the product directly — but still frame it as personal experience, not a pitch. "We use [X] for this — been solid for about 6 months, main thing I like is [specific detail]."
- **One mention max.** Never mention the product/brand more than once in a single comment. Repeating it screams advertisement.

## What to include with each draft

When presenting a draft reply to the user, always include:

1. **The permalink** to the post or comment being replied to
2. **The draft text** — ready to copy-paste
3. **A brief note** on why this approach/angle was chosen (1-2 sentences)
4. **A reminder**: "Copy and paste this into Reddit — I can't post for you."

## Multiple options

If the user asks for reply ideas (plural), or if the situation calls for it, offer 2-3 variations with different angles or tones:

- One that's more **technical/detailed**
- One that's more **casual/anecdotal**
- One that **subtly mentions their product** (if relevant)

Let the user pick, combine, or ask for adjustments.

## Anti-patterns to avoid

These are things that immediately mark a comment as AI-generated or spam on Reddit:

- Starting with "Great question!" or "That's a really interesting point!"
- Using the phrase "I hope this helps!" at the end
- Listing 5+ bullet points of advice
- Using words like "comprehensive", "robust", "seamless", "cutting-edge"
- Writing in a perfectly structured intro-body-conclusion format
- Being relentlessly positive with no caveats or nuance
- Using em dashes excessively (one per comment max)
- Responding to everything in the thread instead of focusing on one angle
- Signing off with a name, title, or company
