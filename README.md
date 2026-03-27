# StudyLog Pro – Academic Journal & Study Tracker

A powerful, offline-first web app to log your academic life – classes, tasks, media, and notes.  
Designed for engineering students with semester‑wise routines, batch scheduling, and GitHub sync.

## ✨ Features

- **📅 Semester Routine** – Load a custom JSON timetable. The app auto‑detects your semester folder from the filename.
- **🔁 GitHub Gist Sync** – Keep your data in sync across all devices using a private GitHub Gist (free). Works in the background.
- **📝 Rich Entries** – Add multiple session titles, notes (with word count), mood, self‑rating (1–10), and review reminders.
- **✅ To‑Do Lists** – Per‑entry tasks with due dates and animated strikethrough.
- **🎥 Media Attachments** – Embed YouTube videos (click to watch) and upload any files (images, PDFs, etc.).
- **🏷️ Tags & Search** – Smart search by day, month, subject, tag (#exam) or free text.
- **📊 Statistics** – Streak, subject distribution, mood summary, task completion.
- **🎨 Themes** – Dark / light mode with a smooth transition.
- **⌨️ Keyboard‑first** – Full shortcut support (F1 help, Ctrl+K command palette, Alt+N new entry, etc.).
- **📱 Responsive** – Works on desktop and mobile (collapsible sidebar).
- **📂 LocalStorage + GitHub** – Data is always saved locally; GitHub sync works silently in the background.

## 🚀 Getting Started

### 1. Open the App
- Download the single `studylog.html` file.
- Open it in any modern browser (Chrome, Firefox, Edge, Safari).

### 2. First Run – Setup Wizard
On first launch you will be guided through:

- **Step 1 (optional)** – Connect your GitHub account to enable cloud sync.  
  You need a GitHub [Personal Access Token](https://github.com/settings/tokens) with the **gist** scope.
- **Step 2** – Load your routine JSON file (see below).  
  If you skip, the default Year 1 Semester 2 routine (CSE AIML) will be used.

> 💡 **You only need to do this once per semester.** After that, the app loads instantly from your browser and syncs in the background.

### 3. Routine File Format
Create a JSON file with the following structure (example included in the app):

```json
{
  "meta": {
    "college": "Your College",
    "routineId": "y1s2",
    "routineName": "Year 1 · Semester 2",
    "academicYear": "2026-27",
    "section": "1A",
    "branch": "CSE (AIML)",
    "batches": ["G1", "G2"]
  },
  "subjects": [
    { "id": "DSA", "label": "Data Structure and Algorithms", "color": "#4f8ef7", "bg": "rgba(79,142,247,.14)" },
    ...
  ],
  "schedule": {
    "1": [   // Monday = 1 (Sunday = 0, Monday = 1, ...)
      { "time": "10:00–11:45", "subj": "DECO_L", "room": "MB326", "batch": "G1", "note": "DECO Lab — ANG" },
      ...
    ],
    "2": [ ... ],
    ...
  }
}
```

- Days are numbered **0 = Sunday … 6 = Saturday**.
- The app uses the `routineId` to automatically determine the semester folder name (e.g., `2_Semester`).  
  This is only used for display purposes; the routine itself is stored and synced.

You can upload this file via the sidebar (**⏏ Routine** button) or during the setup wizard.

### 4. Data Persistence
- All entries are saved automatically in your browser’s `localStorage`.
- If you connect GitHub, changes are automatically pushed to your private gist.  
  When you open the app on another device, it merges data from the cloud with local storage (latest wins, deletes are respected across devices).

### 5. Log Out / Change Semester
Use the **↹ Sem** button in the sidebar to clear the current semester data and restart the setup wizard.  
Your data stays in storage – you just pick a new routine.

## ⌨️ Shortcuts

| Shortcut            | Action                     |
|---------------------|----------------------------|
| `Alt` + `N`         | New entry                  |
| `Ctrl` + `K`        | Command palette            |
| `Ctrl` + `F`        | Focus search               |
| `Alt` + `T`         | Toggle theme               |
| `Ctrl` + `Enter`    | Save entry (in modal)      |
| `Ctrl` + `Z`        | Undo delete                |
| `Ctrl` + `E`        | Export all entries as Markdown |
| `Ctrl` + `B`        | Toggle sidebar             |
| `F1`                | Help                       |
| `F10`               | Focus mode                 |
| `1` / `2` / `3` / `4` | Switch views (List/Grid/Calendar/Stats) |
| `Esc`               | Close modals / command palette |

> While editing, use `Tab` to navigate between fields.

## 🔧 Advanced Usage

### GitHub Sync
- **Token**: Only needs `gist` scope. It’s stored locally (never sent anywhere else).
- **How it works**: The app creates a private gist with two files: `studylog_data.json` (entries) and `studylog_routine.json` (routine). All changes are merged automatically.

### Import / Export
- Export entries as **Markdown** – one file per entry, ready for sharing or backup.
- Import a JSON file previously exported from the app (or any JSON with an `entries` array).

### File Attachments
- Files are stored as Base64 inside the entry (so they are also synced via GitHub).  
  Large files (>10 MB) are rejected to keep performance and sync reasonable.

### Calendar View
- Hover over a date to see a preview of entries and due tasks.
- Holidays (Saturday/Sunday) are shown with a subtle background.

### Focus Mode
- Hides toolbar, sidebar, and status bar for distraction‑free writing.

## 🛠️ Technologies
- Vanilla HTML/CSS/JS – no external frameworks.
- GitHub REST API (Gists) for sync.
- Fonts: Inter (system fallback) + Roboto Mono.
- View Transitions API for theme switching (fallback for unsupported browsers).

## 📦 Installation
No installation needed. Just save the HTML file and open it in your browser.  
For offline use, ensure you open it once while online to load the default fonts.

## 🤝 Contributing
Feel free to fork and adapt. This is a personal project designed for specific academic needs, but the structure is modular – you can easily replace the routine file format or add new fields.

## 📄 License
MIT – do whatever you want with it.

---
