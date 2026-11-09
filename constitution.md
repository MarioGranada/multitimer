# Project Constitution — MultiTimer

This document defines the non-negotiable foundations for this repository. Read it before adding or changing features.

## Guiding Principles

- **Simplicity first** — prefer the smallest solution that solves the problem. If a change needs a long explanation, it is probably over-engineered.
- **No hardcoded secrets or endpoints** — configuration belongs in environment variables; visual design tokens belong in styles, not in `.env` files.
- **Traceability** — every value, dependency, and route should make its origin and purpose obvious.
- **Debuggability** — fail loudly and visibly; avoid silent fallbacks that hide broken data.
- **Official patterns** — use the documented API of each framework and library before inventing a workaround.
- **Portfolio clarity** — this repository is part of a public portfolio. Code should read as clean, intentional, and easy for a reviewer to follow. As a follow-along project, its purpose is to demonstrate the concepts practised in the course, not to imitate production scale.

## Technology Stack Foundations

| Layer | Choice | Rationale |
| --- | --- | --- |
| Framework | React 18 + Vite | Fast setup for a small refs-focused exercise. |
| State | React state + refs | Timer values and interval ids need both render state and mutable refs. |
| UI | Plain CSS | Keeps attention on the React APIs being practised. |
| Rendering | React portals | The result modal renders outside the challenge container. |

**Rule of thumb:** a new dependency must solve a concrete problem that the current stack cannot solve cleanly. Justify it in the change that introduces it.

## Core Premises

### 1. Scope

A refs/portals exercise. Keep the component count small and do not add routing, persistence, or a backend; the point is the React API practice.

### 2. Environment Isolation

- This project has no runtime secrets. Do not introduce `.env` files unless a real secret or environment-specific URL appears.
- If configuration is added, use environment variables and document them in the README.
- Never commit keys, tokens, database URLs, or credentials.

### 3. Architecture

- Keep timer mechanics in `TimerChallenge` and modal rendering in `ResultModal`.
- Expose only the imperative methods the parent needs.
- Use portals for overlays that should escape layout overflow.

### 4. Data and State

- Timer state is component-local and intentionally ephemeral.
- No persistence or global state is needed.
- Clear intervals and timeouts to avoid updates after unmount.

### 5. Styling and UX

- Plain CSS in `src/index.css`.
- Keep the challenge cards visually distinct and the modal readable over any challenge.
- Avoid adding a UI library for this exercise.

### 6. Quality Gates

- `npm run lint` and `npm run build` are the gates.
- Manually test start/stop for every challenge, stopping early, stopping late, and rapid repeated clicks.
- Verify the interval stops when the component unmounts.

### 7. Deployment

- Publish the Vite build to GitHub Pages through Actions.
- Configure the correct base path.
- No server is required.

## What to Avoid

- Leaving intervals running after stop or unmount.
- Using state for values that must update without a render (interval ids).
- Replacing the portal with an inline modal without checking overflow.
- Adding global state for a single-screen exercise.

## Checklist Before Adding Anything New

- Does this solve a real problem for this project, or am I adding scope for its own sake?
- Is every new value configuration-driven rather than hardcoded?
- Does the change follow the existing folder and naming patterns?
- Is there a clear failure path when data, the network, or the environment is unavailable?
- Have I run the available lint/build/test command and fixed what it reports?
- Did I update `README.md` and `MEMORY.md` if behaviour or setup changed?

## Philosophy Statement

This repository exists to show thoughtful front-end engineering: clear structure, readable code, and deliberate trade-offs. The goal is not to use every tool available, but to make every file explain itself. Simplicity is the feature.
