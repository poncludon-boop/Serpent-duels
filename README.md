# 🐍 Serpent Duels

> Gameplay system: **T.R.A.C.E.** (traced planning, turn-based with simultaneous resolution, body-length reach, power pellets) — see [TRACE-MECHANIQUE.md](./TRACE-MECHANIQUE.md) for the canonical vocabulary and tunables, reused by future games.

Turn-based 3D strategy game with **simultaneous resolution**, built with Three.js in a single `index.html` file — no build step, no dependencies.

## Play

Open `index.html` in any modern browser (or enable **Settings → Pages → main branch** to play it directly on GitHub Pages).

## How it works

- **Planning phase**: draw your snake's path with the mouse or a finger. A virtual circle shrinks as you draw — it represents your remaining reach, which equals your snake's own length. The bigger your snake, the farther it goes.
- **Resolution phase**: both camps move at the same time. Every head that bites an opponent's body **cuts** it (the victim shortens, and dies if it becomes too short). Head-to-head contact is fatal for both, and the arena border is deadly.
- **Power-up pellets** scattered on the map:
  - 🟢 **Grow** — +5 segments
  - 🟡 **Speed** — burst of speed for the next turn
  - 🔵 **Dash** — stored; activate it yourself during planning (⚡ button) to pass through one collision
  - 🔴 **Fireball** — instantly strikes the nearest enemy head
  - 🟣 **Split** — divide your snake into two smaller controllable snakes
  - 🟠 **Bicephalous** — hydra-style: requires 3+ body segments; the body splits into two equal parts (odd surplus goes to the body). The first part stays the body (tail intact), and the second part is split into two equal necks pointing forward from the head root, like a two-headed dragon. Planning order: body, then head A, then head B, both freeing within their neck length.
- Only grow pellets spawn during the first 5 turns.
- The reach circle follows your drawn path (not the head) and shrinks as you draw.
- A distinct tail tip marks the snake's end; the body turns red when one hit away from death — if cut below the minimum, the snake dies with a burst.

## AI difficulties

- **Easy** — watches your movement, flees from you and ignores pellets (plays to lose, but stays in the arena)
- **Medium** — hunts pellets and looks for openings against you
- **Hard** — predicts your planned path every turn, simulates both moves in time and strikes where your body will be (or defends by keeping its distance); arms its stored dash when pinned

## Modes

- Player vs AI (heuristic: hunts pellets, avoids bodies)
- 2 players on the same screen (hot-seat planning, simultaneous resolution)

## Controls

| Input | Action |
|---|---|
| Left click (near head) + drag | Draw the path |
| Right click + drag | Orbit the camera |
| Mouse wheel | Zoom |
