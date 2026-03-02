# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of browser-based mini games, each as a **single self-contained HTML file** with no build step, no dependencies, and no external assets. Open any file directly in a browser to play.

## Running Games

```bash
open <game>.html        # macOS — opens in default browser
```

No server, bundler, or install step required.

## Architecture Pattern

Every game follows the same conventions:

- **One file only** — HTML, CSS, and JS are all inline in a single `.html` file.
- **Dark theme palette** — background `#1a1a2e`, accent red `#e94560`, accent teal `#a8dadc`, text `#eee`.
- **No external dependencies** — vanilla JS, no frameworks, no CDN imports.

### DOM-based games (e.g. `tictactoe.html`)
- State held in plain JS variables; `render()` rebuilds the DOM on each state change.
- Event listeners wired directly to elements.

### Canvas-based games (e.g. `shooter.html`)
- `requestAnimationFrame` loop: `loop(now)` → `update(dt, now)` → `render()`.
- Delta-time (`dt`) capped at 50ms to prevent large jumps after tab blur.
- All game objects are plain JS objects (`player`, `bullets[]`, `enemies[]`).
- Collision detection uses circle-circle: `dist(a,b) < a.radius + b.radius`.
- Canvas resizes to `window.innerWidth × window.innerHeight` on load and on `resize`.

## Git & GitHub Workflow

- **Remote:** `https://github.com/victorshenbr/helloworld`
- **Branch:** `main`
- Use [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `chore:`, `refactor:`
- Each game addition or significant feature change gets its own commit.
- To roll back a file: `git revert <hash>` (prefer revert over reset to preserve history).
