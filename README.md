# Portfolio

Static showcase site for the generative-art engines. Light manuscript aesthetic, video-only gallery, ready for GitHub Pages.

## Adding videos

1. Drop your MP4s into folders under `videos/`, one folder per engine:
   ```
   portfolio/
     index.html
     videos/
       waveform/
         piece-1.mp4
         piece-2.mp4
       dijkstra/
         piece-1.mp4
       gulgee/
         …
   ```
2. Open `index.html` and edit the `ENGINES` array near the top of the `<script>` block. For each engine, set:
   - `number` — section numeral (e.g. `'02'`)
   - `title`  — display name
   - `description` — one-line copy below the title (optional)
   - `folder` — path to the folder you used (e.g. `'videos/dijkstra'`)
   - `aspect` — default aspect ratio for that engine's clips (`'1:1'`, `'9:16'`, `'4:5'`, `'16:9'`)
   - `videos` — array of filenames in display order

3. A video can override its engine's default aspect by using the tuple form:
   ```js
   videos: [
     'square.mp4',
     ['reel.mp4', '9:16'],
   ]
   ```

## Instagram link

Set `INSTAGRAM_HANDLE` at the top of the `<script>` block (no `@`). If left at `'your_handle_here'`, the link falls back to `instagram.com`.

## Hosting on GitHub Pages

1. `git init` (if needed), commit `portfolio/` into a repo.
2. Push to GitHub.
3. Repo Settings → Pages → Branch: `main` / folder: `/portfolio` (or move `index.html` to repo root and serve `/`).
4. Done. All asset paths are relative, no build step.

## Performance notes

- Videos use `preload="metadata"` and `autoplay muted loop playsinline`.
- An `IntersectionObserver` pauses off-screen videos so a long page doesn't melt the browser.
- For best result encode MP4s with `-movflags +faststart` so they start playing before fully buffered.
