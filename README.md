# 🐍 Serpent Duels

Turn-based 3D strategy game with **simultaneous resolution**, built with Three.js in a single `index.html` file — no build step, no dependencies.

## Play

Open `index.html` in any modern browser (or enable **Settings → Pages → main branch** to play it directly on GitHub Pages).

## How it works

- **Planning phase**: draw your snake's path with the mouse or a finger. A virtual circle shrinks as you draw — it represents your remaining reach, which equals your snake's own length. The bigger your snake, the farther it goes.
- **Resolution phase**: both camps move at the same time. Every head that bites an opponent's body **cuts** it (the victim shortens, and dies if it becomes too short). Head-to-head contact is fatal for both, and the arena border is deadly.
- **Power-up pellets** scattered on the map:
  - 🟢 **Grow** — +5 segments
  - 🟡 **Speed** — burst of speed for the next turn
  - 🔵 **Dash** — pass through the first collision once
  - 🔴 **Fireball** — instantly strikes the nearest enemy head
  - 🟣 **Split** — divide your snake into two smaller controllable snakes
  - 🟠 **Bicephalous** — gain a second head (planned after the body, anchored to the tail with a limited neck)

## Modes

- Player vs AI (heuristic: hunts pellets, avoids bodies)
- 2 players on the same screen (hot-seat planning, simultaneous resolution)

## Controls

| Input | Action |
|---|---|
| Left click (near head) + drag | Draw the path |
| Right click + drag | Orbit the camera |
| Mouse wheel | Zoom |
