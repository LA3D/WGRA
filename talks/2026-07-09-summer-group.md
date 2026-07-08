# Wiki-Grounded Research Agent — Summer AI Extraction Group talk

**Date:** Thursday 9 July 2026
**Speaker:** Chris R. Sweet, CRC
**Duration:** 35 minutes presented + Q&A
**Audience:** Summer group colleagues, broad AI-expertise range, some potential template adopters
**Format:** PowerPoint slides with one live browser demo (§7)

Underscore prefix on `_talks/` means GitHub Pages skips this directory. Local artifact.

---

## Slide 1 — Title

**On slide:**
- Title: Wiki-Grounded Research Agents
- Subtitle: A shared living memory for scientists and their AI agents
- Byline: Chris R. Sweet, CRC · Notre Dame
- Footer: 9 July 2026 · Summer AI Extraction Group
- URL: la3d.github.io/WGRA

**Visuals:** clean title slide. Maybe the "long-serving lab technician" framing as a soft-tone italic line under the byline.

**Speaker notes (30 sec):** Set the scene. "This is a talk about a pattern I've been working on with a small group at CRC. Not a product launch, more like an invitation. What you'll see is what happens when you take LLM-authored durable memory seriously and build the discipline around it."

---

## Slide 2 — The problem

**On slide:**
- Header: Every LLM session starts from zero.
- Three bullets:
  - ChatGPT / Claude conversations don't remember the last one.
  - Retrieval-augmented generation over your group's PDFs rediscovers the same chunks every query.
  - Nothing accumulates between conversations. Nothing compounds between collaborators.
- Bottom: When the student who ran the analysis graduates, so does the knowledge.

**Visuals:** a simple diagram showing "session 1 → nothing → session 2 → nothing → session 3." Or three faded overlapping conversation bubbles with no arrows connecting them.

**Speaker notes (2 min):** "Everyone in this room has had the experience of pasting the same context into an LLM session for the third time this week. RAG helps at query time but doesn't build anything. And when the student who did the work leaves, the practical knowledge, what worked, what failed, why we abandoned that approach, walks out the door with them. That's the problem. And it's not solved by more compute or a better model."

---

## Slide 3 — The pattern in one diagram

**On slide:**
- Header: The wiki-grounded pattern
- Diagram (left-to-right):
  - `Raw sources` (PDFs, code, notes, meeting transcripts)  →
  - `LLM-authored wiki` (Markdown pages with typed frontmatter edges, in git)  →
  - `Agent` (Claude, Cursor, etc.)
- Small caption: The wiki sits between raw sources and the agent. It is the memory.
- Attribution: Karpathy 2026 · Saboia Moreira et al. 2026

**Visuals:** three-box diagram with the wiki as the middle box, larger and highlighted. Small arrows suggesting bidirectional flow (agent reads from wiki, agent writes to wiki).

**Speaker notes (1.5 min):** "The whole pattern is right here. A wiki, LLM-authored, sitting between your raw sources and whichever agent you're using today. Markdown pages, git-committed, browsable by humans through GitHub or Obsidian, queryable by machines through typed edges and a formal ontology. The agent writes to the wiki as it works; the next session reads what the last one wrote. Karpathy sketched the idea in a Gist earlier this year; we filed the Beyond Memory paper on Zenodo formalizing the discipline."

---

## Slide 4 — Memory that compounds

**On slide:**
- Header: Memory that compounds
- Two-column contrast pair:
  - **RAG:** rediscovers your documents on every query. Nothing accumulates.
  - **Wiki:** the memory itself. Grows across sessions, users, and machines.
- Small note: The wiki carries both formal outputs (publications, code, benchmarks) and informal institutional memory (lab notebooks, meeting slides, protocol binders, half-drafted thesis chapters).

**Visuals:** the same two-panel contrast style you use in the flyer (grey callout box with strong terms in accent color). Optional: a screenshot of a real wiki page with typed frontmatter visible.

**Speaker notes (1.5 min):** "The core value proposition is this: RAG's memory is your document store, which the model rediscovers on every query. The wiki's memory is the memory. It grows. When someone new joins the group in September, they don't start from zero. They start from where the wiki is."

---

## Slide 5 — Failure-path preservation

**On slide:**
- Header: The file-drawer effect (Rosenthal 1979)
- Left: Journals publish the win. The abandoned method is noise.
- Right: Wiki preserves the trajectory. The corrected page is filed alongside the original with a cross-reference. The failure stays in place with a status pointer.
- Bottom, boxed: "Every group has a student who repeated a failed method because no one told them."

