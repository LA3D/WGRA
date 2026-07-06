# Wiki-Grounded Research Agent

**A shared wiki-memory for scientists and their AI agents.**

*Configured to keep the AI honest, the collaboration durable, and the knowledge from walking out with the next graduating student.*

---

## Memory that compounds

### Persistent, structured memory

Every ChatGPT and Claude session starts from zero. Retrieval-augmented generation over your group's documents helps on the current question but rediscovers the same chunks on every next one. Nothing compounds between conversations.

The Wiki-Grounded Research Agent maintains an LLM-authored wiki between your raw sources and the agent ([Karpathy, 2026](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)): a small set of cross-linked Markdown pages with typed relationships (`extends:`, `requires:`, `related:`), written by the agent as it works, browsable directly by any collaborator through GitHub, the file system, or Obsidian. The wiki grows with the project; the agent's next conversation starts where the last one ended.

**RAG:** rediscovers your documents on every query. Nothing accumulates.
**Wiki:** the memory itself. Grows across sessions, users, and machines.

> **Data sources.** Off the shelf: papers, PDFs, notes, tables. For databases, APIs, or complex figures, small schema-driven connectors bring them into the wiki through the same ingest path.

### Failure-path preservation

Journals publish the win. The abandoned method, the walked-back claim, the metric bug that inflated an earlier result: all deleted from the record. Every group has a student who repeated a failed method because no one told them.

The Wiki-Grounded Research Agent is append-only by convention ([Saboia Moreira et al., 2026](https://doi.org/10.5281/zenodo.21213176)). When an approach turns out to be wrong, the corrected successor page is filed alongside the original with a cross-reference back; the failure stays in place with a *Status* note pointing forward. A verification gate makes sure new claims are filed *alongside* the ones they qualify, not on top of them. A reader arriving a year later encounters the trajectory, not just the answer.

**Journal:** the win. The abandoned path is noise.
**Wiki:** the win, plus every walked-back claim and its correction. The trajectory is the documentation.

---

## Team scale

### Collaborative within a group

A postdoc and a student on the same project keep notes in three places: Slack, Google Docs, their own Jupyter notebooks. When the PI comes back a month later, half the trail is lost.

The Wiki-Grounded Research Agent maintains a shared wiki with per-action attribution. Every entry carries a `by: <human>` line naming who claimed what; git preserves the full amendment history. When two collaborators write at the same time, the environment resolves mechanical conflicts automatically and routes semantic conflicts through an LLM-assisted merge. Both contributions land, neither overwrites the other, and the trail of who did what stays legible.

**Slack + Google Docs:** parallel notes that never combine. Trail decays with time.
**Wiki:** one attributed memory. Contributions compound rather than pile up.

### Federated across groups

Comp-chem overlaps with materials science, biophysics, catalysis. Every group is quietly re-answering questions another campus group already answered last year. When a PI leaves, that group's institutional memory often walks with them.

Wiki-Grounded Research Agents federate across projects. Each group runs its own wiki (its own memory, its own permissions), and its agent publishes an agent card that says what the group knows about and what channels it subscribes to. Your agent can query a peer group's memory for their DFT functional benchmarks, their tried-and-abandoned ML potentials, or the analysis workflow that produced a specific paper's figure, with the peer group's permission, and cited back to specific pages in the peer's wiki.

**Institutional knowledge:** locked in individual labs, walks out with the PI.
**Federated wikis:** your peers' actual work, queryable through your agent.

---

## Agent capability

### Built-in expertise

A group Claude or ChatGPT subscription doesn't get you a workflow, it gets you access. Every student prompts differently, no one enforces discipline, and the AI's helpfulness depends entirely on how well each student happened to prompt it.

The Wiki-Grounded Research Agent ships with the workflow already configured. A verification gate blocks the agent from filing numerical claims that aren't backed by real script output. Discipline gates catch universally-wrong rationalizations paired with the check that defeats them. Four built-in operations (ingest a source PDF, query the wiki, lint for staleness, verify a change before commit) run as single commands. The agent knows about them and reaches for the right one when the context calls, without waiting for the user to remember to type. Every session begins with a reminder to the agent that the wiki is project memory.

**Raw AI subscription:** every student prompts differently. Discipline lives in memory.
**Configured environment:** the discipline is in the artifact. Every session starts from a known baseline.

### Multi-AI model

The AI vendor landscape churns every six months. Betting a group's workflow on a single subscription today locks you into one company's model choices, pricing changes, and terms of use tomorrow.

The Wiki-Grounded Research Agent decouples the wiki (your durable memory) from the model doing the work today (Claude, Cursor, or whoever comes next). Different coding assistants each read the wiki through their own set of commands and skills, while sharing the same policy files, discipline gates, and wiki schema. One student can use Claude Code and another can use Cursor on the same project; the `by: <human> via <agent>` line on every log entry captures which tool did which write. When a better model appears next year, adopting it is a new overlay, not a migration.

**Vendor-locked AI:** the memory lives with the vendor.
**Wiki-grounded:** the memory is yours. Swap the AI.

---

## Get started

- **Setup:** new repository, or we bring the pattern into your existing one.
- **Ingest:** we help load your first papers, benchmarks, and lab data.
- **Contact:** Chris Sweet · csweet1@nd.edu · CRC, University of Notre Dame

`la3d.github.io/WGRA`
