# Simple Notes Frontend (Svelte)

A modern, single-page note-taking app with a sidebar list and a markdown editor preview, styled with the Ocean Professional theme.

## Features

- Create, view, edit, and delete notes
- Local persistence using `localStorage`
- Autosave while typing (400ms debounce)
- Markdown textarea with live preview (lightweight renderer)
- Keyboard shortcuts:
  - Ctrl/Cmd+N: New note
  - Ctrl/Cmd+S: Save current note
- Responsive layout (sidebar collapses on narrow screens)
- Ocean Professional theme (primary #2563EB, secondary #F59E0B)

## Getting Started

Install dependencies and start the dev server:

```bash
npm install
npm run dev
```

Open the app at http://localhost:3000 (or the configured port).

## Environment Variables

The app reads optional environment variables via Vite:
- `VITE_API_BASE` (if a backend exists; not required for localStorage mode)
- `VITE_BACKEND_URL`, `VITE_FRONTEND_URL`, `VITE_NODE_ENV`, etc. are read if present for display or future integration.

No environment variables are required for localStorage mode; sensible defaults are used.

## Build

```bash
npm run build
npm run preview
```

## Notes about Data

Notes are saved in the browser's localStorage under the key `simple_notes_v1`. Clearing browser data will remove them.

## Accessibility

- Keyboard navigable and ARIA roles for main regions
- Focus-visible states on interactive elements
