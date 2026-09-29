# A.L.E.X-M1.0

> Personal multi-tool autonomous agent — Mark 1 of an evolving JARVIS/FRIDAY-style assistant.

![Status](https://img.shields.io/badge/status-planning-blue)
![Stack](https://img.shields.io/badge/stack-TypeScript%20%7C%20Next.js-3178C6)
![License](https://img.shields.io/badge/license-MIT-green)

## Overview

A.L.E.X-M1 is the first iteration of a personal autonomous agent inspired by fictional AI assistants like JARVIS, FRIDAY, and EDITH — built as a real, working system rather than a sci-fi reference. The "M1" (Mark 1) naming is intentional: this is meant to be the first of several iterations, each one adding capability as the underlying tools and architecture mature.

Unlike a single-purpose chatbot, A.L.E.X is designed around **tool use** — the agent reasons about a request, decides which tool(s) it needs (web search, code execution, calendar, file operations, custom automations), calls them, and synthesizes a response. That tool-calling loop is the actual engineering challenge this project is meant to demonstrate.

## Why Mark 1

This repo intentionally starts small. Mark 1's job is to prove the core loop works — conversation in, the right tool called, a useful result out — end to end, deployed, and demoable. Voice, memory, and a polished UI are real goals, but they're sequenced as later phases rather than blockers to a working v1.

## Design Principles

- **Tool-first, not chat-first.** The conversational interface is just the entry point; the value is in what tools the agent can reach for.
- **Reuse, don't reinvent.** Lean on existing skills (React/Next.js/TypeScript/Three.js) and existing infra (Vercel, free-tier APIs) rather than learning a new stack just to build v1.
- **Ship something demoable at every phase.** Each roadmap phase should end in something that can go on a resume or in a demo video, not just internal progress.
- **Progressive autonomy.** Mark 1 reacts to requests. Later marks move toward proactive behavior (reminders, triggers, scheduled checks) without trying to do it all at once.

## Planned Capabilities

**Conversational core**
- LLM-driven reasoning with a consistent agent persona
- Multi-turn context within a session

**Tool use (the core feature)**
- Web search / information lookup
- Code execution / sandboxed scripting
- Calendar and reminders
- File operations
- Extensible plugin architecture for adding new tools over time

**Voice interface** *(Mark 2+)*
- Speech-to-text input
- Text-to-speech output with a consistent "voice" for the agent

**Memory** *(Mark 2+)*
- Session memory (current conversation)
- Long-term memory (preferences, past requests, recurring context)

**Interface**
- Web dashboard as the primary interface for Mark 1
- Stretch goal: a HUD-style 3D visualization for the agent's "presence," in the spirit of Fizz & Co's product-storytelling visuals

## Tech Stack

| Layer | Choice | Why |
|---|---|---|
| Frontend | Next.js (App Router) + TypeScript + Tailwind | Already proven on Fizz & Co; fast to build, free to deploy |
| Agent orchestration | Vercel AI SDK | Native multi-step tool-calling loop, TypeScript-native, no separate backend needed for v1 |
| Reasoning engine | Claude or GPT-4-class model via API | Strong function-calling support; either integrates cleanly with the Vercel AI SDK |
| Voice (later phase) | Web Speech API → Whisper + ElevenLabs | Start free and native, upgrade once the core loop works |
| Memory (later phase) | Supabase (Postgres + pgvector) | Free tier, handles structured data and vector search in one place |
| Deployment | Vercel | Same workflow as existing projects, zero cost for this stage |

The whole stack stays in TypeScript through Mark 1 deliberately — engineering effort goes into the agent's tool-calling behavior, not into context-switching between languages.

## Architecture (Mark 1)

```
User ── Next.js UI ── API Route (Vercel AI SDK)
                              │
                       Agent reasoning loop
                              │
              ┌───────────────┼───────────────┐
         Tool: search    Tool: code-exec   Tool: calendar
              │               │                 │
              └───────────────┴─────────────────┘
                              │
                        Response to user
```

## Roadmap

- [ ] **Phase 1 — Foundation:** Chat UI, one working tool call end-to-end, deployed on Vercel
- [ ] **Phase 2 — Tool Expansion:** Multi-tool support, plugin-style architecture for adding new tools
- [ ] **Phase 3 — Voice:** Speech-to-text / text-to-speech integration for spoken interaction
- [ ] **Phase 4 — Memory:** Persistent memory and basic personalization
- [ ] **Phase 5 — Autonomy:** Proactive triggers, scheduled checks, reminders without being asked
- [ ] **Phase 6 — Polish:** 3D HUD-style interface, demo video, write-up for portfolio/resume

## Inspiration

Named in the spirit of fictional AI assistants — JARVIS, FRIDAY, EDITH — that combine conversational reasoning with the ability to actually *do* things in the world, not just answer questions.

## Status

🚧 **Planning phase.** Architecture and roadmap defined; implementation starts with Phase 1.

## Author

Built by Madhu ([@madhushankarkr-cmd](https://github.com/madhushankarkr-cmd)) — [portfolio](https://madhushankarkr-cmd.github.io/My-Portfolio)

## License

MIT — to be confirmed at first release.
