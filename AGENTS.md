# AGENTS.md — MultiTimer

Compact guide for future OpenCode sessions. It records only the facts an agent is likely to miss or get wrong.

## Quickstart

| Command | Description |
| --- | --- |
| `npm install` | Install dependencies. |
| `npm run dev` | Start Vite at http://localhost:5173. |
| `npm run lint` | Run ESLint. |

## Requirements

- Node.js 18+.
- npm (a `package-lock.json` is committed).

## Environment

- No environment variables are required.

## Architecture

- `src/components/TimerChallenge.jsx` — timer state, refs, imperative handle.
- `src/components/ResultModal.jsx` — portal-based result dialog.
- `src/components/Player.jsx` — player name form.
- `src/App.jsx` — challenge composition.

## Commands and build order

- Use `npm run dev` for iteration.
- Run `npm run build` and `npm run lint` before finishing.
- There are no tests.

## Conventions and gotchas

- Always clear the interval in the stop handler and in effect cleanup.
- Do not read or write refs during render.
- The modal must remain a portal; moving it inline changes stacking behaviour.

## Memory

- Read `MEMORY.md` first to understand the current status and decisions.
- Before changing behaviour, read `constitution.md` and keep the change aligned with it.
- After a task, update `MEMORY.md` with status, decisions, and mistakes to avoid. Keep it short.
- If a rule becomes permanent, move it into this file instead of leaving it in memory.
- Never store secrets, tokens, or personal data in `MEMORY.md`.
