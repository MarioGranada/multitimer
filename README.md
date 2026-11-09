# MultiTimer

A small timer game built to practise React refs, imperative handles, and portals. The player picks a name, then starts four challenges with target times of 1, 5, 10, and 15 seconds and tries to stop each timer as close to the target as possible.

Each challenge exposes start/stop behaviour through a ref, and the result is shown in a modal rendered outside the normal component tree.

> **Follow-along project.** This app was built while following **React — The Complete Guide (Academind / Maximilian Schwarzmüller)**. It is included in the portfolio as a learning exercise, not as a production product. The implementation is my own work based on the course material.

## Features

- Player name entry before starting.
- Four timer challenges with different target times.
- Start and stop controls per challenge.
- Result modal showing success or failure and the elapsed time.
- Countdown/elapsed display driven by an interval.
- Refs and `useImperativeHandle` to expose challenge controls.
- Portal-based modal rendering.

## Tech stack

| Layer | Technology |
| --- | --- |
| Framework | React 18 + Vite |
| State | React state + refs |
| UI | Plain CSS |
| Rendering | React portals |

## Project structure

```text
multitimer/
├── src/
│   ├── components/
│   │   ├── Player.jsx          # Player name form
│   │   ├── TimerChallenge.jsx  # Challenge card and timer logic
│   │   └── ResultModal.jsx     # Portal-based result dialog
│   ├── App.jsx                 # Challenge list
│   ├── main.jsx
│   └── index.css
├── index.html
└── vite.config.js
```

## Getting started

### Requirements

- Node.js 18+.
- npm (a `package-lock.json` is committed).

### 1. Install dependencies

```bash
npm install
```

### 2. Run locally

**Start the development server**

```bash
npm run dev
```

Open http://localhost:5173.

### Available scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start Vite on port 5173. |
| `npm run build` | Build the production bundle. |
| `npm run preview` | Preview the production build. |
| `npm run lint` | Run ESLint. |

## How it works

`App.jsx` renders the player form and four `TimerChallenge` cards with different `targetTime` values.

`TimerChallenge` owns the countdown state and exposes `start`/`stop` through `useImperativeHandle`. The parent can trigger those methods through a ref.

`ResultModal` renders through `createPortal` so the dialog is not clipped by the challenge layout. It receives the remaining time and target time and derives the result.

## Deployment

- Target: GitHub Actions builds the Vite app and publishes `dist/` to GitHub Pages. Set the Vite `base` to the repository path.
- The app is fully client-side and needs no backend or database.
- Vercel is an alternative if a simpler preview deployment is preferred.

## Notes and limitations

- Timer state is local to each challenge and is lost on reload.
- The game uses intervals; always clear them on stop and unmount.
- There is no persistence or leaderboard.

---

**Author:** Mario Granada
