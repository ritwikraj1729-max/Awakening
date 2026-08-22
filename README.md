# Awakening — Study Tracker

A premium, gamified study-tracking web application inspired by a **system/awakening interface**. It turns subjects into **Domains**, chapters into progression paths, and study milestones into levels.

The entire application runs in the browser and stores user data locally using `localStorage`.

---

## ✦ Features

### ◈ Dashboard

The Home page provides a quick overview of your study progress:

* Current level
* Overall completion percentage
* Number of Domains
* Number of Chapters
* Current Quest
* Recent activity
* Study streak

The **Current Quest** automatically points toward the most recently opened chapter so you can quickly resume where you left off.

---

### ✦ Domains

Subjects are represented as **Domains**.

Each Domain contains:

* Custom symbol
* Name
* Chapters
* Custom roadmap
* Overall completion percentage
* Visual progress bar

Domains can be:

* Created
* Edited
* Searched
* Deleted

Example Domains:

```text
Mathematics
Physics
Computer Science
Chemistry
Biology
```

---

## ⬡ Chapter Progression

Every Domain contains Chapters.

Each Chapter follows its Domain's roadmap.

The default roadmap is:

```text
Notes
Concepts
Examples
Practice
Revision
Quiz
```

Each roadmap stage behaves like a progression level.

A stage can be:

* 🔒 Locked
* ▶ Active
* ✓ Completed

Stages must generally be completed sequentially, creating a simple progression system.

---

## ✦ Roadmap System

Every Domain can have its own custom roadmap.

For example:

```text
Learn
Understand
Solve Examples
Practice
Advanced Problems
Revision
Test
```

Roadmaps can be:

* Edited
* Extended
* Reduced
* Renamed
* Reordered through editing

When a roadmap changes, the existing chapters are synchronized with the new roadmap.

---

## ⬡ Player Status

The Statistics page provides a broader overview of progress.

It displays:

* Total Domains
* Total Chapters
* Completed levels
* Remaining levels
* Overall completion
* Domain mastery
* Completion overview
* Top Domains
* Player profile

Two charts are generated using **Chart.js**:

1. Domain Mastery
2. Completed vs Remaining

---

## ✦ Level System

The application converts overall completion into a progression level.

The current implementation uses completion percentage:

```text
0–9%     → LV 1
10–19%   → LV 2
20–29%   → LV 3
30–39%   → LV 4
40–49%   → LV 5
50–59%   → LV 6
60–69%   → LV 7
70–79%   → LV 8
80–89%   → LV 9
90–99%   → LV 10
100%     → GOD
```

When a new level is reached, the application displays a **Level Up** overlay.

At 100% completion:

```text
ALL DOMAINS CLEARED
GOD
```

---

## 🔥 Streak System

The tracker calculates a study streak based on the dates Chapters were opened.

The system checks:

* Today
* Yesterday
* Previous consecutive days

The current streak is displayed in the HUD using the 🔥 indicator.

---

## 🦊 Player Profile

The player can customize:

* Name
* Avatar

Available avatars include:

```text
🦊 🐼 🦁 🐨 🐯
🦄 🐲 👑 🌟 💎
```

The profile appears on the Statistics page and in the HUD.

---

## ✦ Recent Activity

The application records the most recently opened Chapters.

Recent activity is used for:

* The Recent Activity section
* Current Quest
* Resume Quest functionality

Selecting a recent Chapter opens its progression interface.

---

## ⚡ Visual Design

The interface uses a dark **purple glassmorphism** aesthetic.

### Design characteristics

* Dark purple background
* Translucent glass cards
* Frosted-glass blur
* Subtle borders
* Soft purple glow
* Minimal shadows
* Cinzel headings
* Cormorant Garamond body text
* Smooth hover animations
* Subtle grid background
* Vertical chapter progression path

### Typography

The application loads:

* **Cinzel** — headings and system-style UI
* **Cormorant Garamond** — body text and controls

---

## 🧭 Navigation

The sidebar contains four primary sections:

```text
◈ Home
✦ Domains
⬡ Status
⚙ Settings
```

The sidebar expands when hovered on desktop.

