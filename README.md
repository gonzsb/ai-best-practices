# AI Best Practices

A static editorial blog published via GitHub Pages.  
Live at: **https://gonzsb.github.io/ai-best-practices/**

---

## Stack

| File | Purpose |
|---|---|
| `index.html` | The entire site — layout, styles, JS. No build step. |
| `articles.json` | All articles. Edit this to add, update, or remove content. |

---

## Setup (one-time)

```bash
# 1. Create the repo on GitHub (do this in the browser first):
#    github.com/new → name: ai-best-practices → Public → Create repository

# 2. Clone and push
git clone https://github.com/gonzsb/ai-best-practices.git
cd ai-best-practices

# Copy your index.html and articles.json into this folder, then:
git add .
git commit -m "init: AI Best Practices blog"
git push origin main

# 3. Enable GitHub Pages
#    github.com/gonzsb/ai-best-practices → Settings → Pages
#    Source: Deploy from a branch → Branch: main → / (root) → Save
#
#    Your site will be live at:
#    https://gonzsb.github.io/ai-best-practices/
#    (takes ~60 seconds on first deploy)
```

---

## Adding a new article

Open `articles.json` and add a new object at the **top** of the array:

```json
{
  "id": "006",
  "title": "Your Article Title",
  "category": "Prompting",
  "tagline": "One or two sentences. The hook. Shown on the card.",
  "content": "Full article body.\n\nSeparate paragraphs with \\n\\n.\n\nUse **bold text** for key terms.",
  "tags": ["Tag1", "Tag2"],
  "publishedAt": "2025-06-05T10:00:00Z",
  "featured": false
}
```

Then push:

```bash
git add articles.json
git commit -m "add: Your Article Title"
git push
```

GitHub Pages rebuilds automatically. Live in ~30 seconds.

---

## Fields reference

| Field | Required | Notes |
|---|---|---|
| `id` | Yes | Unique string. Increment manually: "006", "007"… |
| `title` | Yes | Full article title |
| `category` | Yes | One of: `Prompting`, `Architecture`, `Evaluation`, `Governance` — or add your own |
| `tagline` | Yes | 1–2 sentences shown on the card and at the top of the article |
| `content` | Yes | Full text. Use `\n\n` for paragraph breaks. `**word**` for bold. |
| `tags` | No | Array of strings. Shown as small pills on the card. |
| `publishedAt` | Yes | ISO 8601 datetime: `"2025-06-05T10:00:00Z"` |
| `featured` | No | `true` = displayed as the large hero card. Only one article should be `true` at a time. |

---

## Adding a new category

Just use a new string in the `category` field — the filter bar generates automatically from the data.  
To add a custom color for it, open `index.html` and add two CSS rules following the existing pattern:

```css
/* in :root */
--cat-mynewcat: #2a3a2a;

/* color classes */
.cat-mynewcat { background: rgba(42,58,42,0.1); color: var(--cat-mynewcat); }
.visual-mynewcat { background: var(--cat-mynewcat); }
```

And add `'Mynewcat': 'mynewcat'` to the `catClass` map in the JS.

---

## Readers

Share the URL: `https://gonzsb.github.io/ai-best-practices/`  
Readers can browse, filter, and search — no login, no editing capability.  
The repo is public (required for free GitHub Pages), but only you can push changes.
