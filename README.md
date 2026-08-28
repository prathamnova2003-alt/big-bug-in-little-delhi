# Dick's House Defence 🏠🦟

A top-down survival game built from real photos of your house. You're a mosquito.
Rats spray a pixelated purple mist. You throw stones (then bricks). Everything
is slightly wrong. Nobody asked for this.

## Files

Everything sits flat in one folder — `index.html` plus all the image assets
right alongside it. No subfolders needed.

## Updating your GitHub repo

1. Unzip this download.
2. Go to your repo on GitHub → **Add file → Upload files**.
3. Select every file in the unzipped folder and drag them all in.
4. Scroll down and click the green **Commit changes** button — this is the
   step that actually saves it. Nothing is saved until you click it.
5. Give GitHub Pages a minute to rebuild, then hard-refresh your live link
   (Ctrl+Shift+R / Cmd+Shift+R).

## How to play

- **Left half of the screen**: drag anywhere to move (invisible joystick).
- **Right half of the screen**: tap or hold to throw, straight in whatever
  direction you're currently facing.
- **Desktop**: WASD or arrow keys to move, Spacebar to throw — always active.
- You start with a **stone** (1 damage). Find a glowing **brick pickup** on
  the ground to permanently upgrade to the **brick** (10 damage — one-shots
  most enemies).
- Enemies have 2 HP, so stones take two hits to kill.
- The purple mist spraying off each rat IS the actual hitbox — stand in the
  stream and it hurts (a burst on entry, then more per second you stay in
  it); stand next to a rat but out of its current spray direction and
  you're safe.
- Walls block movement except through the gaps/doorways.
- 10 HP. Survive.

## Adding sound later

Drop these five files into the same folder as `index.html`, exact names,
no code changes needed:

| File | When it plays |
|---|---|
| `intro.mp3` | Loops on the home screen |
| `throw.mp3` | Every throw |
| `enemy_death.mp3` | When an enemy dies |
| `hero_hit.mp3` | When you take damage |
| `hero_death.mp3` | Game over |

## Still pending

- **stone.png** — the starting weapon currently renders as a plain grey
  circle placeholder until this is provided.
- **Mosquito walk-cycle asset** — legs currently don't animate; a proper
  multi-frame asset is planned.

See `GAME_DESIGN.md` for the full mechanics reference.
