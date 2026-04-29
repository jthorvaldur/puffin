# puffin

> Read `INTENT.md` before acting. It governs all work in this repo.

## Overview
Electron GUI for Claude Code adding structured software engineering workflow: Central Reasoning Engine (CRE), automated sprint orchestration, Excalidraw AI diagrams, and Code Model memory plugin. Transforms conversational AI coding into deterministic, traceable development.

## Language & Stack
- Primary: JavaScript/React (Electron)
- Key files: `src/main/`, `plugins/`, `shared/hdsl-types/`, `h-dsl-engine/`
- See `CHANGELOG.md` for version history

## Session Start Protocol
If Qdrant is available (localhost:6333), query `feedback_events` and `fact_registry` for context before producing output.

## Agent rules
- Do not commit .env or secret files
- This is a fork of Claude Code — be careful with upstream merge compatibility
- Plugin architecture is deliberate — extend via plugins, don't modify core
