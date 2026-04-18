# CSE 163 ML-Course-Vault

Personal LLM-powered knowledge base for CSE 163 (Intermediate Data Programming) at UW, following the Karpathy/Elvis Obsidian-wiki workflow.

## Structure
- `raw/` — pointers to source material (references into `../hw1/`, `../lessons/`, `../lectures/`, `../past_final_projects/`)
- `wiki/` — LLM-compiled interlinked concept articles
- `outputs/` — study guides, Q&A results, visualizations

## How to use
1. Open this folder as an Obsidian vault.
2. Start at [[INDEX]] to navigate.
3. Add new source material as files (or pointers) in `raw/`.
4. Run the `leverage-llm-knowledge-base` scheduled task to ingest new material and grow the wiki.

## Workflow reference
See [[wiki/llm-knowledge-base-workflow]] for the Karpathy method this vault is built on.

## Recommended Obsidian setup

### First-time setup
1. Install Obsidian from https://obsidian.md/download
2. Open Obsidian → click the vault-switcher (bottom-left) → **Open folder as vault**
3. Point it at this folder (`ML-Course-Vault`)
4. Click **Trust author and enable plugins**
5. Open `INDEX.md` to start navigating

### Useful keyboard shortcuts
- `Cmd+O` — quick-switch to any note by name
- `Cmd+E` — toggle edit / preview mode
- `Cmd+Click` on a `[[wikilink]]` — open in new pane
- `Cmd+P` — command palette (search every Obsidian action)

### Core plugins to enable (Settings → Core plugins)
- **Graph view** — visualize how wiki articles connect. Great for seeing concept clusters before exams.
- **Backlinks** — shows every other note that links to the one you're reading. Indispensable for navigating the wiki.
- **Outline** — table of contents for long articles.
- **Tags** — if you start tagging notes (`#exam`, `#thapatterns`).
- **Templates** — for creating new lesson/THA articles with a consistent format.

### Community plugins worth installing (Settings → Community plugins → Browse)
- **Obsidian Web Clipper** — browser extension (Chrome/Firefox/Safari). Clip articles, docs, Stack Overflow answers directly into `raw/` as clean markdown. This is the tool Karpathy uses in his workflow.
- **Marp** — render Markdown as slide decks directly inside Obsidian. Useful for the CSE 163 final presentation — you can write slides as a `.md` file in `outputs/` and Marp renders them.
- **Dataview** — treat your markdown files like a database. Write queries like "list all wiki articles tagged `#lesson`, sorted by date." Overkill for now, powerful as the vault grows.
- **Excalidraw** — hand-drawn-style diagrams inside Obsidian. Good for data-structure diagrams or ML concept sketches.
- **Copy Block Link** — right-click any paragraph to get a direct link back to it. Helps when citing sources in outputs.

### Settings worth flipping right away
- **Editor → Readable line length** — ON (keeps articles from stretching edge to edge)
- **Files & Links → Use `[[Wikilinks]]`** — ON (this is already how the vault is written)
- **Appearance → Theme** — dark mode if you prefer; pick any community theme you like

### Folder to ignore
Add `raw/` to **Settings → Files & Links → Excluded files** if source files clutter your search results. The wiki articles in `wiki/` already reference them.
