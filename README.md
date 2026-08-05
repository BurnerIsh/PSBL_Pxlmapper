# PSBL PXLMAPPER

A browser-based LED pixelmap generator for PSBL. Builds tile-accurate test
pattern images for LED walls — zones, irregular row heights, missing-tile
staircase edges, letter/number tile labeling, and per-project overview boards.

No install, no build step, no server required. It's a single HTML file
that runs entirely in the browser.

## Using it

Open `index.html` in Chrome or Edge (recommended — enables folder export
and folder overview features via the File System Access API). Firefox and
Safari work too, but exports fall back to normal browser downloads and the
folder overview feature won't be available.

### Projects
- Everything is organized into **Projects** (a show) containing **Maps**
  (individual pixelmaps).
- Projects auto-save to the browser's local storage.
- Use **Export project** to save a `.json` backup you can keep with the
  show folder or hand to a teammate — **Import** brings it back on any
  machine. This is the real save file; local storage is convenience only.

### Maps
- Set canvas size, tile size (with common LED pitch presets), colors,
  numbering style, guides, and an info badge.
- **Zones** split a canvas into left-to-right color regions with their own
  tile counts (e.g. two side screens + a center wall of different pitch).
- **Irregular rows** give each row its own height and tile width, for
  double-height cabinets and staggered layouts.
- **Edit tiles** mode lets you click tiles in the preview to remove them —
  for staircase edges and partially-filled walls.

### Exporting
- Export a single map, each zone separately, or every map in a project.
- Optionally set an export folder (Chrome/Edge) so PNGs save directly to
  disk without a download dialog per file.

### Overview boards
- Click a project's folder icon (or the ⊞ icon) to see every map in that
  project as thumbnails on a drag-to-arrange board. Layout is saved with
  the project.
- "View folder overview" scans a chosen folder of already-exported PNGs
  for the same kind of layout board.

## Repo structure

```
index.html      the entire application
README.md       this file
```

## Deploying (GitHub Pages)

1. Push this repo to GitHub.
2. Repo Settings → Pages → Deploy from branch → `main` / `(root)`.
3. The tool is now live at `https://<your-org>.github.io/<repo-name>/`.

Any push to `main` updates the live version for everyone on the team —
no separate install step.

## Notes

- All data lives in the browser (localStorage) or in exported `.json`
  project files. There is no backend and no analytics.
- Tile-pitch-to-pixel mappings on the preset dropdown are approximate and
  vary by manufacturer — always confirm against the actual cabinet spec
  sheet before finalizing a real show file.
