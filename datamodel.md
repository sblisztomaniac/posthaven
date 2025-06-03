# 🗂️ Data Model: Post Collector MVP (Dynamic Version)

This document defines the data schema and storage layers for the dynamic Post Collector application.

---

## 🔹 1. Entity: `Post`

### Description:
A normalized post object fetched from X.com (formerly Twitter), Substack, or manually imported from LinkedIn.

### Fields:

| Field        | Type       | Required | Description |
|--------------|------------|----------|-------------|
| `id`         | string     | ✅       | Unique post identifier (Tweet ID, RSS GUID, etc.) |
| `platform`   | enum       | ✅       | `"x"`, `"substack"`, `"linkedin"` |
| `title`      | string     | ✅       | Post title or main text |
| `author`     | string     | ✅       | Author name or handle |
| `url`        | string     | ✅       | Direct link to original post |
| `summary`    | string     | ✅       | Short excerpt or body |
| `saved_at`   | string (date) | ✅    | Date of post creation or save action (format: `YYYY-MM-DD`) |

---

## 🔹 2. Entity: `UserNote`

### Description:
Stores user-specific data like tags and notes separately for persistence.

### Fields:

| Field        | Type       | Required | Description |
|--------------|------------|----------|-------------|
| `post_id`    | string     | ✅       | Foreign key mapping to `Post.id` |
| `tags`       | string[]   | ⛔       | List of user-defined tags |
| `note`       | string     | ⛔       | Freeform user-written annotation |
| `last_edited`| string (date) | ⛔    | Last modified timestamp |

---

## 🔹 3. Data Sources

| Source       | Type        | Notes |
|--------------|-------------|-------|
| `X.com`      | API         | `/2/users/:id/liked_tweets` |
| `Substack`   | RSS         | Feed URLs defined in config |
| `LinkedIn`   | Local JSON  | Manually created by user |

---

## 🔹 4. Persistence Strategy

| File                  | Purpose |
|------------------------|---------|
| `local_notes.json`     | Stores all `UserNote` entries keyed by `post_id` |
| `feeds.json`           | Contains list of Substack RSS URLs |
| `.env`                 | Stores API keys, bearer tokens, user ID for X.com |

> All fetched content is ephemeral and refreshed via API/RSS.
> Only tags and notes are persistently stored across sessions.

---

## 🔹 5. Unified Post Example

```json
{
  "id": "178934892723",
  "platform": "x",
  "title": "Most founders don’t understand dilution.",
  "author": "@founderhandle",
  "url": "https://x.com/founder/status/178934892723",
  "summary": "Here’s a thread explaining how SAFEs actually dilute your equity...",
  "saved_at": "2025-06-04"
}