On smaller screens it remains compact.

---

## ⚙ Data Management

All study data is stored locally in the browser.

Storage key:

```text
loopers_data_v5
```

The application does not require a backend database.

### Export

Users can export their complete tracker data as a JSON file.

### Import

JSON backups can be restored from:

* A JSON file
* Pasted JSON text

### Copy Backup

The complete JSON state can also be copied directly to the clipboard.

### Reset

The Settings page provides a complete data reset option.

---

## 💾 Data Structure

The application stores data approximately in the following structure:

```text
data
├── profile
│   ├── name
│   └── emoji
│
├── subjects
│   ├── id
│   ├── name
│   ├── symbol
│   ├── roadmap
│   ├── createdAt
│   └── chapters
│       ├── id
│       ├── name
│       ├── lastOpened
│       └── levels
│           ├── id
│           ├── name
│           └── completed
│
└── settings
```

---

## 🛠 Technology

The project is a client-side web application built with:

* HTML5
* CSS3
* Vanilla JavaScript
* `localStorage`
* Chart.js
* Google Fonts

External libraries are loaded through CDN links.

### Chart.js

Used for the Statistics page charts.

### Google Fonts

Used for the application's typography.

---

## 🚀 Running the Project

No build system is required.

Simply open the HTML file in a modern web browser.

```text
index.html
```

The application should work directly in the browser.

For the best experience, use a modern Chromium-based browser, Firefox, Safari, or another browser with support for:

* JavaScript
* localStorage
* CSS backdrop filters
* Canvas
* Clipboard API

---

## 📁 Project Structure

The current version is designed as a single-file application:

```text
Awakening/
└── index.html
```

The HTML file contains:

```text
HTML
├── Application structure
├── Modals
└── Canvas

CSS
├── Theme
├── Glass UI
├── Layout
├── Responsive styles
└── Animations

JavaScript
├── Data management
├── Navigation
├── Domain CRUD
├── Chapter CRUD
├── Roadmap system
├── Progress system
├── Level system
├── Streak system
├── Statistics
├── Charts
├── Import/export
└── UI interactions
```

---

## 🔄 Application Flow

The basic progression is:

```text
Create Domain
      ↓
Create Chapter
      ↓
Open Chapter
      ↓
Complete Roadmap Levels
      ↓
Chapter Progress Increases
      ↓
Domain Progress Increases
      ↓
Overall Completion Increases
      ↓
Player Level Increases
      ↓
100% → GOD
```

---

## 🎮 Design Philosophy

Awakening is designed around a simple principle:

> **Turn studying into visible progression.**

Instead of relying on complicated game mechanics, the application focuses on:

* Clear progress
* Sequential milestones
* Visual feedback
* Simple statistics
* Custom study roadmaps
* A motivating system-like interface

The progression system intentionally avoids unnecessary complexity such as XP calculations.

---

## 📌 Current Limitations

This version is entirely client-side.

Therefore:

* Data is stored only in the current browser.
* There is no account system.
* There is no cloud synchronization.
* Data can be lost if browser storage is manually cleared.
* Import/export should be used for backups.
* Study time is not currently tracked.
* There is no server-side authentication.
* There is no multi-device synchronization.

---

## 🔮 Possible Future Improvements

Potential future additions include:

* Study timer
* Daily objectives
* Calendar-based study history
* Better streak tracking
* Detailed chapter notes
* Tasks inside roadmap levels
* Drag-and-drop roadmap ordering
* More detailed analytics
* Keyboard shortcuts
* Mobile navigation improvements
* Cloud synchronization
* User accounts
* PWA/offline support
* More advanced progression mechanics
* Custom themes

---

## 🔐 Privacy

Awakening currently stores study information locally in the browser through `localStorage`.

No personal study data is intentionally sent to a backend by the application itself.

External resources such as Google Fonts and Chart.js are loaded from their respective CDNs.

---

## ✦ Philosophy

**Awakening is not meant to make studying complicated.**

The goal is to make progress tangible.

Every Chapter is a path.

Every roadmap step is a milestone.

Every completed milestone moves the system forward.

**Study → Progress → Mastery → Awakening.**
