# LED Football

A browser-based recreation of the classic [Mattel Electronics Football](https://en.wikipedia.org/wiki/Mattel_Electronics_Football) handheld game from the late 1970s/early 1980s.

## Play

Open `index.html` in any modern browser. No server, build tools, or dependencies required.

```
open index.html
```

Or host it anywhere that serves static files — it's a single HTML file.

## Features

- **Retro LED look** — red blinking player dot, blue defenders, green football field with yard lines and hash marks
- **Full 100-yard field** — 10-column scrolling viewport over the full field with yard position indicator
- **Kickoff mechanic** — opposing team kicks at game start and after each touchdown
- **Synthesized audio** — all sounds generated via Web Audio API (reveille, referee whistle, crowd noise, move beeps) — no audio files
- **Stats tracking** — touchdowns, total yards, plays, and turnovers
- **Mobile support** — on-screen d-pad and touch controls

## Controls

| Action | Keyboard | On-screen |
|--------|----------|-----------|
| Move | Arrow keys / WASD | D-pad |
| Kick / Punt | Space | KICK button |
| Pause / Stats | P | STS button |
| Start game | Enter | START button |

## Screenshot

The game renders a handheld device frame with a green football field, scoreboard, and physical-style buttons — all in the browser.

## License

MIT
