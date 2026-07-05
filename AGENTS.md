# LLM Wiki Methodology (AGENTS.md)

This document defines the schema and procedures for maintaining a personal knowledge base using the LLM Wiki methodology, as described by Andrej Karpathy. It is tool-agnostic and can be used by any LLM agent or assistant.

## Core Principles

The LLM Wiki system consists of three layers:

1. **Raw Sources Layer**: Immutable original documents, articles, notes, or any source material ingested into the system.
2. **LLM-Generated Wiki Layer**: A collection of interlinked Markdown files that represent distilled knowledge, summaries, and insights extracted from the raw sources.
3. **Schema/Doc Layer (this file)**: Provides the LLM with instructions on how to structure, update, and query the wiki.

## Directory Structure

- `SOURCES/` : Store raw source materials (e.g., PDFs, text files, web clips). Each source should be placed here before ingestion.
- `WIKI/` : Contains the generated knowledge base as Markdown files. Each note corresponds to a concept, entity, or topic.
- `LOGS/` : Contains chronological logs of ingestion and update actions for audit and replay.

## Workflow

### 1. Ingest

When a new source is available:

1. Place the source file in `SOURCES/` (or reference it via a stable URL/ID).
2. Instruct the LLM to:
   - Read the source.
   - Extract key information, facts, and concepts.
   - For each significant concept:
     - If a corresponding note exists in `WIKI/`, update it with new information, citing the source.
     - If no note exists, create a new Markdown file in `WIKI/` with a concise title and initial summary.
   - Append an entry to `LOGS/ingest.log` (or a timestamped log) documenting the action: source identifier, timestamp, notes created/updated, and any actions taken.
3. Optionally, the LLM may generate a brief summary of the source and store it as a note in `WIKI/` (e.g., `Source Summary - <title>.md`).

### 2. Query

To ask a question of the knowledge base:

1. Instruct the LLM to:
   - Search the `WIKI/` directory for relevant notes (by keyword, tag, or content similarity).
   - Read the top‑matching notes.
   - Synthesize an answer that cites the source notes.
   - Optionally, store the synthesized answer as a new note in `WIKI/` if it represents a durable insight, linking to the source notes used.
2. Return the answer to the user, including inline citations (e.g., `[[Note Title]]` or footnotes) so the user can trace the information back to the source material.

### 3. Lint (Maintenance)

Periodically, run a health‑check on the wiki:

1. Instruct the LLM to:
   - Scan `WIKI/` for:
     - Orphaned notes (no incoming links from other notes).
     - Duplicate or redundant notes covering the same concept.
     - Stale information that may have been superseded by newer sources.
     - Contradictions between notes.
     - Missing citations or links to source material.
   - Propose actions: merge notes, update content, add links, archive outdated notes, or request clarification from the user.
2. Record linting actions in `LOGS/lint.log` or a similar log.
3. Apply the LLM’s suggestions (with user approval if desired) to keep the wiki coherent and up‑to‑date.

## Agent Responsibilities

The LLM agent acting as the wiki maintainer should:

- Treat raw sources as immutable; never modify files in `SOURCES/`.
- Write all wiki notes in clear, concise Markdown, using Wikilinks (`[[Note Title]]`) for internal connections.
- Preserve a clear trail of provenance: every factual statement in a wiki note should ideally reference the source note(s) or raw source from which it was derived.
- Use consistent naming conventions for notes (e.g., Title Case for concept notes, `YYYY-MM-DD` for daily logs if applicable).
- Keep logs append‑only and timestamped.
- When uncertain, ask the user for clarification rather than hallucinating.

## Tool Agnosticism

This methodology does not depend on any specific LLM framework or tooling. Implementation details (such as how the LLM reads files, executes searches, or writes logs) are left to the agent or system employing this schema. The only requirements are:

- Ability to read files from `SOURCES/` and `WIKI/`.
- Ability to write files to `WIKI/` and `LOGS/`.
- Capability to perform semantic or keyword‑based search over Markdown content.
- Support for standard Markdown and Wikilink syntax (or equivalent linking mechanism).

## Getting Started

1. Ensure the directories `SOURCES/`, `WIKI/`, and `LOGS/` exist.
2. Place an initial source (if any) into `SOURCES/`.
3. Invoke your LLM agent with a prompt to ingest that source following the Ingest workflow above.
4. Begin querying the wiki to retrieve or synthesize knowledge.
5. Schedule regular linting cycles to maintain knowledge quality.

---

*This file is named `AGENTS.md` to be cross‑tool generic, as requested.*