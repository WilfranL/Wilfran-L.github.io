# Wilfran Loera: playable portfolio

A handmade-craft 2D platformer. Visitors walk through the level to find my
background, projects, experience, skills, leadership, and contact links.
There's also a "Skip to plain version" button that opens a normal résumé page.

Plain HTML, CSS, and JavaScript. No build step, no image files.

## Edit your info

Everything lives in **`js/content.js`**. Change a value, save, and refresh.
Both the game and the plain résumé update.

| Want to…                         | Edit this in `content.js`                         |
| -------------------------------- | ------------------------------------------------- |
| Change name or tagline           | `name`, `tagline`                                 |
| Recolor your doll (Patch)        | `player.knit`, `player.scarf`, `player.tuft`, optional `player.patch` |
| Give your doll a hat             | `player.hat`: `"none"`, `"beanie"`, or `"crown"`  |
| Change the Jukebox song          | `music.youtubeId` (the part after `v=` in a YouTube link), `music.title`, `music.artist`. Set `youtubeId` to `""` to use only the built-in soundtrack. |
| Add the Riftline game link       | `projects[0].link`                                |
| Add Riftline screenshots         | Put images in an `img/` folder, then list them in `projects[0].screenshots`, e.g. `["img/riftline-1.png"]`. The first one also appears on the in-level screen. |
| Change your contact email        | `contact.email` (leave `""` to send "Contact me" to LinkedIn) |
| Add or remove skills             | `skills` (one prize bubble each; the Skills area grows to fit) |
| Change bonus bubble facts        | `bonus` (up to 3 per area)                        |
| Update the receipt prop          | `experience[0].receipt`                           |

Keep your phone number off the site. It isn't in `content.js`, so it never appears.

## Music

The Music button opens the Jukebox. It has two tracks:

- **Your YouTube song**, played in YouTube's own player. YouTube requires that
  player to stay visible while it plays, so it sits in the Jukebox panel.
  Closing the Jukebox stops it.
- **Patchwork Parade**, an original loop generated in the browser with the Web
  Audio API. It's the fallback when YouTube can't load.

Sound effects are separate (the Sound button) and start off.

## Preview on your computer

From this folder, run:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy to GitHub Pages

1. Create a new public repo on GitHub. Naming it `Wilfran-L.github.io` gives
   you the address `https://wilfran-l.github.io`.
2. Upload the contents of this folder (`index.html`, `resume.html`, `css/`,
   `js/`) to the repo's root, using "Add file → Upload files" or git.
3. In the repo, go to **Settings → Pages**. Under "Build and deployment",
   choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. Wait a minute or two, then visit your site. Every push to `main` redeploys.

## Files

- `index.html`: the game page and its HTML overlay (HUD, info cards, touch buttons)
- `resume.html`: the plain résumé as its own page (good for linking directly)
- `css/style.css`: all styles
- `js/content.js`: **your info**
- `js/level.js`: the level layout (where areas, platforms, and bubbles go)
- `js/game.js`: controls, physics, camera, main loop
- `js/art.js`, `js/sprites.js`, `js/props.js`: everything drawn on the canvas
- `js/ui.js`: info cards, finish screen, plain-version overlay, touch buttons
- `js/audio.js`: Web Audio sound effects and the original soundtrack
- `js/plain.js`: builds the plain résumé from `content.js`

## Controls

- Move: A / D or ← / →
- Jump: W, Space, or ↑ (hold longer to jump higher)
- Phones: on-screen buttons
- Stop near a sign to read its card.
- Red spring pads launch you high. Moving platforms carry you.
- Fall into the rift and you respawn at the last flag. The Skills area's cloud pit just bounces you back up.
