# WGRA talk — Quarto / reveal.js source

Source and rendered output for the *Wiki-Grounded Research Agents* talk (Summer AI Extraction Group, 9 July 2026).

Live URL: `https://la3d.github.io/WGRA/talks/quarto/WGRA_talk.html`

## Contents

- `WGRA_talk.qmd` — Quarto source. Title + 19 content slides.
- `WGRA_talk.html` — rendered output. Open in Safari or Chrome to present.
- `WGRA_talk_files/` — reveal.js + Quarto library assets the HTML depends on.
- `custom.scss` — theme matching the PowerPoint palette (navy `#14213d`, gold `#b8860b`, cream callouts).
- `cytoscape.min.js` — Cytoscape.js 3.30.4, used by the three live KG widgets.
- `instance-graph-slice.json` — 30-node markov_embeddings_and_rag slice with six case-study edges gold-highlighted (used on the KG demo slide).
- `document-graph-slice.json` — 25-node slice of a real briefing document from the extraction pipeline (used on the document-graph slide).
- `rwr_animation.html` — the Random Walk with Restart simulation from `markov_embeddings_and_rag/docs/`. Iframed on the Markov chain slide.
- `paper-explorer.html` — Priscila Moreira's paper-atomizer explorer (from `markov_embeddings_and_rag/docs/`), copied with the "Mercadier 2011 — live graph" tab set as default. Iframed on the extraction slide.

## Rendering

```bash
brew install quarto            # one-time, if not already installed
cd talks/quarto
quarto render WGRA_talk.qmd
```

Or preview live while editing:

```bash
quarto preview WGRA_talk.qmd
```

Auto-reloads on save.

## Presenting

Open `WGRA_talk.html` in Safari or Chrome. Reveal.js keybindings:

- Arrow keys / space — next slide
- `s` — speaker view (opens a second window with notes + upcoming slide)
- `f` — fullscreen
- `esc` — overview
- `?` — full keybinding list

## Alternative output formats

Same `.qmd` renders to:

```bash
quarto render WGRA_talk.qmd --to beamer   # LaTeX Beamer PDF
quarto render WGRA_talk.qmd --to pptx     # PowerPoint (static; loses live JS)
```
