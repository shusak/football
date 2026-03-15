# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A browser-based recreation of the classic Mattel Electronics Football handheld game from the late 1970s/early 1980s. The entire game is a single `index.html` file (HTML + CSS + JavaScript, no build tools or dependencies).

## Running

Open `index.html` directly in a browser. No server, bundler, or install step required.

```
open index.html
```

## Architecture

Single-file app with three sections in `index.html`:

- **CSS (top)**: Styling for the handheld device shell, green football field with yard lines/hash marks, LED dots for players, and responsive mobile layout.
- **HTML (middle)**: Device frame with scoreboard (score, time, down, YTG, ball position), 10x5 grid field, d-pad controls, kick/status buttons, and start/reset buttons.
- **JavaScript (bottom)**: All game logic.

### Game State Model

The `game` object holds all state. Key concepts:

- **100-yard field with 10-column viewport**: The field is 100 yards. The 10-column LED grid is a sliding window (`viewOffset`). When the player reaches the right edge, the viewport shifts forward and new defenders spawn.
- **Absolute vs screen coordinates**: `yardLine`, `lineOfScrimmage`, `firstDownYard` are absolute (0-100). Player/defender positions use screen columns (0-9). `yardToCol()` and `colToYard()` convert between them.
- **Game phases**: `idle` → `kickoff` → `return` → `play`. Kickoff happens at game start and after touchdowns. Return phase has free movement (no downs). Play phase enforces downs/scrimmage rules.
- **Stats tracking**: `totalYards`, `touchdowns`, `plays`, `turnovers` — shown via STS/pause button.

### Audio

All sound is generated via Web Audio API (`AudioContext`) — no audio files. Includes reveille (game start), move beeps, referee whistle (tackle), crowd noise (touchdown), kick sounds, and fanfare.

### Controls

- Arrow keys / WASD / on-screen d-pad: movement
- Space / KICK button: punt
- P / STS button: pause + stats
- Enter / START: begin game
