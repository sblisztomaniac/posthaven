Here’s your complete and **streamlined `backlog.md`** file for the **Dynamic Post Collector MVP**, structured for **90-minute execution**. It breaks down all tasks by epics and user stories with a clear and focused scope — aligned with your real-time API+RSS fetching and local tagging interface.

---

### 📋 `backlog.md`: Dynamic Post Collector MVP (Live Data, Local Notes)

````markdown
# 📋 Backlog: Dynamic Post Collector MVP

This backlog defines the epics, user stories, and task breakdown for building a local, dynamic app that fetches liked/saved content from X.com, Substack, and LinkedIn — and allows tagging and notes with local persistence.

---

## 🧱 Epic 1: Setup & Configuration

### 🧩 User Story:
As a developer, I want to quickly set up my environment and config files so I can start fetching data.

#### ✅ Tasks
- [ ] Create `post_collector/` project folder
- [ ] Create `.env` file with:
  - `X_BEARER_TOKEN`
  - `X_USER_ID`
- [ ] Create `feeds.json` with sample Substack RSS URLs
- [ ] Create `linkedin_saves.json` with mock entries
- [ ] Install required packages:
  - `streamlit`, `requests`, `feedparser`, `python-dotenv`

---

## 🔌 Epic 2: Data Fetching & Normalization

### 🧩 User Story:
As a user, I want to load my liked/saved posts from X, Substack, and LinkedIn into a single list.

#### ✅ Tasks
- [ ] Write `fetch_x_likes()` function
  - Use `Bearer Token` to fetch liked tweets
  - Extract `id`, `author`, `text`, `created_at`, `url`
- [ ] Write `fetch_substack_feeds()` function
  - Load RSS URLs from `feeds.json`
  - Parse `title`, `summary`, `link`, `published`
- [ ] Load `linkedin_saves.json` into memory
- [ ] Normalize all post objects into this structure:

```python
{
  "id": str,
  "platform": "x" | "substack" | "linkedin",
  "title": str,
  "author": str,
  "url": str,
  "summary": str,
  "saved_at": str (YYYY-MM-DD)
}
````

---

## 🖼 Epic 3: UI – View & Annotate Posts

### 🧩 User Story:

As a user, I want to view all saved posts in a clean UI and add tags or notes for future reference.

#### ✅ Tasks

* [ ] Display search input (`st.text_input`)
* [ ] Loop through posts in `st.expander` format

  * Show platform badge
  * Title (as clickable link)
  * Author + summary (trimmed)
  * Saved date
* [ ] Add `st.text_input` for tag entry
* [ ] Add `st.text_area` for note entry

---

## 💾 Epic 4: Save & Load Local Notes

### 🧩 User Story:

As a user, I want my tags and notes to be saved so I don’t lose my work after closing the app.

#### ✅ Tasks

* [ ] Create `local_notes.json` (if not exists)
* [ ] On app load:

  * Load previous notes/tags by `post_id`
* [ ] On user edit:

  * Update in-memory `notes_map[post_id]`
* [ ] Add `💾 Save All` button:

  * On click: write all `post_id`, `tags`, `note`, `last_edited` to `local_notes.json`

---

## 🔄 Epic 5: Refresh Content (Live Fetch)

### 🧩 User Story:

As a user, I want to fetch the latest liked posts or articles without restarting the app.

#### ✅ Tasks

* [ ] Add `🔁 Refresh Posts` button
* [ ] On click:

  * Call `fetch_x_likes()` and `fetch_substack_feeds()`
  * Reload the dashboard with new posts

---

## 🧪 Epic 6: Testing & Error Handling

### 🧩 User Story:

As a developer, I want the app to handle missing data or errors gracefully.

#### ✅ Tasks

* [ ] Handle X.com API failure (e.g. rate limit)
* [ ] Catch RSS parse errors (invalid URLs)
* [ ] Show fallback message if `linkedin_saves.json` is empty
* [ ] Ensure `local_notes.json` is safely created and updated

---

## 🛑 Out of Scope (For MVP)

* Multi-user login
* OAuth-based login
* GPT summaries
* Markdown/Notion export
* Tag suggestion/autocomplete

---

## 🧠 Stretch Goals (Optional)

* Add tag filters in sidebar
* Export notes to Markdown
* Group posts by platform or tag

```

---

Would you like this backlog converted into GitHub-style issue templates next? I can format each Epic/User Story into JSON for easy uploading to your repo.
```
