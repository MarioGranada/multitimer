# MultiTimer — Working Memory

_Last updated: 2026-11-02_

## Current status

- Four timer challenges, player form, and result modal are implemented.
- Refs, `useImperativeHandle`, and portals are the core learning points.
- No tests or deployment workflow yet.

## Key decisions

- Used an imperative handle so the challenge card owns its timer while the parent can start/stop it.
- Used a portal for the modal to avoid layout clipping.

## Known limitations and follow-ups

- No persistence or score history.
- No automated tests.
- Timer accuracy depends on browser interval scheduling.

## Mistakes to avoid

- Forgetting to clear the interval leaves timers running after stop.
- Reading refs during render produces stale or unexpected values.
- Do not move the modal inline without rechecking z-index and overflow.

## Next steps

- Add tests around the timer result calculation.
- Add a Pages workflow.
- Consider a best-score summary.

---

Keep this file under ~60 lines. Summarise or delete notes that no longer add value.
