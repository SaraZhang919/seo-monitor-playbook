# SEO Monitoring Playbook Dashboard

A personal, self-hosted daily SEO checklist for AI site owners — with a full "Why → Signals → Actions" playbook for every metric. Runs entirely in the browser with no backend required.

---

## What this is

A single-page HTML checklist you open every day to run through your SEO monitoring routine. It covers:

- **Daily** checks — traffic, technical health, backlinks, indexing (13 items)
- **Weekly** checks — rankings, technical audit, content performance, link profile (16 items)
- **Monthly** checks — full audit, strategy, reporting (16 items)

Every item is expandable to reveal:
1. **Why** this metric matters
2. **Key signals & thresholds** — exact numbers to watch
3. **Action playbook** — what to do when a signal fires

Progress is saved automatically in `localStorage` and resets each morning. Dark mode is supported out of the box via `prefers-color-scheme`.

---

## File structure

```
/
├── index.html     ← The entire app (single file, self-contained)
├── README.md      ← This file: how to deploy and customize
├── CONTEXT.md     ← The strategic rationale and design decisions
└── CHANGELOG.md   ← Version history of your edits
```

---

## Deploy to Vercel via GitHub (5 minutes)

### 1. Create a GitHub repo

```bash
git init seo-dashboard
cd seo-dashboard
cp /path/to/index.html .
cp /path/to/README.md .
cp /path/to/CONTEXT.md .
cp /path/to/CHANGELOG.md .
git add .
git commit -m "v1.0.0 initial dashboard"
git remote add origin https://github.com/YOUR_USERNAME/seo-dashboard.git
git push -u origin main
```

### 2. Deploy to Vercel

1. Go to [vercel.com](https://vercel.com) → **Add New Project**
2. Import your `seo-dashboard` GitHub repo
3. Vercel detects it as a static site automatically — no configuration needed
4. Click **Deploy**
5. Your dashboard is live at `https://seo-dashboard-XXXX.vercel.app`

### 3. Set a custom domain (optional)

In Vercel → Settings → Domains → Add `seo.yourdomain.com` → follow DNS instructions.

### Updating the dashboard

1. Edit `index.html` locally (or directly on GitHub)
2. Commit and push — Vercel auto-deploys in under 30 seconds
3. Add a new entry in `CHANGELOG.md` before pushing

---

## Accessing on mobile

Bookmark the Vercel URL to your phone's home screen:

- **iOS**: Open in Safari → Share → "Add to Home Screen"
- **Android**: Open in Chrome → Menu → "Add to Home screen"

The dashboard is mobile-responsive and uses your system's dark/light mode preference.

---

## How to add a new checklist item

All checklist data lives in the `DATA` object near the top of `index.html`, starting around line 180. The structure is:

```js
// Each tab (d = daily, w = weekly, m = monthly) contains categories
d: [
  {
    icon: "ti-chart-bar",        // Tabler icon class name (see tabler.io/icons)
    title: "Category name",      // Shown in the collapsible category header
    items: [
      {
        t:       "Short label shown in the checklist",
        b:       "c",            // Badge: "c" critical | "w" watch | "o" opportunity | "a" AI-specific
        tool:    "GA4 → Acquisition → Organic Search",  // Where to find this data
        why:     "Why this metric matters...",
        signals: [
          "Threshold 1: what the number means",
          "Threshold 2: when to be concerned",
        ],
        actions: [
          "If X happens: do Y",
          "If Z happens: do W",
        ]
      }
    ]
  }
]
```

To add a new item, copy an existing item block and paste it into the appropriate category, then update all six fields.

---

## How to add a new category

Add a new object to the `d`, `w`, or `m` array in `DATA`:

```js
{
  icon:  "ti-robot",        // pick from tabler.io/icons
  title: "AI model monitoring",
  items: [ /* your items here */ ]
}
```

Tabler icons are loaded from CDN. Browse all 5,800+ icons at [tabler.io/icons](https://tabler.io/icons) — use the outline version name (e.g., `ti-robot`, not `ti-robot-filled`).

---

## How to change a badge type

| Badge value | Colour | Meaning |
|---|---|---|
| `"c"` | Red | Critical — fix/check immediately, high impact |
| `"w"` | Amber | Watch — monitor closely, could become critical |
| `"o"` | Green | Opportunity — ranking gain available |
| `"a"` | Blue | AI-specific — disproportionately important for AI sites |

---

## How state persistence works

The dashboard uses `localStorage` to save your checked state. The key is `seo-dash-v1-YYYY-MM-DD`, which means:

- **Progress is saved** across browser refreshes and tab closes during the same day
- **Progress resets automatically** each morning when the date changes — no manual reset needed
- The "Reset tab" button manually clears the current tab's state for the current day

If you want to change the key prefix (e.g., after a major data update where old state would be misleading), update `STORAGE_KEY` near line 400:

```js
const STORAGE_KEY = `seo-dash-v2-${TODAY}`;  // bump v1 → v2
```

---

## Customization quick reference

| What you want to change | Where to find it |
|---|---|
| Add / edit a checklist item | `DATA` object → find the right tab and category |
| Change badge priority | Item's `b` field |
| Change the tool reference | Item's `tool` field |
| Change the expand detail content | Item's `why`, `signals`, `actions` fields |
| Change colours / dark mode | CSS `:root` variables at the top of `<style>` |
| Change the page title | `<title>` tag in `<head>` |
| Change fonts | `--font` variable in `:root` |
| Move an item to a different frequency tab | Cut and paste the item object to the `d`, `w`, or `m` array |
