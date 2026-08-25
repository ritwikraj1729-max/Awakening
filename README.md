# ◈ Loopers — Study Tracker

**Loopers** is a minimal, Notion-inspired study tracker built with vanilla HTML, CSS, and JavaScript. It helps you organize subjects into chapters, track progress through customizable learning roadmaps, and maintain daily streaks — all stored locally in your browser.

---

## ✨ Features

### 🗂 Subject Management
- Create, edit, and delete subjects
- Assign custom symbols (emojis) and color themes
- 5 built-in color themes: **Blue, Green, Violet, Amber, Coral**

### 📚 Chapter & Roadmap System
- Add chapters to any subject
- Define a **roadmap** (learning steps) per subject — e.g., *Notes → Concepts → Examples → Practice → Revision → Quiz*
- Every chapter follows the subject's roadmap with GitHub-style toggle squares
- Inline rename chapters directly in the table
- **Drag-and-drop** chapter reordering

### 📊 Statistics Dashboard
- Overall completion percentage
- Subject-wise mastery doughnut chart
- Completed vs. remaining levels bar chart
- Top subjects ranking with progress bars
- Day streak counter based on chapter activity

### 🏠 Home Dashboard
- Quick stats: completion %, subjects, chapters, streak
- **Current Quest** — your most recently opened chapter
- Recent activity feed with one-click resume

### 👤 Profile System
- Custom display name and avatar emoji
- XP-style completion bar
- 10+ avatar options to choose from

### 💾 Data & Settings
- **Auto-save** to `localStorage`
- **Export** as JSON file
- **Import** from JSON file or pasted text
- **Copy backup** to clipboard
- **One-click reset** with confirmation

---

## 🚀 Getting Started

### Option 1: Direct Use
Open `index.html` in any modern browser. Sample data is auto-seeded on first run so you can explore immediately.

### Option 2: Local Server (Optional)
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .
```
Then visit `http://localhost:8000`.

> No build tools, dependencies, or installation required — just HTML, CSS, and JS.

---

## 🎯 How to Use

### Creating Your First Subject
1. Navigate to **Subjects** in the sidebar
2. Click **+ New**
3. Choose a **symbol** (e.g., `◈` for math, `✦` for physics)
4. Enter a **name**
5. Pick a **color theme**
6. Customize the **roadmap** (one step per line)
7. Click **Create**

### Adding Chapters
1. Open a subject from the Subjects grid
2. Click **+ Chapter**
3. Enter a chapter name (e.g., "Algebra", "Mechanics")
4. The chapter automatically gets a row with toggle squares for each roadmap step

### Tracking Progress
- **Click any square** in the chapter table to toggle completion
- The chapter progress bar updates in real time
- Subject completion % and stats refresh instantly

### Reordering Chapters
- **Grab the `⋮⋮` handle** on any chapter row
- **Drag** it to a new position
- Release to save the new order

### Renaming Chapters
- **Click on a chapter name** in the table
- Type the new name
- Press `Enter` to save or `Esc` to cancel

### Editing Roadmaps
1. Open a subject
2. Click **Roadmap**
3. Add, remove, or reorder steps
4. Click **Save** — existing chapters are automatically synced to the new roadmap

### Using Statistics
- View **overall completion** and **subject mastery**
- Check **top subjects** by completion %
- Track your **daily streak** on the home dashboard

### Backing Up Data
- Go to **Settings**
- Click **Export** to download a JSON file
- Or click **Copy Text** to copy JSON to clipboard
- Restore via **Import** (file) or **Import Text** (paste JSON)

---

## 📁 Data Structure

All data is stored in `localStorage` under the key `loopers_data_v5`. The shape looks like:

```json
{
  "profile": {
    "name": "Player",
    "emoji": "🦊"
  },
  "subjects": [
    {
      "id": "s1",
      "name": "Mathematics",
      "symbol": "◈",
      "color": "violet",
      "roadmap": ["Notes", "Concepts", "Examples", "Practice", "Revision", "Quiz"],
      "chapters": [
        {
          "id": "c1a",
          "name": "Algebra",
          "levels": [
            { "id": "l1a0", "name": "Notes", "completed": true },
            { "id": "l1a1", "name": "Concepts", "completed": false }
          ],
          "lastOpened": 1738560000000
        }
      ],
      "createdAt": 1738560000000
    }
  ],
  "settings": {}
}
```

| Field | Type | Description |
|-------|------|-------------|
| `subjects[].roadmap` | `string[]` | Learning steps shared across all chapters |
| `chapters[].levels` | `object[]` | One entry per roadmap step with completion state |
| `chapters[].lastOpened` | `number` | Unix timestamp for streak/recent tracking |

---

## 🎨 Color Themes

| Theme | Hex | Best For |
|-------|-----|----------|
| 🔵 Blue | `#3b82f6` | Sciences, Physics |
| 🟢 Green | `#22c55e` | CS, Biology |
| 🟣 Violet | `#8b5cf6` | Math, Logic |
| 🟠 Amber | `#f59e0b` | Languages, Humanities |
| 🔴 Coral | `#ff6b6b` | Literature, Arts |

