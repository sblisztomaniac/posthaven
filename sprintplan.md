### 📦 `sprintplan.md`: Post Collector MVP — 1 Hour Sprint

````markdown
# 🏃‍♂️ Sprint Plan: Post Collector MVP (1-Hour Build)

## 🎯 Goal
Build a local Streamlit app that:
- Loads saved posts from `twitter.json`, `substack.json`, and `linkedin_saves.json`
- Displays them in clean cards
- Lets you add tags and notes
- Includes basic search by keyword or tag

---

## ⏱️ Total Time: 60 Minutes

### ✅ PREP (5 min)
- [ ] Create project folder: `post_collector/`
- [ ] Add `twitter.json`, `substack.json`, `linkedin_saves.json` with sample data
- [ ] Create `app.py` (main Streamlit app)

---

### 🔍 PHASE 1: Load + Merge Posts (10 min)
- [ ] Read all 3 JSON files into Python
- [ ] Normalize each into a common schema (`id`, `platform`, `title`, `summary`, `tags`, `note`, `url`, `saved_at`)
- [ ] Combine into a single `posts` list

```python
import json

def load_posts():
    with open('twitter.json') as f1, open('substack.json') as f2, open('linkedin_saves.json') as f3:
        return json.load(f1) + json.load(f2) + json.load(f3)
````

---

### 🖼️ PHASE 2: Streamlit UI (25 min)

* [ ] Setup `streamlit run app.py`
* [ ] Add search bar (`st.text_input`)
* [ ] Filter posts by keyword in title/summary/note
* [ ] Display each post in a `st.expander` or `st.card` format
* [ ] Show:

  * Title (clickable)
  * Platform badge
  * Summary
  * Tags (display as chips)
  * Notes (editable input)

---

### 🏷️ PHASE 3: Tag + Note Editing (10 min)

* [ ] Add `st.text_input` or `st.tags_input` for each post
* [ ] Let user add/edit tags and notes
* [ ] Store edits in memory
* [ ] Add a "Save All" button to overwrite all 3 JSON files

```python
if st.button("💾 Save All Changes"):
    # separate by platform and save back
```

---

### 🧪 PHASE 4: Test & Export (5 min)

* [ ] Test search + editing
* [ ] Add button to export as Markdown (optional)

---

## ✅ Files

```
post_collector/
├── app.py
├── twitter.json
├── substack.json
├── linkedin_saves.json
└── README.md
```

---

## 🚫 Out of Scope

* No DB, login, or persistent tagging history
* No automatic API fetching (use pre-fetched JSONs for now)
* No rich text editing

---

## 🏁 Done =

* Load posts from all 3 sources
* View, search, and tag them
* Edit notes
* Save changes locally

```

---

Want me to generate a working `app.py` starter file based on this plan? I can give you the whole folder setup in one go.
```
