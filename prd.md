# 📄 PRD: PostHaven MVP (Personal Collector for X, Substack, LinkedIn)

## 🎯 Objective
Create a lightweight tool that collects your liked or saved posts from:
- 🐦 X (Twitter likes via API)
- 📬 Substack (via RSS)
- 💼 LinkedIn (manual input or extension)

Let you **organize**, **tag**, **annotate**, and **search** across them in one place — without login or user accounts.

---

## 👤 Assumptions
- Single-user only (you)
- API keys, RSS links, or manual inputs are added in config
- No authentication or signup
- Runs as local app (Streamlit or simple Flask/React combo)

---

## 🧠 Core Features

| Feature         | Description |
|-----------------|-------------|
| 🐦 Twitter Likes | Use Bearer Token to fetch your last 100 liked tweets |
| 📬 Substack Feed | Parse a list of your favorite Substack RSS feeds |
| 💼 LinkedIn Saved | Import LinkedIn saved post links via CSV, copy-paste, or local browser extension |
| 🏷️ Tagging        | Add tags to any post manually |
| 📝 Notes          | Add a short annotation or reason for saving |
| 🔍 Search         | Search by keyword or tag |
| 📤 Export         | Optional: export as Markdown or JSON |

---

## 🛠️ Tech Stack

| Layer    | Tool / Framework |
|----------|------------------|
| Frontend | Streamlit (preferred for speed) |
| Backend  | Python script (FastAPI optional) |
| Storage  | Local JSON or SQLite DB |
| Twitter  | Twitter API v2 with bearer token |
| Substack | RSS feeds via `feedparser` |
| LinkedIn | CSV/JSON + manual scraping or extension (local only) |

---

## 📦 Components

### 1. Twitter Likes Fetcher
- Hardcoded bearer token
- Hit `/2/users/:id/liked_tweets`
- Store Tweet ID, text, link, author, date

### 2. Substack Fetcher
- Input: list of RSS URLs in config
- Fetch latest posts
- Extract title, link, summary, date

### 3. LinkedIn Saver (Manual)
- Load from `linkedin_saves.json` or paste into UI
- OR use a Chrome extension to capture current URL + title

---

## 🧪 Task Checklist

- [ ] Add config file for tokens, feeds, and LinkedIn data
- [ ] Twitter likes fetch + store
- [ ] Substack RSS fetch + store
- [ ] JSON loader for LinkedIn links (manual)
- [ ] UI to view, tag, annotate, and search posts
- [ ] Export to `.md` or `.json` by tag/date (optional)

---

## 📅 Timeline

| Task                         | Time Estimate |
|------------------------------|---------------|
| Twitter fetch setup          | 0.5 day       |
| Substack RSS parsing         | 0.5 day       |
| LinkedIn JSON/CSV loader     | 0.25 day      |
| Local tagging + annotation UI| 1 day         |
| Search UI                    | 0.25 day      |
| Export & polish              | 0.25 day      |

**Total: ~2.5 days**

---

## 🚫 Out of Scope

- LinkedIn API integration (not available for saved posts)
- Auth or multiple users
- Chrome extension (future add-on)

---

## 💡 Future Scope (Post-MVP)

- Chrome extension to capture LinkedIn or X posts in real time
- GPT-powered summarization or categorization
- Cross-platform similarity detection (e.g., same post on X and Substack)
- Full-text search engine (e.g., using SQLite FTS5 or Meilisearch)
