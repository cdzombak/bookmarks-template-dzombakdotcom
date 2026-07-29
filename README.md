# bookmarks-template-dzombakdotcom

The dzombak.com-styled template for
[raindrop-public-browser](https://github.com/cdzombak/raindrop-public-browser),
making the public bookmarks browser appear as part of
[dzombak.com](https://www.dzombak.com): same header, footer, typography,
colors, dark mode, and responsive behavior as the site itself.

## Usage

Point the app's `TEMPLATE_DIR` environment variable at this directory (or
mount it into the Docker container at the template mount point). The three
files — `list.html.tmpl`, `search.html.tmpl`, `results.html.tmpl` — are the
complete template set; the data each receives is documented in the app repo's
[TEMPLATES.md](https://github.com/cdzombak/raindrop-public-browser/blob/main/TEMPLATES.md).

## Notes

- Static assets are hotlinked from dzombak.com
  (`https://www.dzombak.com/assets/built/screen.css`); this template serves
  nothing of its own, and app-specific CSS is embedded in `list.html.tmpl`'s
  `app-css` define. Dark mode follows the site's `prefers-color-scheme`
  mechanism automatically.
- The bookmark cards reuse the site's Ghost `.kg-bookmark-card` classes, but
  the card is deliberately not a wrapping anchor — the title is the link —
  so some container styling is re-supplied in the embedded CSS.
- Known inherited contrast issue: the footer's `.cdz-terms-notice` uses the
  site's `--color-tertiary-text` (#999 on #fff, 2.85:1), which fails
  WCAG 2.2 AA in light mode. It is kept for fidelity with dzombak.com; a
  commented-out one-line fix sits alongside it in the embedded CSS.
