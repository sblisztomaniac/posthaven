# 🗂️ Data Model: PostHaven MVP

This document outlines the data schema for the PostHaven MVP — a personal app that collects and organizes liked/saved posts from X (Twitter), Substack, and LinkedIn.

---

## 🔖 Entity: Post

Each post from any platform (Twitter, Substack, LinkedIn) is normalized into the same structure.

### `Post`

| Field        | Type     | Description |
|--------------|----------|-------------|
| `id`         | string   | Unique post ID (e.g., Tweet ID, custom UUID, or LinkedIn URL hash) |
| `platform`   | enum     | Source platform: `"twitter"`, `"substack"`, `"linkedin"` |
| `title`      | string   | Title or main line of the post |
| `author`     | string   | Username or author of the post |
| `url`        | string   | Link to the original post |
| `summary`    | string   | Short summary or excerpt of the content |
| `tags`       | string[] | User-defined tags for organization |
| `note`       | string   | Optional personal note |
| `saved_at`   | date     | Date the post was saved or liked |
| `raw`        | object   | Original full content (optional; platform-specific)

---

## 📚 Example JSON Entry

```json
{
  "id": "tweet_17834523",
  "platform": "twitter",
  "title": "Most founders get cap tables wrong",
  "author": "@toby_morning",
  "url": "https://twitter.com/toby_morning/status/17834523",
  "summary": "Short thread on how to model dilution using SAFEs.",
  "tags": ["cap table", "startup", "funding"],
  "note": "This is the base idea for CapTableGuru's AI Copilot",
  "saved_at": "2025-06-04",
  "raw": {
    "text": "Most founders get cap tables wrong. Here's how to fix that 🧵",
    "media": null
  }
}
