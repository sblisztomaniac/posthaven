### ⚡ `sprintplan.md`: 90-Min Sprint – Dynamic Post Collector MVP

````markdown
# ⏱️ Sprint Plan: Post Collector MVP (1.5-Hour Build)

## 🎯 Goal

Build a **local Streamlit app** that:
- Dynamically fetches liked posts from **X.com** and articles from **Substack RSS**
- Loads saved posts from **LinkedIn (local JSON)**
- Displays them in a unified view
- Lets user **tag + annotate** each post
- Saves those edits locally

---

## ⏳ Total Time: 1.5 Hours (Solo Developer)

---

### ✅ Phase 1: Setup & Config (10 min)

- [ ] Create project folder: `post_collector/`
- [ ] Add `.env` for X.com Bearer Token + User ID
- [ ] Create `feeds.json` with sample Substack RSS URLs
- [ ] Create `linkedin_saves.json` with 1–2 entries (mock)
- [ ] Install: `streamlit`, `feedparser`, `requests`, `dotenv`

---

### 🔌 Phase 2: Live Fetch (25 min)

- [ ] **X.com**: `fetch_x_likes()` using Bearer Token  
  - Fetch latest 10–20 liked tweets
- [ ] **Substack**: `fetch_substack_posts()` from RSS URLs  
  - Use `feedparser` to extract title, summary, link
- [ ] **LinkedIn**: Load `linkedin_saves.json` as fallback

- [ ] Normalize all into:
```python
{
  "id", "platform", "title", "author",
  "url", "summary", "saved_at"
}
````

---

### 🖼️ Phase 3: UI Display (25 min)

* [ ] Use `st.text_input()` for search
* [ ] Loop through posts, display as `st.expander()`:

  * Title (clickable), platform badge, summary
  * Author, saved date
* [ ] Add `st.text_input()` for tags
* [ ] Add `st.text_area()` for notes

---

### 💾 Phase 4: Save Edits (20 min)

* [ ] Load/edit `local_notes.json`

  * Tags/notes mapped by `post_id`
* [ ] Update memory on change
* [ ] Add `Save All Changes` button

  * Writes updated tags/notes to `local_notes.json`

---

### 🧪 Phase 5: Testing & Polish (10 min)

* [ ] Test fetching, editing, saving
* [ ] Handle errors:

  * If X.com API fails → show Streamlit warning
  * If RSS fails → skip feed
* [ ] Confirm `local_notes.json` loads on next run

---

## ✅ Success =

* Live data from X and Substack shown
* Editable tags + notes per post
* Local save works
* App runs with `streamlit run app.py`

---

## ❌ Skip for Now

* Multi-tag UI (chips, dropdowns)
* Markdown export
* LinkedIn automation
* GPT summaries
* Platform filter

---

## 🗂 Minimal Folder Layout

```
post_collector/
├── app.py
├── .env
├── feeds.json
├── linkedin_saves.json
├── local_notes.json
```

