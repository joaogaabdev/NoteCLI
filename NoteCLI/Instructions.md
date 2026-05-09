# 📘 Instructions — Zettel Terminal Knowledge System

Welcome to your terminal-based knowledge system built on **Zettelkasten** and **Maps of Content (MOCs)** principles.

This guide will help you create, organize, and navigate your notes efficiently.

---

## 🧠 Core Concepts

### 1. Atomic Notes (Zettelkasten)

* Each note should represent **one idea only**
* Keep notes **small, clear, and self-contained**
* Use unique IDs (timestamp-based)

---

### 2. Links Between Notes

* Use double brackets to link notes:

```
[[202604231030]]
[[software_engineering]]
```

* Links create a **network of knowledge**, not a hierarchy

---

### 3. Maps of Content (MOCs)

* MOCs are **index notes** that organize topics
* They act as entry points to navigate your knowledge

---

## 📁 Project Structure

```
zettel/
├── notes/        # Atomic notes
├── mocs/         # Maps of Content
├── tags/         # Tag-based grouping (optional)
└── index.md      # Main entry point
```

---

## ✍️ Creating a New Note

Use the terminal:

```bash
nano notes/$(date +%Y%m%d%H%M).md
```

---

## 📝 Note Template

```
# Title

ID: YYYYMMDDHHMM  
Tags: #tag1 #tag2

## Content
Write your idea clearly and concisely.

## Links
- [[related_note_id]]
- [[topic_or_moc]]
```

---

## 🔍 Searching Notes

Find content using:

```bash
rg "keyword"
```

Or search backlinks:

```bash
rg "NOTE_ID"
```

---

## 🔗 Backlinks Concept

Backlinks are **notes that reference the current note**.

Example:

If note A contains:

```
[[B]]
```

Then note B has a **backlink from A**.

---

## 📖 Viewing Notes (Rendered)

Use a Markdown viewer in terminal:

```bash
glow notes/your_note.md
```

---

## 🔄 Git Workflow (Sync with GitHub)

```bash
git add .
git commit -m "add new note"
git push
```

---

## ⚙️ Best Practices

* Write **frequently**, refine later
* Prefer **linking over organizing**
* Avoid large, monolithic notes
* Use MOCs to structure knowledge when needed
* Keep filenames as IDs (not titles)

---

## 🚀 Advanced Ideas (Optional)

* Build a CLI tool to:

  * Create notes automatically
  * Parse `[[links]]`
  * Generate backlinks
* Export graph visualization
* Implement ranking or recommendation system

---

## 💡 Philosophy

> Knowledge is not a tree. It is a graph.

Your goal is not to store information —
but to **connect ideas over time**.

---

## 🧩 Tips

* Use `nano` or `vim` for writing
* Use `glow` for reading
* Use `git` for versioning
* Use your brain for connecting dots 😉

---

## 📌 Final Note

Start simple.
Consistency beats complexity.

Your system will evolve as your knowledge grows.

---
