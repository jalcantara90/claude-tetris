# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Pure vanilla JS/HTML5/CSS3 Tetris — no package manager, no build step, no dependencies. All game state lives as module-level globals in `game.js`.

## Running the Game

Open `index.html` directly in a browser, or serve it with any static server:

```
python3 -m http.server 8000
```

## Code Style

- `'use strict'` at top of `game.js`
- No ES modules — `game.js` is a classic script; all state is global
- 2-space indentation, single quotes

## Critical Gotchas

**Canvas dimensions must be manually synced.** If you change `COLS`, `ROWS`, or `BLOCK` in `game.js`, you must also update the `width`/`height` attributes on `<canvas id="board">` in `index.html`. There is no auto-calculation.

**Next-piece canvas is independent of `BLOCK`.** It is hardcoded to 120×120px with its own block size constant `NB = 30` — changing `BLOCK` does not affect it.

**Wall kicks are horizontal-only.** Rotation collision resolution only tries column offsets `[0, -1, 1, -2, 2]`; there are no vertical kicks.

## Notes

- The README is written in Spanish
- `Space` key calls `e.preventDefault()` to prevent page scroll — this is intentional
