# Dick's House Defence 🏠

## Concept
Top-down 2D survival game. A custom hero (asset TBD) explores a world built from real photos of your house/surroundings, dodging a stationary rotating hazard (a rat spewing glowing mist) and fighting off waves of increasingly ridiculous roaming enemies (random PNGs) by throwing bricks. Built in plain HTML/JS/Canvas — hosted free on GitHub Pages.

---

## How It Plays

1. **The World** — A ~1600×1600px map built from real photographed areas (garden, pipe, drain, bathroom, tile floor, etc.), connected by gaps/doorways in dividing walls. Camera follows the hero and only shows a small window into the map at any time.
2. **The Hero** — Custom character (you're building this asset). 10 HP total. Moved via a virtual joystick, throws unlimited bricks via a throw button.
3. **The Rat — Stationary Hazard** — Fixed in specific spots around the map. Rotates in place, constantly emitting a glowing mist hazard around itself. Touching it hurts. Standing in it hurts more, continuously.
4. **The Enemies** — Random ridiculous PNGs (skulls, mummy heads, mirrored faces) that spawn over time in whatever area the hero is in, and chase them down.
5. **The Goal** — Survive. Score = enemies killed. Game ends when hero's 10 HP hits 0.

---

## Controls

| Input | Action |
|-------|--------|
| **Left side of screen**: virtual joystick (drag) | Move hero around the world |
| **Right side of screen**: throw button (tap) | Throws a brick straight in the hero's current facing direction |
| Desktop fallback: WASD/arrows to move, click/spacebar to throw | Same actions, desktop-friendly |

Fully touch-friendly — built for a phone screen held in both hands, thumbs on either side.

---

## World & Camera

- **Map size**: ~1600×1600px (scaled down from an original 10,000×10,000 plan — full resolution isn't visible on screen anyway since the camera is always zoomed in close, so this keeps load times fast).
- **Background**: a clean version of the user's photographed floor/areas collage (no annotations — provided separately), divided into distinct areas connected by gaps in dividing walls.
- **Camera**: follows the hero, centered on them at all times.
- **Spawn point**: hero starts at a fixed spawn location in "Area 1" at game start.
- No area name / title-card popups (dropped from scope).

---

### Hero — Mosquito
- Custom asset: user's own phone photo of a mosquito/crane-fly-type bug (long thin legs, small body).
- Animated **in-engine** from the single image — no GIF file needed:
  - **Idle**: subtle body bob, maybe a slight leg twitch.
  - **Moving**: legs/body scuttle-wiggle effect while walking.
  - Faces the direction of its last movement input.
- **Health**: 10 HP total.
- Controlled via joystick (move) + throw button (attack).

---

## The Rat — Stationary Hazard

- Size: 20 (matches user's asset scale).
- Placed at fixed positions around the map (user will specify exact locations per area).
- Continuously rotates in place.
- Constantly emits a glowing mist/pixie-dust hazard extending ~3 blocks out from itself.
- **Damage rule**:
  - Entering the mist: instant **-3 HP** the moment of contact.
  - Remaining inside the mist: **-2 HP per second** for every additional second still inside.
- **Physical collision**: if the hero ends up behind/inside the rat's own body (not just the mist), the rat physically shoves/rolls the hero out of the way — like a log rolling a ball along with it. This is a positional push, not damage.

---

## Bricks — Throwing Mechanic

- **Unlimited ammo** — throw as fast as the throw button is tapped. No cooldown, no reload.
- Bricks always fly straight in the hero's current facing direction (no auto-aim), at **2× the hero's movement speed**.
- **Spin**: bricks rotate fast in flight, shuriken-style — fast enough to feel violent, slow enough to still read clearly as a brick.
- A brick disappears on hitting an enemy, or after traveling a fixed max distance (so bricks thrown into empty space don't live forever).

---

## Wave Enemies — Roaming, Chase the Hero

- **Enemy contact damage**: touching the hero deals **-1 HP** per touch (separate from the rat's mist damage).
- **Persistence**: enemies never despawn on their own — the only way to remove an active enemy is to kill it.
- Pool of enemy PNGs (skull, mummy head, two mirrored-face heads, more to be added) — **one is chosen at random** for each spawn.
- **Spawn rate scales with continuous time spent in an area**, minute by minute:
  - Minute 1 in an area → spawn 1 enemy every 10 seconds.
  - Minute 2 → spawn 2 enemies every 10 seconds.
  - Minute 3 → spawn 3 enemies every 10 seconds.
  - Pattern continues: **minute N → N enemies per 10 seconds**, uncapped as long as the hero stays in that area.
- **Persistence across areas**:
  - Enemies already spawned in an area do **not** despawn, and do **not** follow the hero when they leave that area.
  - When the hero returns to a previously-visited area, the existing enemy count there is *not* reset to zero — new spawns resume adding on top of what's already present.
  - The per-minute spawn-rate escalation restarts from minute 1 each time the hero (re-)enters an area, but the standing enemy count from prior visits remains.
  - A brand-new area (never visited) starts fresh: 1 enemy at minute 1, escalating from there.

---

## Visuals & Feel — Pure Chaos Energy

- **Home Screen**: Full-screen custom background (the UV-lit cotton swabs / Amul brownie photo). Hand-drawn red "PLAY" button. Intro music loops here until tapped.
- **In-game HUD**: HP (out of 10), current area, and kill score displayed — exact style TBD once hero asset is in.
- **Settings menu** (via hand-drawn red "SETTING" button): two options —
  - **Sound**: On / Off toggle.
  - **"Flag this game for terrorism"**: does nothing except show a fake "Complaint sent." popup message.
- **Replay**: hand-drawn red "REPLAY" button shown on the game-over screen.
- **Enemy death**: pops/disappears with a small effect, plays death sound.
- **Hero hit**: hero briefly swells (scales up slightly) with a red tint flash, then returns to normal size/color — same effect used consistently as the universal "took damage" feedback.
- **Enemy hit**: same swell + red tint flash on any hit, whether or not it's a killing blow.
- **Hero death (0 HP)**: game over — dramatic effect, death sound, final score shown, REPLAY button.
- **General vibe**: everything is slightly wrong on purpose — a rotating rat sprays glowing mist, you fight mirrored-face heads by throwing bricks, and settings let you "report the game for terrorism." Nobody asked for this. It exists anyway.

---

## Sound Design

Sound files will be added **after** the game is built and playable — the user wants to see/feel the visuals first, then record sounds that actually match. The code will include all the play-sound hooks wired to the right moments, using placeholder/silent stand-ins until real files are dropped into `assets/` with these exact names:

| Sound | File | When It Plays |
|-------|------|----------------|
| Intro/menu music | `intro.mp3` | Loops on home screen, stops on game start |
| Brick throw | `throw.mp3` | Every time the hero throws a brick |
| Enemy death | `enemy_death.mp3` | When any roaming enemy dies |
| Hero hit | `hero_hit.mp3` | When hero takes damage (rat mist or enemy contact) |
| Hero final death | `hero_death.mp3` | When HP hits 0 (game over) |

---

## Assets — Status

### Images
| Asset | File | Status |
|-------|------|--------|
| Home screen bg | `homescreen.png` | ✅ Provided (UV cotton swabs photo) |
| PLAY button | `btn_play.png` | ✅ Provided |
| REPLAY button | `btn_replay.png` | ✅ Provided |
| SETTING button | `btn_setting.png` | ✅ Provided |
| Hero (mosquito) | `hero.png` | ✅ Provided |
| Rat (hazard) | `rat.png` | ✅ Provided |
| Brick (projectile) | `brick.png` | ✅ Provided |
| Enemy 1 | `enemy1.png` (skull) | ✅ Provided |
| Enemy 2 | `enemy2.png` (mummy head) | ✅ Provided |
| Enemy 3 | `enemy3.png` (mirrored face v1) | ✅ Provided |
| Enemy 4 | `enemy4.png` (mirrored face v2) | ✅ Provided |
| More enemies | *(TBD)* | ⏳ User making more |
| World/floor map (clean, no annotations) | `floor.png` | ✅ Provided |
| Rat placement positions per area | *(reference image w/ blue dots)* | ✅ Provided |

### Sounds
| Asset | File | Status |
|-------|------|--------|
| Intro music | `intro.mp3` | ⏳ Added after build |
| Brick throw | `throw.mp3` | ⏳ Added after build |
| Enemy death | `enemy_death.mp3` | ⏳ Added after build |
| Hero hit | `hero_hit.mp3` | ⏳ Added after build |
| Hero final death | `hero_death.mp3` | ⏳ Added after build |

### Still Needed Before Build
Nothing — all image assets are in. Sound files come after the first playable build, once the user has seen the visuals in motion.

---

## File Structure (what goes on GitHub)

```
your-repo/
├── index.html
├── assets/
│   ├── homescreen.png
│   ├── floor.png
│   ├── hero.png
│   ├── rat.png
│   ├── brick.png
│   ├── enemy1.png
│   ├── enemy2.png
│   ├── enemy3.png
│   ├── enemy4.png
│   ├── btn_play.png
│   ├── btn_replay.png
│   ├── btn_setting.png
│   ├── intro.mp3
│   ├── throw.mp3
│   ├── enemy_death.mp3
│   ├── hero_hit.mp3
│   └── hero_death.mp3
└── README.md
```

---

## Hosting on GitHub Pages (free, zero cost)

1. Create a new GitHub repo (public).
2. Upload all files above.
3. Go to repo **Settings → Pages → Source → main branch → / (root)**.
4. Game is live at `https://yourusername.github.io/repo-name/`.
5. Share that link on LinkedIn.

---

## Scope Boundary — What This WON'T Have

- No pathfinding / obstacles for enemy movement beyond direct chase.
- No save/load — each session is fresh.
- No area name/title-card popups.
- Sound requires one tap to start (browser autoplay policy) — home screen PLAY tap handles this.

---

## Optional Extras (only if wanted later)

- High score saved in browser localStorage.
- Boss variant of the rat or an enemy with more HP.
- Combo counter for fast kills.
- Random taunt text on kills ("BRICK'D", "GET OUT OF MY HOUSE", "DENIED").
