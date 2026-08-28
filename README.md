# Dick's House Defence 🏠🦟

A top-down survival game built from real photos of your house. You're a mosquito.
Rats spray a pixelated purple mist. You throw bricks. Everything is slightly wrong.

## Files

Everything sits flat in one folder — `index.html` plus all the image assets
right alongside it. No subfolders needed.

## Updating your GitHub repo with this version

1. Go to your repo on GitHub.
2. Click into `index.html`, click the pencil (edit) icon, select all, delete,
   paste in the new `index.html` from this folder, commit.
3. For any image that changed (check the file list below), click that file in
   your repo, click the trash/delete icon or use "Add file → Upload files" to
   overwrite it with the new version from this folder, and commit.
   Easiest: just drag ALL the files in this folder into GitHub's upload page
   at once — it will overwrite anything with a matching filename.
4. Give GitHub Pages a minute to rebuild, then reload your live link.

## How to play

- **Left half of the screen**: drag anywhere to move (invisible joystick).
- **Right half of the screen**: tap or hold to throw bricks, straight in
  whatever direction you're currently facing.
- **Desktop**: WASD or arrow keys to move, Spacebar to throw — always active.
- Avoid the purple mist spraying off the rats — it hurts on contact and hurts
  more the longer you stay in it.
- Walls block movement except through the gaps/doorways.
- Kill enemies by hitting them with bricks. They never leave on their own.
- 10 HP. Survive.

## Adding sound later

Drop these five files into the same folder as `index.html`, exact names,
no code changes needed:

| File | When it plays |
|---|---|
| `intro.mp3` | Loops on the home screen |
| `throw.mp3` | Every brick throw |
| `enemy_death.mp3` | When an enemy dies |
| `hero_hit.mp3` | When you take damage |
| `hero_death.mp3` | Game over |

See `GAME_DESIGN.md` for the full mechanics reference.
