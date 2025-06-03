Here’s your clean, actionable `backlog.md` file based on the **1-hour MVP sprintplan** for your saved post collector.

---

### 📋 `backlog.md`: Post Collector MVP

```markdown
# 🧾 Backlog: Post Collector MVP (1-Hour Local Version)

This backlog captures all tasks to be executed in a 1-hour sprint to build a personal Streamlit-based app that collects saved posts from Twitter, Substack, and LinkedIn using local JSON files.

---

## 🧠 Epic 1: Setup & Data Prep

### 🧩 User Story:
As a developer, I want a clean project folder and sample data ready so I can start building fast.

#### ✅ Tasks
- [ ] Create project folder `post_collector/`
- [ ] Add sample files:
  - [ ] `twitter.json`
  - [ ] `substack.json`
  - [ ] `linkedin_saves.json`
- [ ] Create `app.py` as the main Streamlit script

---

## 🔄 Epic 2: Load + Normalize Data

### 🧩 User Story:
As a user, I want to see all my posts from different platforms in one view, regardless of source.

#### ✅ Tasks
- [ ] Load all 3 JSON files into Python
- [ ] Normalize structure:
  - `id`, `platform`, `title`, `summary`, `url`, `author`, `tags`, `note`, `saved_at`
- [ ] Combine all into a single list for rendering

---

## 🖥️ Epic 3: Post Display UI

### 🧩 User Story:
As a user, I want a clean UI where I can view all posts with their platform, title, and link.

#### ✅ Tasks
- [ ] Add Streamlit UI with search bar
- [ ] Loop over all posts
- [ ] Display each post in an `st.expander` or `st.card`-like format:
  - Title (clickable link)
  - Platform badge
  - Summary/preview
  - Tags display
  - Note display

---

## 🏷️ Epic 4: Tagging + Notes Editing

### 🧩 User Story:
As a user, I want to tag and annotate each post so I can organize my saved content meaningfully.

#### ✅ Tasks
- [ ] For each post, show `st.text_input` or tag input
- [ ] Let user edit `note` and `tags`
- [ ] Keep edits in memory
- [ ] Add "Save All" button

---

## 💾 Epic 5: Save & Export

### 🧩 User Story:
As a user, I want to save my edits and optionally export them for use elsewhere.

#### ✅ Tasks
- [ ] Add function to group posts back by platform
- [ ] Write changes to:
  - `twitter.json`
  - `substack.json`
  - `linkedin_saves.json`
- [ ] Optional: Add button to export all posts as `.md` or `.json`

---

## 🧪 Epic 6: Final Testing

### 🧩 User Story:
As a user, I want to ensure everything runs correctly and that no data is lost.

#### ✅ Tasks
- [ ] Test UI for 10+ posts
- [ ] Confirm save button rewrites all 3 files
- [ ] Validate tag and note persistency

---

## 🛑 Out of Scope (For Now)

- Twitter API fetch
- LinkedIn scraping
- Multi-user support
- Auth or login
- DB integration

---
```

Would you like this bundled with:

* A starter `app.py` file?
* JSON templates for each platform?
* Markdown export function?

Just say the word and I’ll generate it.
