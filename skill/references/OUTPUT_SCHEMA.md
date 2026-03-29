# Output Schema

All commands return JSON to stdout: `{ ok, data | error }`.

## Success envelope

```json
{ "ok": true, "data": { ... } }
```

## Error envelope

```json
{ "ok": false, "error": { "message": "...", "details": "..." } }
```

---

## Post object

Returned by `posts`, `search`, `find`, and `thread` commands.

```json
{
  "id": "abc123",
  "fullname": "t3_abc123",
  "subreddit": "python",
  "title": "How do you deploy FastAPI in production?",
  "author": "someone",
  "score": 123,
  "num_comments": 45,
  "created_utc": 1737060000,
  "created_iso": "2026-01-16T12:00:00.000Z",
  "permalink": "https://www.reddit.com/r/python/comments/abc123/.../",
  "url": "https://...",
  "is_self": true,
  "over_18": false,
  "flair": "Discussion",
  "selftext_snippet": "First 2000 chars of the post body..."
}
```

## Comment object (flattened)

Returned by `comments`, `recent-comments`, and `thread` commands.

```json
{
  "id": "def456",
  "fullname": "t1_def456",
  "author": "someone_else",
  "score": 10,
  "created_utc": 1737060100,
  "created_iso": "2026-01-16T12:01:40.000Z",
  "depth": 2,
  "parent_fullname": "t1_...",
  "permalink": "https://www.reddit.com/r/python/comments/abc123/.../def456/",
  "body_snippet": "First 2000 chars of the comment body..."
}
```

## Find result object

Extends the post object with match metadata. Returned by `find`.

```json
{
  "id": "abc123",
  "subreddit": "python",
  "title": "...",
  "score": 45,
  "num_comments": 12,
  "created_utc": 1737060000,
  "created_iso": "2026-01-16T12:00:00.000Z",
  "permalink": "https://...",
  "reason": ["query:fastapi", "include:docker,nginx", "age_h:12.5"],
  "match_score": 2
}
```

Find response also includes `criteria` (what was searched) and `meta` (counts):

```json
{
  "criteria": {
    "subreddits": ["python", "webdev"],
    "query": "fastapi",
    "include": ["docker"],
    "exclude": ["homework"],
    "minScore": 2,
    "maxAgeHours": 48,
    "perSubredditLimit": 25,
    "maxResults": 10,
    "rank": "new"
  },
  "meta": {
    "fetched_per_subreddit": { "python": 25, "webdev": 18 },
    "candidates": 7,
    "returned": 7
  },
  "results": [ ... ]
}
```

## Subreddit info object

Returned by `subreddit-info`.

```json
{
  "name": "python",
  "fullname": "t5_2qh0y",
  "title": "Python",
  "description": "Short public description...",
  "description_full": "Full sidebar description (up to 5000 chars)...",
  "subscribers": 1200000,
  "active_users": 3500,
  "created_utc": 1264710000,
  "created_iso": "2010-01-28T21:00:00.000Z",
  "over_18": false,
  "language": "en",
  "url": "https://www.reddit.com/r/python/",
  "submission_type": "any",
  "rules": [
    {
      "number": 1,
      "name": "Be respectful",
      "description": "First 500 chars of the rule description...",
      "kind": "all"
    }
  ]
}
```

## User profile object

Returned by `user`.

```json
{
  "profile": {
    "name": "spez",
    "fullname": "t2_1w72",
    "created_utc": 1118030400,
    "created_iso": "2005-06-06T00:00:00.000Z",
    "link_karma": 150000,
    "comment_karma": 800000,
    "total_karma": 950000,
    "is_gold": true,
    "is_mod": true,
    "verified": true,
    "has_verified_email": true,
    "profile_url": "https://www.reddit.com/user/spez/"
  },
  "activity": [
    {
      "type": "post",
      "id": "xyz789",
      "subreddit": "announcements",
      "title": "...",
      "score": 5000,
      "num_comments": 2000,
      "created_utc": 1737060000,
      "created_iso": "2026-01-16T12:00:00.000Z",
      "permalink": "https://...",
      "selftext_snippet": "..."
    },
    {
      "type": "comment",
      "id": "abc456",
      "subreddit": "reddit",
      "score": 200,
      "created_utc": 1737059000,
      "created_iso": "2026-01-16T11:43:20.000Z",
      "permalink": "https://...",
      "link_title": "Title of the post being commented on",
      "body_snippet": "..."
    }
  ]
}
```

## Recent comments object

Returned by `recent-comments`. Slightly different from threaded comments — includes `link_id`, `link_title`, and `link_permalink` for context.

```json
{
  "id": "ghi789",
  "fullname": "t1_ghi789",
  "subreddit": "webdev",
  "author": "someone",
  "score": 5,
  "created_utc": 1737060200,
  "created_iso": "2026-01-16T12:03:20.000Z",
  "permalink": "https://...",
  "link_id": "t3_abc123",
  "link_title": "Title of the parent post",
  "link_permalink": "https://...",
  "body_snippet": "..."
}
```
