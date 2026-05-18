# Notes

**Read them at:** <https://ivan-shishkin-dev.github.io/notes/>

My personal class notes from UC Irvine, organized by academic quarter.

I take raw notes during lecture in [Obsidian](https://obsidian.md/), then at the end of each day I have [Claude Code](https://claude.com/claude-code) clean them up — fixing typos, normalizing formatting, splitting content into logical lecture boundaries, and expanding shorthand where it helps readability. The original meaning, personal annotations, and humor are preserved.

## Current Courses (Spring 2026)

- **ICS 46** — Data Structures & Algorithms (C++)
- **ICS 51** — Computer Architecture
- **Informatics 43** — Software Engineering

## Structure

- All notes live under `content/` (the Quartz content directory)
- Inside `content/`, each top-level folder is a quarter (e.g. `content/Spring 2026/`)
- Each course is a single `.md` file inside its quarter folder, with all lectures appended sequentially
- `content/Pictures/` holds image embeds referenced by the notes
- Older quarters are archived as zip files in `content/Winter 2026/`

## Hosting

The site is built with [Quartz 4](https://quartz.jzhao.xyz/) and auto-deployed to GitHub Pages on every push to `main` via `.github/workflows/deploy.yml`. The notes themselves are plain Markdown — they render in Obsidian, on GitHub, and on the published site.

### Local development

```bash
npm ci
npx quartz build --serve
```

Then open <http://localhost:8080>.

## License

Notes content is personal coursework. The Quartz engine in `quartz/` is MIT-licensed by [jackyzha0](https://github.com/jackyzha0/quartz) — see `LICENSE.txt`.
