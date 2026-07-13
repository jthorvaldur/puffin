# puffin

## Overview
Electron GUI for Claude Code adding structured software engineering workflow: Central Reasoning Engine (CRE), automated sprint orchestration, Excalidraw AI diagrams, and Code Model memory plugin. Transforms conversational AI coding into deterministic, traceable development.

## Language & Stack
- Primary: JavaScript/React (Electron)
- Key files: `src/main/`, `plugins/`, `shared/hdsl-types/`, `h-dsl-engine/`
- See `CHANGELOG.md` for version history

## Session Start Protocol
If Qdrant is available (localhost:6333), query `feedback_events` and `fact_registry` for context before producing output.

## Data-First Protocol
When answering questions about data, facts, documents, conversations, or history:
1. **Query the vector DB first.** Use `devctl search "query"` or direct Qdrant search before answering from memory or general knowledge. The DB has 2M+ vectors across legal docs, chats, sessions, and facts.
2. **Know the search scopes.** `devctl search` defaults to ingested docs, court files, facts, and algorithms — AI-assistant chats are excluded (they carry questions and assertions, not ground truth). Use `--claude` for AI chat history (Claude Code, Claude.ai, ChatGPT), `--facts` for the fact registry / case facts, `--algos` for algorithms, `--all` to include everything.
3. **Cite the source.** Include collection name, confidence level, and date when referencing DB results.
4. **Distinguish confidence levels.** A bank statement (verified) is not the same as an email claim (asserted). Never present asserted facts as verified.
5. **Log new facts.** When you discover or confirm a fact during work, log it: `devctl log-fact --fact "..." --source-type X --confidence Y --domain Z`

## Agent rules
- Do not commit .env or secret files
- This is a fork of Claude Code — be careful with upstream merge compatibility
- Plugin architecture is deliberate — extend via plugins, don't modify core
