# Dick's House Defence 🏠🦟

A top-down survival game built from real photos of your house. You're a mosquito. Rats spray glowing mist. You throw bricks. Everything is slightly wrong. Nobody asked for this.

Play it here once deployed: `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/`

## How to put this on GitHub Pages (free hosting)

1. Create a new **public** repository on GitHub.
2. Upload everything in this folder — `index.html`, the `assets/` folder, and this `README.md` — keeping the same structure.
3. In the repo, go to **Settings → Pages**.
4. Under **Source**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then **Save**.
5. Wait a minute or two, then your game is live at:
   `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/`
6. Share that link — works on phones and desktop.

## How to play

- **Left thumb**: drag the joystick to move.
- **Right thumb**: tap (or hold) THROW to spam bricks in whatever direction you're facing.
- Avoid the glowing green mist around the rats — it hurts, and hurts more the longer you stand in it.
- Kill enemies by hitting them with bricks. They never go away on their own.
- You've got 10 HP. Survive.

## Adding sound later

Drop these five files into the `assets/` folder with these **exact names** — no code changes needed, the game will just start using them:

| File | When it plays |
|---|---|
| `intro.mp3` | Loops on the home screen |
| `throw.mp3` | Every brick throw |
| `enemy_death.mp3` | When an enemy dies |
| `hero_hit.mp3` | When you take damage |
| `hero_death.mp3` | Game over |

## Notes

- Everything is one `index.html` file plus an `assets/` folder — no build step, no server needed beyond GitHub Pages itself.
- See `GAME_DESIGN.md` for the full design doc and mechanics reference.
