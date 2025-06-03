Here is the detailed and updated `PRD.md` for your **Dynamic Post Collector MVP** — now clearly referencing **X.com (formerly Twitter)**, Substack, and LinkedIn.

---

### 📄 `PRD.md`: Dynamic Post Collector MVP (X.com + Substack + LinkedIn)

---

## 🧭 Objective

Build a single-user dashboard that dynamically fetches and organizes **saved or liked content** from:

* 🐦 **X.com** (liked posts via API)
* 📬 **Substack** (via RSS feeds)
* 💼 **LinkedIn** (manually imported JSON)

It should allow the user to:

* View saved posts from all platforms in one place
* Tag, annotate, and search through them
* Persist user-created tags and notes locally

---

## 🎯 Key Features

| Feature                   | Description                                              |
| ------------------------- | -------------------------------------------------------- |
| 🐦 X.com Integration      | Fetch latest liked posts via API                         |
| 📬 Substack Integration   | Parse RSS feeds for latest posts                         |
| 💼 LinkedIn Manual Import | Load `linkedin_saves.json` file with saved post metadata |
| 🗂️ Unified View          | Display posts in a consistent, scrollable layout         |
| 🏷️ Tagging & Annotation  | Allow users to add/edit tags and notes                   |
| 🔍 Search                 | Filter posts by keywords and tags                        |
| 💾 Local Persistence      | Save tags/notes to a file or lightweight DB              |
| 🔁 Refresh Button         | Pull new content from X and Substack on demand           |

---

## 🧱 Data Model

### Unified Post Schema

```json
{
  "id": "string",
  "platform": "x|substack|linkedin",
  "title": "string",
  "author": "string",
  "url": "string",
  "summary": "string",
  "tags": ["string"],
  "note": "string",
  "saved_at": "YYYY-MM-DD"
}
```

### Persistence File

* `local_notes.json` stores tag and note overrides per `id`.

---

## 🔌 Data Ingestion Logic

### 🐦 X.com

* API: `GET /2/users/:id/liked_tweets`
* Auth: Bearer Token (manually added to `.env`)
* Fetched Fields:

  * `id`, `text`, `author.username`, `created_at`, `url`

### 📬 Substack

* RSS URLs listed in config or `feeds.json`
* Use Python `feedparser` to fetch:

  * `title`, `summary`, `link`, `published`, `author`

### 💼 LinkedIn

* Manually create/import a file: `linkedin_saves.json`
* Each entry should match unified schema

---

## 🖼 UI Requirements

### Dashboard Page

| Component          | Description                                         |
| ------------------ | --------------------------------------------------- |
| 🔍 Search Bar      | Filters posts by `title`, `summary`, `tags`, `note` |
| 📋 Post Cards      | One card per post, expandable view                  |
| 🏷️ Tag Editor     | Input chips or comma-separated text                 |
| 📝 Note Editor     | Multi-line `text_area`                              |
| 💾 Save Button     | Writes local tag/note edits to `local_notes.json`   |
| 🔁 Refresh Buttons | Re-fetch X.com likes and Substack feeds             |

### Card Display Example:

```
[Platform Badge] [Title as Link]
by [Author] on [saved_at]

Summary...

Tags: [founder] [fundraising]
Note: [Useful for CapTableGuru UI ideas]
```

---

## 🛠 Tech Stack

| Layer    | Tech                                          |
| -------- | --------------------------------------------- |
| Frontend | Streamlit                                     |
| Backend  | Python scripts for API & RSS                  |
| Storage  | JSON (local\_notes.json) or SQLite (optional) |
| Env Vars | `.env` for tokens and feed list               |

---

## 🧪 Testing & Edge Cases

| Case                            | Expected Behavior                 |
| ------------------------------- | --------------------------------- |
| Invalid RSS URL                 | Skip and log error                |
| No internet                     | Display cached data only          |
| Empty tag/note                  | Acceptable — save as empty string |
| Duplicate post IDs              | Skip or override (warn in logs)   |
| Twitter API rate limit exceeded | Show Streamlit warning message    |

---

## ⏱ Timeline (MVP Implementation)

| Task                                    | Time Estimate |
| --------------------------------------- | ------------- |
| Set up `.env`, feed config, sample data | 0.25 day      |
| Fetch X.com likes via API               | 0.25 day      |
| Fetch Substack posts via RSS            | 0.25 day      |
| Parse LinkedIn JSON                     | 0.25 day      |
| Normalize + merge posts                 | 0.25 day      |
| Build UI to view + search + tag         | 0.5 day       |
| Add local save logic                    | 0.25 day      |
| Test refresh + save behavior            | 0.25 day      |

Total: **\~2 days**

---

## ⛔ Out of Scope (MVP)

* OAuth login or user sessions
* Real LinkedIn integration (no public API)
* GPT tagging or summaries
* Multi-user support
* Markdown or Notion export

---

## 🔮 Future Enhancements

* GPT summarization per post
* Chrome extension to save LinkedIn content live
* Tag suggestions or autocomplete
* Export to Markdown, Notion, or CSV
* Background job to auto-refresh content

---

Let me know if you want this PRD bundled with:

* `env_template`, `feeds.json`, and `local_notes.json` templates
* A `main.py` scaffold
* GitHub issues autogenerated from this PRD

Ready to ship 🚀