**Visuals:** on the right, a small screenshot of a real wiki page showing a `Status:` frontmatter field pointing to a successor page. Or a diagram: original page (grey, marked "abandoned") → successor page (blue, current).

**Speaker notes (1 min):** "Journals publish the win. Everything else, the abandoned method, the walked-back claim, the metric bug that inflated an earlier result, gets deleted from the record. The wiki flips that. Corrections are filed alongside originals, not on top of them. A reader arriving a year later sees the trajectory, not just the answer. Verification gates enforce this at commit time; you can't silently overwrite a claim, you have to file the correction as its own page."

---

## Slide 6 — Case study: web_forager, the setup

**On slide:**
- Header: Case study — Web Forager (research execution, two-author project)
- What: two researchers, Claude Code sessions on separate machines, a demo branch a colleague was preparing.
- Setup: colleague's ran the pipeline, reported 17/17 entity coverage on the flagship client.
- Reviewer picked it up in a separate session on the main branch.

**Visuals:** simple two-panel diagram. Left panel: "Colleague on demo branch, reports 17/17." Right panel: "Reviewer on main branch, reads the wiki."

**Speaker notes (1.5 min):** "Concrete story. Two-author project. Web scraping, entity coverage as the metric. The colleague on the demo branch reports 17 out of 17 entities extracted for the flagship customer. Sounds great. The reviewer opens a separate Claude Code session on the main branch to sanity-check. That's where it gets interesting."

---

## Slide 7 — Case study: the finding

**On slide:**
- Header: The reviewer walked the wiki, not the code
- The `extends:` edge on Experiment 11 pointed to Experiment 7.
- Experiment 7 pointed to Experiment 8.
- Following the typed-edge chain surfaced a claim: "if the LLM answers 'not visible on this page,' the pipeline treats it as a successful answer and stops the search."
- That is exactly the case where deeper searching was warranted.
- Real coverage: **8 of 17.** Not 17 of 17.

**Visuals:** three boxes connected by arrows labeled `extends:`. Experiment 11 → Experiment 7 → Experiment 8. Highlight the bug callout in a red-tinted callout box.

**Speaker notes (2 min):** "The pipeline was counting the model's honest 'I can't find this on this page' hedges as successful answers, and stopping the search. That's a subtle bug. And the way it surfaced was through the wiki, not through the code. The reviewer followed the `extends:` edge from the current experiment page back to the two previous experiments. Same bug had cascaded from Experiment 7 through Experiment 8 to Experiment 11. Real coverage was 8 of 17, not 17. Fix in one commit; the cascade to the prior experiments was corrected because the graph told the reviewer where else the bug had spread."

---

## Slide 8 — Case study: what worked

**On slide:**
- Header: What worked here
- Bullets:
  - Two authors, two Claude sessions, no coordination needed.
  - The typed `extends:` edge is what made the cascade legible. A body link would have said "there's a connection somewhere." The typed edge said "this page inherits from that one."
  - 75% coverage recovery on the flagship entity after the fix.
  - Full narrative: `la3d.github.io/WGRA/wiki-collaboration-story/`
- Bottom line: **This does not happen with RAG.** RAG surfaces similar chunks; it does not walk semantic edges backward across experiments.

**Visuals:** on the right, a small QR code or short URL to the full case study.

**Speaker notes (1.5 min):** "The mechanism that made this catchable was the typed edge, and the discipline of filing every experiment as its own page with an `extends:` back to what it built on. Body links would have said 'these pages are related somehow.' The typed edge said 'this experiment inherits its analytic frame from that one; if that one is wrong, this one probably is too.' 75% coverage recovery after the fix, on the customer's flagship entity. Full story linked from the flyer."

---

## Slide 9 — Team scale: attribution

**On slide:**
- Header: Team scale — collaborative within a group
- Left contrast: Slack + Google Docs: parallel notes that never combine. Trail decays with time.
- Right contrast: Wiki: one attributed memory. Contributions compound.
- Small callout: Every log entry carries `by: <human> via <agent>`. Git preserves full amendment history. Conflicts route through LLM-assisted merge.

**Visuals:** small diagram of two collaborators writing to the same wiki, both attributed, both landing without overwrite.

