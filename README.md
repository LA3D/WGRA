# WGRA — Wiki-Grounded Research Agent

Flyer and landing page for the **Wiki-Grounded Research Agent**: a shared wiki-memory for scientists and their AI agents.

Live at [la3d.github.io/WGRA](https://la3d.github.io/WGRA).

## Files

- `index.html` — the flyer, served by GitHub Pages at the URL above.
- `flyer.md` — Markdown source for the flyer text. Edit here, regenerate `index.html` if the structure changes.
- `README.md` — this file.

## Companion artifacts

- Substrate paper: [Beyond Memory (Saboia Moreira et al., 2026)](https://doi.org/10.5281/zenodo.21213175) — the templated substrate the WGRA is built on. (Concept DOI, tracks the latest Zenodo version.)
- Template: [`crcresearch/llm-wiki-memory-template`](https://github.com/crcresearch/llm-wiki-memory-template) — the reusable llm-wiki-memory-template repository.
- Semantic foundation: [`la3d/llm-wiki-colab`](https://la3d.github.io/llm-wiki-colab/) — typed-edge OWL ontology, JSON-LD context, SHACL shapes, SPARQL queries. Formal vocabulary the template's KG pipeline applies.
- Companion paper (in submission): "A Wiki-Grounded Educational Gateway for Course-Aware Socratic LLM Tutoring: Built on the llm-wiki Pattern" — Gateways 2026.

## Contact

Chris Sweet · [csweet1@nd.edu](mailto:csweet1@nd.edu) · Center for Research Computing, University of Notre Dame

## GitHub Pages setup

Enable Pages on this repo: Settings → Pages → Source: `Deploy from a branch` → Branch: `main`, folder `/`. Save. The site takes a minute to appear at [la3d.github.io/WGRA](https://la3d.github.io/WGRA).
