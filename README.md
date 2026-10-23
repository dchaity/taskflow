# 🗂️ TaskFlow — Professional Productivity Web App

**TaskFlow** is a modern, fully responsive task management application built with pure **HTML5, CSS3, and Vanilla JavaScript (ES6+)**. It helps users organize their daily tasks with categories, due dates, priorities, and progress tracking — all stored locally in the browser with no backend required. Designed with a clean, SaaS-inspired interface and built with accessibility, performance, and mobile-first responsiveness in mind.

---

## 🌐 Live Demo

🚀 **[Visit TaskFlow — Live Website](https://dchaity.github.io/taskflow/)**
- **GitHub Repository:** [https://github.com/dchaity/taskflow](https://github.com/dchaity/taskflow)

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Key Features](#-key-features)
- [User Roles](#-user-roles)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [How It Works](#-how-it-works)
- [Security and Privacy](#-security-and-privacy)
- [Deployment](#-deployment)
- [Future Improvements](#-future-improvements)
- [Contributing](#-contributing)
- [Contact](#-contact)
- [License](#-license)

---

## 🎯 About the Project

Staying organized is one of the biggest challenges in modern life. Many productivity tools are bloated, require accounts, or depend on cloud services. **TaskFlow** takes a different approach: a lightweight, instant-loading productivity dashboard that runs entirely in the browser.

TaskFlow aims to address these challenges by providing a centralized, zero-dependency workspace where:

- Users can create and manage tasks with titles, descriptions, categories, and due dates.
- Tasks persist across page reloads using the browser's `localStorage` API.
- Users can filter, search, sort, and prioritize tasks without ever touching a server.
- Dashboard statistics and progress indicators update in real time.
- A polished light/dark theme makes the app comfortable for any time of day.

### 🎨 Design Philosophy

- **Theme:** Soft neutrals with a single blue accent (`#3b82f6`)
- **Interface:** Modern, minimalist, and responsive — inspired by leading SaaS tools
- **Accessibility:** Semantic HTML, ARIA attributes, keyboard navigation, reduced-motion support
- **User experience:** Instant feedback, toast notifications, confirmation dialogs, and empty states
- **Target audience:** Students, professionals, freelancers, and anyone who wants a fast, private task manager

---

## ✨ Key Features

### 👤 Core Task Management

- ✅ **Create tasks** with title, description, category, and optional due date
- 📝 **Edit existing tasks** through a modal dialog
- 🗑️ **Delete tasks** with a confirmation step to prevent accidental loss
- ☑️ **Toggle completion** with smooth visual feedback
- 🏷️ **Categorize tasks** (Work, Personal, Study, Other) with color-coded badges
- 📅 **Set due dates** with automatic overdue detection

### 🔎 Search and Discovery

- **Filter by status:** All, Active, Completed, Overdue
- **Live search** across task titles and descriptions
- **Category filtering** via dropdown
- **Sorting options:** Newest, Oldest, Due date ascending/descending
- **Combined filters:** search + category + status + sort all work together without modifying source data

### 📊 Dashboard and Productivity Summary

- **Live statistics:** Total, Active, Completed, and Overdue task counts
- **Animated progress bar** showing overall completion percentage
- All metrics update **instantly** whenever tasks change

### 📱 Responsive User Interface

- **Mobile-first** layout using CSS Grid and Flexbox
- **Sidebar navigation** on desktop → **drawer menu** on mobile
- Optimized for **320px to 1440px+** viewports
- **No horizontal scrolling** at any supported width
- Touch targets meeting **44 × 44px** minimum
- Works in **portrait and landscape** orientations

### ♿ Accessibility

- Semantic HTML5 structure with landmarks
- All form controls have associated `<label>` elements
- Icon-only buttons have descriptive `aria-label`s
- Full **keyboard navigation** with visible focus indicators
- `Escape` key closes modals and the mobile drawer
- Modals use `role="dialog"` and `aria-modal="true"`
- Animations respect `prefers-reduced-motion`
- WCAG AA-compliant color contrast

### 💾 Data Persistence

- All tasks saved to **`localStorage`** — no backend or database needed
- Data survives page reloads and browser restarts
- Malformed or corrupted storage data handled gracefully
- **XSS protection** via safe DOM rendering

---

## 🛠️ Technology Stack

### 🎨 Frontend

| Technology | Purpose |
|---|---|
| HTML5 | Semantic, accessible page structure |
| CSS3 | Flexbox, Grid, custom properties, media queries, transitions |
| Vanilla JavaScript (ES6+) | Application logic, state management, DOM manipulation |
| localStorage API | Persistent client-side task storage |
| Google Fonts | Inter and DM Sans for professional typography |
| Lucide Icons | Lightweight, consistent SVG icon set |

**Important:** TaskFlow is intentionally built **without any framework** — no React, Vue, Angular, Tailwind, or build tools. It runs directly in the browser from a single HTML file, making it portable, fast, and easy to audit.

### ⚙️ Development and Deployment

| Technology | Purpose |
|---|---|
| Git | Version control |
| GitHub | Source code hosting |
| GitHub Pages | Static site deployment |
| VS Code (optional) | Code editor with Live Server extension |

---

## 📁 Project Structure

```text
taskflow/
├── index.html              # Main HTML — structure, styles, and logic (single-file build)
├── README.md               # Project documentation
└── LICENSE                 # MIT License (add before publishing)
Optional split structure (for scaling):

text
taskflow/
├── index.html              # Semantic markup only
├── css/
│   └── style.css           # All styles, theme variables, media queries
├── js/
│   └── app.js              # State, CRUD, rendering, event handlers
├── README.md
└── LICENSE
🚀 Getting Started
Prerequisites
Install the following before running the project:

Any modern web browser (Chrome, Firefox, Safari, Edge)

Git (for cloning)

Optional: Python 3 or Node.js (for a local development server)

Optional: VS Code with the Live Server extension

1. Clone the Repository
bash
git clone https://github.com/dchaity/taskflow.git
cd taskflow
2. Open the App
Option A — Direct file open:
Double-click index.html to open it in your browser. (Note: Fonts and icons may not load correctly from file:// in some browsers).

Option B — Local development server (recommended):

bash
# Python 3
python -m http.server 8000

# Node.js
npx serve .
Then open http://localhost:8000 in your browser.

3. No Build Step Required
TaskFlow has zero dependencies and no build process. There is nothing to install beyond cloning the repository.

🔐 Environment Variables
TaskFlow does not use any environment variables. It has no backend, database, or authentication service. All configuration is handled client-side.

There is no .env.example file required, and no secrets are stored in the repository.

📖 How It Works
Application Initialization: On page load, init() runs: Loads any saved tasks from localStorage, loads saved theme, attaches event listeners, and renders the initial UI.

Task Creation: User fills the form. addTask() validates input, creates a task object with a unique ID and timestamps, pushes it to the tasks array, saves to localStorage, and updates the UI.

Task Editing: Clicking the pencil icon opens a modal pre-filled with data. On save, editTask() updates the task object, persists changes, and re-renders.

Task Deletion: Clicking the trash icon opens a confirmation modal. On confirm, deleteTask() removes the task and re-renders.

Filtering and Search: filterTasks() builds a filtered view by applying sidebar status, tab filter, category, search query, and sort order. The source tasks array is never modified by filtering.

🔒 Security and Privacy
Even though TaskFlow runs entirely client-side, security-conscious design principles matter:

No network requests — all data stays in the user's browser.

No authentication required — no credentials to leak.

XSS protection — user-provided text is rendered via safe DOM APIs.

Storage error handling — malformed localStorage data is caught and handled gracefully.

Privacy by design — tasks never leave the device.

Note: Because data lives in localStorage, clearing browser data will delete all tasks. TaskFlow does not currently support export/backup — this is a planned future feature.

☁️ Deployment on GitHub Pages
TaskFlow is deployed as a static site using GitHub Pages.

Deployment Steps
Push your project to GitHub.

Open the repository → Settings → Pages.

Under Build and deployment:

Source: Deploy from a branch

Branch: main

Folder: / (root)

Click Save.

Wait 1–2 minutes for GitHub to build and deploy.

Your app will be live at: https://dchaity.github.io/taskflow/

🚧 Future Improvements
Drag-and-drop task reordering

Task priorities (Low / Medium / High)

Recurring tasks and habit tracking

Export / import tasks as JSON for backup

Progressive Web App (PWA) support for offline installation

Optional cloud sync via a lightweight backend

🤝 Contributing
Fork the repository.

Create a feature branch (git checkout -b feature/your-feature-name).

Make your changes and test them thoroughly.

Commit your changes (git commit -m "Add your feature description").

Push your branch (git push origin feature/your-feature-name).

Open a pull request describing your changes.

📧 Contact
Developer: Chaity Das

GitHub: dchaity

LinkedIn: Chaity Das

Repository: TaskFlow

📄 License
This project is licensed under the MIT License — free to use, modify, and distribute.
See the LICENSE file for details.

<div align="center">
🗂️ TaskFlow — Stay organized. Get things done.

Made with care by Chaity Das

GitHub Repository · LinkedIn · Live Demo

</div> ```