**Speaker notes (1 min):** "A postdoc and a grad student on the same project today keep notes in Slack, Google Docs, Jupyter notebooks, half-remembered lab meeting slides. When the PI checks in a month later, most of the trail is scattered. The wiki-grounded model gives every entry a `by:` line, per-action attribution. Two collaborators writing at the same time, the environment resolves mechanical conflicts automatically and routes semantic ones through an LLM-assisted merge. Both contributions land."

---

## Slide 10 — Team scale: federation

**On slide:**
- Header: Federated across groups
- Left contrast: Institutional knowledge locked in individual labs, walks out with the PI.
- Right contrast: Federated wikis: your peers' work, queryable through your agent.
- Diagram: three wiki-agent pairs, arrows connecting them via `ask` calls with permission.
- Small note: `ask` is published in v0.1.0 of the template. `message`/`post` mailbox skill is on the maintainer machine, not yet published.

**Visuals:** three connected boxes labeled "Group A wiki + agent," "Group B wiki + agent," "Group C wiki + agent." Bidirectional dashed arrows labeled `ask` between them.

**Speaker notes (1.5 min):** "Every group runs its own wiki, its own permissions, its own memory. Agents publish an 'agent card' that says what the group knows about. Your agent can query a peer group's wiki with permission, and get cited responses back. In practice: your colleague in comp-chem answered a DFT-functional-benchmarks question last year. You don't have to ask them to write it up again; your agent asks their agent, gets a cited response, and files the answer in your own wiki. The `ask` mechanism ships in v0.1.0."

---

## Slide 11 — Agent capability: built-in workflow

**On slide:**
- Header: Discipline in the artifact, not in memory
- Left contrast: Raw AI subscription: every student prompts differently. Discipline lives in memory.
- Right contrast: Configured environment: the discipline is in the repo. Every session starts from a known baseline.
- What ships:
  - Four operations (ingest, query, lint, verify) as single commands.
  - Verification gate: no filed numerical claim without real script output.
  - Discipline gates: universally-wrong rationalizations paired with the check that defeats them.
  - Every session starts with a reminder: the wiki is project memory.

**Visuals:** a screenshot of the `.claude/skills/` folder listing the wiki-source, wiki-experiment, wiki-lint skills. Or a screenshot of a SessionStart hook message.

**Speaker notes (1.5 min):** "A group Claude subscription doesn't get you a workflow, it gets you access. The wiki-grounded pattern ships the workflow. Four operations run as single commands. A verification gate blocks numerical claims that aren't backed by real script output. Discipline gates catch things like 'oh, I'll just skip the validation this once' before they land in a commit. And every session starts with a reminder that the wiki is project memory, so the agent doesn't have to be told."

---

## Slide 12 — Agent capability: multi-AI model

**On slide:**
- Header: Model-agnostic by design
- Left contrast: Vendor-locked AI: the memory lives with the vendor.
- Right contrast: Wiki-grounded: the memory is yours. Swap the AI.
- Bullets:
  - Claude, Cursor, or whoever comes next — same wiki, different overlay.
  - Different agents read the wiki through their own skills, share the same policy files and schema.
  - The `by: <human> via <agent>` line captures which tool did which write.

**Visuals:** the wiki in the middle, three agent icons (Claude, Cursor, "next model") around it, all connected. Vendor logos avoided; use generic agent icons.

**Speaker notes (1 min):** "The AI vendor landscape churns every six months. If your workflow is locked to one company's subscription, you're locked to their model choices, pricing, and terms. The wiki is durable. The agent is disposable. When a better model appears next year, adopting it is a new overlay, not a migration."

---

## Slide 13 — Knowledge graph substrate: what it is

**On slide:**
- Header: The knowledge graph substrate
- Bullets:
  - Every typed edge in a wiki page's frontmatter reifies to an RDF triple.
  - The wiki isn't just linked Markdown. It's a queryable knowledge graph with a 28-class ontology and SHACL-validated structure.
  - A shipped library of SPARQL queries runs against `graph.ttl` directly.
- Bottom: **Prose + hyperlinks:** browsable memory. **Reified graph:** SPARQL over meaning.

**Visuals:** small diagram showing a Markdown page's frontmatter on the left, an arrow, and RDF triples on the right (subject–predicate–object). Or the ontology visualization screenshot from the KG deep-dive.

**Speaker notes (1 min):** "The layer that turns this from 'a wiki with links' into 'a queryable memory' is the RDF reification. Every typed edge, `extends:`, `supports:`, `criticizes:`, `related:`, becomes an RDF triple against a formal ontology. SHACL shapes validate the structure at commit time. And an agent can query the graph directly with SPARQL. This is what makes the case-study cascade possible: the reviewer's agent could have queried 'walk backward along the extends edge and tell me every experiment implicated.' One query, not manual browsing."