---

## 📈 Roadmap Workflow

The roadmap system is designed around a **mastery loop**:

```
Notes → Concepts → Examples → Practice → Revision → Quiz
```

- **Notes** — Gather raw material
- **Concepts** — Understand core ideas
- **Examples** — Work through worked solutions
- **Practice** — Solve problems independently
- **Revision** — Review and consolidate
- **Quiz** — Test yourself

You can customize this to fit any subject. Common alternatives:

- **Language**: `Vocabulary → Grammar → Reading → Listening → Speaking → Writing`
- **History**: `Timeline → Key Events → Analysis → Sources → Essay → Review`
- **Programming**: `Tutorial → Setup → Core Syntax → Projects → Debugging → Review`

---

## 🧮 Streak Calculation

The streak counts **consecutive days** where at least one chapter was opened or updated. The logic:

1. Collect all `lastOpened` timestamps from every chapter
2. Normalize to local midnight
3. Check if today or yesterday has activity
4. Count backward from the most recent active day

> Opening a subject or toggling a completion square updates `lastOpened`.

---

## 💡 Tips & Best Practices

### For Students
- **Keep roadmaps short** (4–7 steps) for manageable tracking
- **Update streaks daily** — even a 30-second review counts
- **Use symbols** that are visually distinct (`◈` vs `✦` vs `◆`)

### For Power Users
- **Export regularly** — data is local-only
- **Import JSON text** to sync across browsers/devices
- **Custom roadmaps** work great for non-academic tracking (fitness, habits, projects)

### Performance Notes
- Designed to handle **hundreds of subjects and chapters** smoothly
- Chart.js is loaded from CDN (requires internet for statistics page)

---

## 🧩 Tech Stack

| Technology | Role |
|-----------|------|
| HTML5 | Structure |
| CSS3 (custom properties) | Notion-style dark theme |
| Vanilla JavaScript | Logic, state management, localStorage |
| Chart.js 4.4.0 (CDN) | Statistics visualizations |

No frameworks, no build tools, no server required.

---

## 📦 Project Structure

```
loopers/
├── index.html          # Single-file application
│   ├── CSS (embedded)  # Notion dark theme
│   └── JS (embedded)   # Full app logic
└── README.md           # This file
```

---

## 🔧 Customization

### Adding New Color Themes
In the `<script>` section, find the `THEMES` object:

```js
const THEMES = {
    blue:   { label: 'Blue',   hex: '#3b82f6' },
    green:  { label: 'Green',  hex: '#22c55e' },
    violet: { label: 'Violet', hex: '#8b5cf6' },
    amber:  { label: 'Amber',  hex: '#f59e0b' },
    coral:  { label: 'Coral',  hex: '#ff6b6b' }
};
```

Add a new entry with a unique id, label, and hex code. The theme will automatically appear in the color picker and apply throughout the UI.

### Changing Default Roadmap
Find `DEFAULT_ROADMAP`:

```js
const DEFAULT_ROADMAP = ['Notes', 'Concepts', 'Examples', 'Practice', 'Revision', 'Quiz'];
```

Modify the array to change the default for new subjects.

---

## ❓ FAQ

### Where is my data stored?
In your browser's `localStorage`. Clearing browser data will erase it — **export regularly**.

### Can I sync across devices?
Not natively. Use **Export → Import Text** to manually transfer data between devices.

### What happens when I edit a roadmap?
Existing chapters are synced automatically. Levels that match by index keep their completion state; new steps are added as incomplete.

### Does it work offline?
Yes, except the **Statistics** page charts (Chart.js loads from CDN). Everything else works fully offline.

### How do I reset my streak?
There's no manual streak reset. The streak naturally resets if you go a full day without activity.

---

## 🐛 Known Limitations

- Data is **local-only** — no cloud sync
- No undo for chapter deletion (subject deletion has confirmation)
- Statistics charts require internet for CDN
- Mobile experience is functional but optimized for desktop

---

## 📄 License

MIT — free to use, modify, and distribute.

---

## 🙏 Acknowledgements

- **Notion** — UI/UX inspiration
- **Chart.js** — Charts on the Statistics page
- **GitHub** — Contribution-square interaction pattern

---

**Happy learning!** ◈
```

This README covers:

| Section | Purpose |
|---------|---------|
| **Overview & Features** | What the app does at a glance |
| **Getting Started** | Zero-setup instructions |
| **How to Use** | Step-by-step workflows for every feature |
| **Data Structure** | JSON schema with field descriptions |
| **Color Themes** | Visual reference table |
| **Roadmap Workflow** | The pedagogical model behind the tracker |
| **Streak Calculation** | How the algorithm works |
| **Tips & Best Practices** | Power user guidance |
| **Tech Stack** | What it's built with |
| **Customization** | How to extend the app |
| **FAQ** | Common questions answered |
| **Known Limitations** | Honest caveats |

The README assumes the reader has just received this single-file app and wants to start using it productively — whether they're a student tracking coursework, a developer studying for interviews, or anyone running a self-paced learning program.
