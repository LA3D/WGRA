# Quarto experiment — inline Cytoscape on a reveal.js slide

Proof of concept for authoring the KG-demo slide with an embedded Cytoscape graph rather than an Alt-Tab to Safari.

## Contents

- `slide-experiment.qmd` — the Quarto source. Two slides: one with the live graph, one plain-text slide to show the pipeline works for both.
- `cytoscape.min.js` — Cytoscape.js 3.30.4, copied from `../../knowledge-graph/`.
- `instance-graph-slice.json` — the same 30-node markov_embeddings_and_rag slice used on `la3d.github.io/WGRA/knowledge-graph/`, with `casestudy: "yes"` markers on the six edges we highlight in gold.

## Rendering

```bash
brew install quarto            # one-time, if not already installed
cd _talks/quarto-experiment
quarto render slide-experiment.qmd
```

Output lands at `slide-experiment.html` in the same directory, alongside a `slide-experiment_files/` folder of reveal.js CSS/JS. Open the HTML file in Safari or Chrome to present.

Or preview live while editing:

```bash
quarto preview slide-experiment.qmd
```

Auto-reloads on save.

## What to look for

**Slide 1:** two-column layout. Left column is a Cytoscape graph rendered from `instance-graph-slice.json`. Right column is a caption with talk-track prose. Speaker notes visible in reveal.js's speaker view (press `s` while presenting).

The six gold-highlighted edges are the same "case-study edges" as on the public knowledge-graph page — same JSON file, same styling logic. The graph is interactive: drag nodes, zoom, click to select.

**Slide 2:** plain bulleted list to demonstrate the pipeline handles both live-graph and static slides from the same Markdown source.

## Alternative output formats

The same `.qmd` renders to:

```bash
quarto render slide-experiment.qmd --to beamer   # LaTeX Beamer PDF
quarto render slide-experiment.qmd --to pptx     # PowerPoint
```

The `pptx` output won't have the live Cytoscape graph (PowerPoint can't run JavaScript on a slide), but it will keep the layout and text as a static handout.

## Things this proof of concept doesn't test yet

- Whether the graph renders correctly when the slide is off-screen at initial load (there's a `Reveal.on('slidechanged')` hook that re-fits, but you'd want to check).
- Full-deck styling to match the WGRA visual identity (currently uses the plain `white` theme).
- Speaker-notes rendering fidelity in reveal.js's speaker view.
- Whether `embed-resources: true` produces a single self-contained `.html` without breaking the JSON fetch (currently `false`, so the output is a folder).