---

## Slide 14 — Live demo teaser

**On slide:**
- Header: What this looks like on a real research wiki
- Bullets:
  - `markov_embeddings_and_rag`. A live research-execution wiki on retrieval-as-Markov-walk. 51 titled notes. 1,162 triples.
  - The same edge pattern that caught the web_forager cascade (slide 8) shows up here on a second wiki.
  - 11 canned SPARQL queries in the base template. All 11 executed against the live `graph.ttl`.
- Bottom: [switching to browser]

**Visuals:** small screenshot preview of the KG deep-dive page.

**Speaker notes (30 sec):** "I want to show you this rather than talk over slides. Give me two minutes in the browser."

---

## Slide 15 — LIVE DEMO placeholder

**On slide:**
- Just: **la3d.github.io/WGRA/knowledge-graph/**
- Subtitle: (switching to browser)

**Visuals:** large URL, nothing else. This is the Alt-Tab slide.

**Speaker notes (5 min live demo, do these three things in order):**

1. **Show the ontology graph.** "Here are the 28 classes a wiki page can inhabit. Concept, Note types, Structure pages, People. This is the shared semantic foundation. Every wiki instantiated from the template gets this for free."
2. **Scroll to the markov_embeddings_and_rag instance graph.** "This is a different research wiki, same pattern. The gold-highlighted edges have the exact shape as the web_forager cascade I just described — a four-hop `extends` chain from a leaf finding (Dense-RAG-Scale-Collapse) back through experimental lineage to a foundational concept (Iterative-Chained-RAG), and a `criticizes` edge from that same leaf finding to a page five hops up its own ancestry (RAG-Sanity-Check). The wiki review pattern that caught the 8-of-17 bug in web_forager is the same graph-shape you're seeing here. Random-Walk-With-Restart is the central hub with 48 inbound edges — surfaced automatically from graph structure. You didn't have to hand-author a 'start here' page."
3. **Scroll to SPARQL: the `supports/criticizes` query.** "Full query text. Executed via rdflib against `graph-full.ttl`. Four rows returned — an unusually rich result. Both supports AND criticizes edges exist. The `Dense-RAG-Scale-Collapse criticizes RAG-Sanity-Check` row is the pattern's own thesis in action: a current experimental finding contradicting an early framework claim, filed as a typed edge so the disagreement survives in the graph."

Alt-Tab back to PowerPoint when done.

**Fallback if browser fails:** Slides 15a, 15b, 15c below.

---

## Slide 15a — DEMO FALLBACK 1 (screenshot: ontology graph)

**Prep:** open `la3d.github.io/WGRA/knowledge-graph/` in Safari, wait for the ontology Cytoscape to render, take a full-window screenshot. Paste on this slide.

**On slide caption:** The `llm-wiki-colab` ontology: 28 classes, semantic properties as edges. Concept as the central hub with page-to-page edges (dashed) for `extends`, `supports`, `criticizes`.

## Slide 15b — DEMO FALLBACK 2 (screenshot: instance graph)

**Prep:** scroll to the markov_embeddings_and_rag instance graph on the same page, wait for render, screenshot. Paste.

**On slide caption:** 30 nodes, 39 typed edges from a real research wiki. Gold-highlighted edges have the same shape as the web_forager cascade (slide 8): a four-hop `extends` chain from a leaf finding (Dense-RAG-Scale-Collapse) back through experimental lineage to a foundational concept (Iterative-Chained-RAG), and a `criticizes` edge to a page in the same finding's ancestry (RAG-Sanity-Check).

## Slide 15c — DEMO FALLBACK 3 (screenshot: SPARQL result table)

**Prep:** scroll to the "All typed evidence edges" section on the same page, screenshot the query text plus the 4-row result table. Paste.

**On slide caption:** Live SPARQL result against the wiki's `graph-full.ttl`. Four typed evidence edges: two `supports` and two `criticizes`. `Dense-RAG-Scale-Collapse criticizes RAG-Sanity-Check` is the pattern's thesis in action — a current experimental finding contradicting an earlier framework claim, filed as a typed edge.

---

## Slide 16 — Case studies at a glance

**On slide:**
- Header: The pattern applied to three different project types
- Three columns:
  - **Web Forager** — research execution + typed-edge bug cascade — 75% recovery. (What we just saw.)
  - **AI-Sci-Disc-Mem** — external literature review, topic map, cross-domain connectivity — 115 papers, 20 topics.
  - **SavoieAgentKnowledge** — research-group publications catalog, 7 research problems as Concepts — 91 papers.
- Bottom: Same pattern, three genres. The queries generalize; the wiki content is domain-specific.

**Visuals:** three-column layout with a small screenshot preview of each case study page.

**Speaker notes (2 min):** "The pattern works across genres. Web Forager is a research-execution wiki with typed evidence edges, and that's how the bug cascade got caught. AI-Sci-Disc-Mem is an external literature survey: 115 papers organized around 20 topics with 453 cross-references, and the graph tells you which sub-domains actually talk to each other — Chemistry-Foundation Models is the strongest cross-topic bond at 18 references. SavoieAgentKnowledge is a group's own publications catalog: 91 papers organized around 7 research problems, and the graph tells the maintainer that 28 papers still need triage before they're linked to a problem. Same pattern, three genres."

---

## Slide 17 — Adoption: the template

**On slide:**
- Header: What ships in v0.1.0
- Bullets:
  - `crcresearch/llm-wiki-memory-template` on GitHub
  - `.claude/skills/` — wiki-source, wiki-experiment, wiki-lint procedures
  - `scripts/kg/` — build-graph.sh, SHACL shapes, 11 canned SPARQL queries
  - Verification gate + discipline gates preconfigured
  - `ask` federation mechanism for cross-wiki queries
- Bottom link: `github.com/crcresearch/llm-wiki-memory-template`

**Visuals:** a screenshot of the template's file tree, focused on `.claude/skills/` and `scripts/kg/`.

**Speaker notes (1 min):** "Everything I've described ships in v0.1.0 of the template. The federation mechanism, the skills, the verification gates, the KG pipeline. Clone the template, `cd` into it, and you have all of this from day one. No per-project configuration work."

---

## Slide 18 — Adoption: first-project setup

**On slide:**
- Header: Getting a wiki running today (15 minutes)
- Numbered list:
  1. Clone the template into a new repo.
  2. Set the project name and clear the seed content.
  3. Ingest your first source (paper, dataset, or code repo).
  4. Ask a question. The agent files the answer as a wiki page.
  5. Commit. From now on, every session starts from that memory.
- Bottom: We help with initial ingest. Bring your first three papers.

**Visuals:** a five-step diagram with small icons.

**Speaker notes (1.5 min):** "Fifteen minutes to a working wiki from a clean checkout. Clone, rename, ingest, ask, commit. After the first session, the wiki has your project in it. If you want help with initial ingest, especially for domain sources like databases or complex figures that need a schema-driven connector, that's what CRC is here for. Bring your first three papers, we'll walk through the pattern with you."

---

## Slide 19 — What compounds when you do this

**On slide:**
- Header: One year in, what you have
- Bullets:
  - A durable, browsable memory of the project as it evolved.
  - Every failure, correction, and decision preserved with attribution.
  - A queryable graph for the agent to reason over.
  - Federation-ready: your peers can query your wiki through their agents, with your permission.
  - A workflow that survives the current student, the current PI, the current AI vendor.
- Bottom: The wiki is the project. The AI is a tool that reads and writes it.

**Visuals:** stylized "wiki in a year" — a growing tree or timeline showing accumulation. Or three panels: month 1, month 6, month 12, each with a denser graph.

**Speaker notes (1.5 min):** "This is what you have twelve months in. Not just papers and code — the trajectory. Every failure filed, every correction cross-referenced, every decision attributed. Queryable. Federated. Portable across AI vendors. That's the compounding claim. The wiki is the project. The AI is a tool that reads and writes it."

---

## Slide 20 — Learn more

**On slide:**
- Header: Learn more
- Bullets with links:
  - Flyer: la3d.github.io/WGRA
  - Paper: Beyond Memory (Saboia Moreira et al., 2026) — doi.org/10.5281/zenodo.21213175
  - Template: github.com/crcresearch/llm-wiki-memory-template
  - Semantic foundation: la3d.github.io/llm-wiki-colab
  - KG deep-dive (with live SPARQL): la3d.github.io/WGRA/knowledge-graph
  - Case study: la3d.github.io/WGRA/wiki-collaboration-story

**Visuals:** two-column list, all as clickable-looking URLs. Optional QR code for the flyer.

**Speaker notes (30 sec):** "All the URLs are on this slide. The paper on Zenodo is the academic anchor with the full method. The template is the code. The KG deep-dive has the live SPARQL. Slack me for the setup session."

---

## Slide 21 — Contact + acknowledgements

**On slide:**
- Contact: Chris Sweet · csweet1@nd.edu · Center for Research Computing, Notre Dame
- Acknowledgements: co-authors on Beyond Memory · CRC leadership · early adopters (markov_embeddings_and_rag, AI-Sci-Disc-Mem, Web Forager teams)
- Bottom: **Questions?**

**Visuals:** simple, clean. Optional CRC logo bottom-right.

**Speaker notes (30 sec):** "Thanks for the time. Questions?"

---

## Fallback answers for likely Q&A

**Q: "How is this different from Obsidian / Notion / Roam?"**
A: Those are notebooks for humans; this is a notebook maintained BY an LLM with discipline gates preventing it from silently overwriting claims. Obsidian is your compatible viewer for the same file tree — you can open the wiki in Obsidian if you like. What's new is: (a) the agent authors it, (b) typed edges reify to RDF for graph queries, (c) verification and discipline gates enforce provenance at commit time.

**Q: "What does the verification gate actually do?"**
A: When the agent goes to file a numerical claim, the gate requires the claim to trace to real script output — not projected, not paraphrased. If there's no run log backing it, the commit is blocked. This is what stops projection-as-fact drift.

**Q: "How do I share my wiki with a collaborator who doesn't use Claude?"**
A: The wiki is Markdown in git. A collaborator with a browser and a text editor is fully productive. They can read, write, commit, and their contributions land with `by: <human>` attribution. The AI part is optional; the wiki is real.

**Q: "What's the LLM-usage cost per month?"**
A: Depends on ingest volume, but the pattern is designed to minimize sessions — you re-read the wiki, not the raw sources. In practice, our active projects are on the order of a few dollars per week of Claude usage. Nothing that scales with team size or corpus size the way RAG does.

**Q: "Can we start with our existing PDF library?"**
A: Yes. The `wiki-source` skill ingests PDFs one at a time and files them as SourceSummary pages with citation metadata. First 20 papers is a good weekend exercise. After that, the pattern is self-reinforcing.

**Q: "What if we want to use a different ontology?"**
A: The 28-class ontology is `llm-wiki-colab`; it's designed for research use and it's what the template ships with. If you have a domain-specific ontology, the extension mechanism is `extends:` on your Concept pages. But 95% of users won't need this.

---

## Speaker preparation checklist

- [ ] Copy this Markdown into PowerPoint (one heading per slide). Use consistent font and CRC template if you have one.
- [ ] Take the three demo-fallback screenshots (slides 15a-c) BEFORE the talk. Instructions on those slides.
- [ ] Rehearse the browser-demo section (slide 15) once. Practice the Alt-Tab back to slides. Rehearse the three-step tour: ontology graph → instance graph → SPARQL result.
- [ ] Test browser demo on the actual room's display 30 minutes before the talk. Confirm the Cytoscape graphs render.
- [ ] Have `la3d.github.io/WGRA/knowledge-graph/` as an open tab in the presenter's Safari before starting. Don't type the URL live.
- [ ] Bring backup: a USB drive with a screenshot of each URL slide in case internet drops.
- [ ] Q&A prep: read the fallback answers section above.

---

## Time budget check

| Slide | Section | Min |
|---|---|---|
| 1–2 | Title + Problem | 3 |
| 3 | Pattern in one diagram | 1.5 |
| 4–5 | Memory that compounds + failure preservation | 2.5 |
| 6–8 | Case study: Web Forager | 5 |
| 9–10 | Team scale (attribution + federation) | 3 |
| 11–12 | Agent capability | 3 |
| 13–14 | KG substrate teaser | 1.5 |
| 15 | LIVE DEMO | 5 |
| 16 | Three-case-studies overview | 2 |
| 17–18 | Adoption | 3 |
| 19 | What compounds | 1.5 |
| 20–21 | Learn more + contact | 1 |
| | **Total** | **32** |

Roughly 32 minutes presented, 3 minutes of buffer, comfortable at 40 max even with a slow start. If you're running short on time, trim slide 16 (the two secondary case studies) to a single sentence — the web_forager story is the flagship narrative and doesn't need help. If you're running long on time, cut slide 19 (the "what compounds" reflective slide).
