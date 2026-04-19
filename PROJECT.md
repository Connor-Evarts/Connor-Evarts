# Connor Andree Evarts — Portfolio Website
## Project Notes

Live URL: https://connor-evarts.github.io/Connor-Evarts/
GitHub Repo: https://github.com/Connor-Evarts/Connor-Evarts.git
Local files: /Users/conr/Documents/website/

---

## What's been built

`index.html` (live) = index-2. Active development is on `versions/index-2.html`.

**index-2 features:**
- Animated TV static background (canvas-based, 15fps, brighter in content area)
- Full-page background photos that crossfade based on active scroll section
- Cinzel (nav + exhibition titles) + Cormorant Garamond (body) + Baunk (site name only) font stack (all red)
- Sidebar: name + nav links + profile photo + email/instagram
- Bloom/glow SVG filter on active/hovered text (two-layer: wide halo + mid glow)
- Scroll-spy navigation (active link updates as you scroll)
- Default cursor everywhere; pointer only on Email/Instagram; red crosshair on profile photo
- LOADING... overlay (animated cycling dots, desynced) on title card videos and lightbox media
- Contact panel: slides down over sidebar on Email click, menu fades out, transparent bg; Cancel or second Email click slides it back up. Formspree ID `xrerqnly` active — sends to connor.andree.evarts@gmail.com
- Easter egg: 6 clicks on profile photo → ambient audio loop with volume slider
- Easter egg: hover right screen edge 350ms → background photos revealed, scroll to change

---

## Design values

- Red: `#e83535`
- Red mid (borders, lines): `rgba(232,53,53,0.45)`
- Red dim (subtle lines, separators): `rgba(232,53,53,0.18)`
- Background: pure black `#000`
- Static noise range: 0–23 brightness
- Static centre boost: `fadeIn * fadeOut * 14`
- Font stack (index-1 / original): MingLiU, PMingLiU, STSong, Songti TC, Noto Serif, serif
- Font stack (index-2): Baunk (local, site name only) + Cinzel (nav, labels, exhibition titles) + Cormorant Garamond (body text)
- Sidebar width: 275px
- Bloom filter: wide glow stdDeviation=14 (1.4x red), mid glow stdDeviation=5 (1.5x red, trace green)
- Send Email button: transparent bg, red border (outline style)
- Contact panel text opacity: labels 0.78, placeholders 0.45

---

## File structure

```
website/
├── index.html              ← live site (copy of index-2.html)
├── PROJECT.md              ← this file
├── .gitignore
├── .nojekyll               ← disables Jekyll on GitHub Pages (required for _ filenames)
├── versions/
│   ├── index-1.html        ← backup of original, do not touch (all paths use ../ prefix)
│   ├── index-2.html        ← active version (currently live)
│   └── index-2-backup.html ← snapshot before easter egg / bg photo work (do not touch)
├── Fonts/
│   └── BAUNK FILE/
│       ├── Baunk.otf
│       ├── Baunk.ttf
│       └── Baunk.woff      ← used in index-2 for site name only
├── Audio/
│   ├── Website Loop.m4a    ← easter egg ambient loop (compressed from WAV, 1.1MB)
│   └── Website Loop.wav    ← original (NOT in git)
├── CV/
│   └── Connor Andree-Evarts Artist CV.pdf
├── Exhibitions/
│   ├── BLISS/
│   │   ├── BLISS Documentation/
│   │   │   └── Live/               ← 10 culled JPGs (signal assembly 5_4_25-38/44/46/50/55/58/63/65/66/69)
│   │   └── Vis Files/
│   │       └── Bliss.mp4
│   ├── THEREMONIC/                 ← remaining old JPGs + promo video
│   │   └── Live/                   ← 10 files: _66A9060 (hero) + 9 docs (_66Axxxx, _MG_xxxx)
│   ├── Sentient/
│   │   └── Live/                   ← sentient-1.png (hero), sentient-2.png, sentient-3.png
│   └── Emergence III/              ← old JPGs (not used)
│       └── Live/                   ← emergence3-hero.png + 6 docs (_U5Axxxx)
├── Profile Photo/
│   ├── Vertical/           ← sidebar profile photo slideshow
│   │   ├── Scan 25.jpeg
│   │   ├── Scan 2.jpeg
│   │   ├── Scan 23.jpeg
│   │   ├── Scan 33.jpeg
│   │   └── Scan 4.jpeg
│   └── Horizontal/         ← full-page background photos, crossfade by active section
│       ├── Scan 29.jpeg
│       ├── Scan 30.jpeg
│       ├── Scan 34.jpeg
│       └── Scan.jpeg
├── Selected Works/
│   ├── Anti Shadow/                ← 8 PNGs
│   ├── Aranea_Daemon/              ← 3 PNGs
│   ├── Cthonic Mechanisim/         ← 2 PNGs + 1 MP4
│   ├── encoded topography/         ← 1 MP4
│   ├── Fantasy Island/             ← 1 MP4 (starts at 13s)
│   ├── FarCry Simulation/          ← 3 MP4s + 1 MOV
│   ├── Iris Agate/                 ← 1 MP4
│   ├── Nyctophobia/                ← 1 MP4
│   ├── Touch Grass/                ← 1 MOV + 3 JPGs
│   └── Vein/
│       ├── 1. Vein.mp4             ← compressed for web (was 212MB, now 14MB)
│       └── 1. Vein_original.mp4    ← original full quality (NOT in git)
├── Public Programs/
│   └── Tectonic Noise/             ← 33 JPGs (IMG_2747 = hero)
└── ORIGINAL PHOTOS/                ← full-res masters, DO NOT TOUCH, NOT in git
```

---

## Sections

### Selected Works
- 10 works in a grid (order): Anti Shadow, Vein, Touch Grass, Aranea Daemon, Cthonic Mechanism, Encoded Topography, Iris Agate, Nyctophobia, FarCry Simulation, Fantasy Island
- All video works autoplay looping on load (muted); LOADING... shown until canplay fires
- Image works (Anti Shadow, Aranea Daemon) auto-slideshow: instant cut, 2.8s interval, desynced offsets
- Clicking any work opens a lightbox with all images/videos for that work
- Lightbox: next/prev arrows flanking the content, keyboard nav (arrows + escape), item counter, close button
- Lightbox videos: no controls, click to pause/play, default cursor
- Vein, Nyctophobia, Fantasy Island play with sound in lightbox; all others muted
- FarCry Simulation: first lightbox slide = FC1 + FC2 + FC3 side by side (trio layout), then MVI_3069.MOV
- Background music ducks to 0 when sound-on works play in lightbox, restores after

### Exhibitions
- **BLISS (2025)**: Solo Exhibition. Echo & Bounce, Woolloongabba. Featured video (autoplay, muted, loop); click video opens lightbox with video at index 0, then 10 docs photos. Show-more shows "+2 more".
- **Theremonic (2023)**: Emergence Collective | Vent Space, Southbank. Hero (_66A9060, clickable) + 9 live docs photos + promo video (8 shown, "+1 more"). Clicking hero opens lightbox at index 0.
- **Sentient (2023)**: Emergence Collective | Vent Space, Southbank. Hero: sentient-1.png (clickable, opens lightbox). Docs grid: sentient-2 + sentient-3. All images in Live/.
- **Emergence III (2022)**: Emergence Collective | Vent Space, Southbank. Hero: emergence3-hero.png (clickable, Live/). 6 docs photos in Live/, all shown — show-more button hidden.
- Documentation grids always collapse to exactly one row
- Show-more button sits above the docs grid, below the docs header

### Public Programs
- **2025**: Rīgorabana, The Balawaia | An Extended Sound Performance: Dean Ansell — Fish Lane Town Square, Southbank (text only)
- **2024**: Tectonic Noise | Sound response to Hannah Hallam-Eames' exhibition Time Tunnels — Outer Space, Fortitude Valley. Hero: IMG_2747, + 32 docs photos in expandable grid. Photos open in lightbox.

### CV
- PDF download link (CV/Connor Andree-Evarts Artist CV.pdf)
- Education: BFA QUT (2021–24), Bachelor of Audio Engineering SAE (2016–18)
- Solo Exhibitions: BLISS, Echo & Bounce, Woolloongabba (2025)
- Group Exhibitions: Theremonic, inFORM, Sentient (2023), Emergence x2 (2022)
- Art Related Employment: QUT Visitor Services/Technician (2024–), Emergence Collective Co-Founder (2021–24), Outer Space Volunteer (2021–23)

---

## Profile photo interactions

- Canvas overlay with spring-physics dot shader (red dots, 8px grid, 0.7px radius)
- Dots attracted toward cursor within 40px radius, spring back on mouseleave
- Image tiles warp toward cursor (same spring displacement applied to photo pixels)
- Trail: last 7 frames of dot positions fade out behind movement
- Click imprints: clicking leaves a red crosshair at that position, fades over ~9s (0.007/frame at 15fps)
- Custom red crosshair cursor (SVG data URL) on the profile wrap
- Profile photo cycles through 5 photos every 45s with 6s crossfade

### Easter egg (audio)
- Audio loop (Audio/Website Loop.m4a) loads silently at volume 0 on page load
  - Fallback: starts on first user interaction if autoplay was blocked
- 6 clicks on profile photo → red speaker icon appears bottom-right, volume animates 0→66% over 6s, auto-closes after 1.5s
- Hover speaker → volume slider slides up (stays open while hovering)
- Slider: 1px red track, solid 4-point star thumb (bottom point stretched); scroll on profile image also controls volume
- Click speaker icon = animated mute toggle: fades volume down (250ms), holds, fades back up (400ms) on second click. Shows muted X icon while muted. Cancels and reverses if clicked mid-animation.
- Loop uses 15-second crossfade: two audio instances alternate, fading in/out seamlessly
- Background music ducks when sound-on lightbox items play
- Volume state managed via `volMuteScale` (0–1) multiplier — all audio paths respect it

### Easter egg (background reveal) — index-2 only
- Hovering cursor against the right edge of the screen (full height, 60px strip) for 350ms fades the main content to opacity 0
- Content restores immediately when cursor leaves the right edge
- While revealed: scroll anywhere on the page to cycle through background photos (4x speed, mapped to sections)
- Sidebar stays fully visible at all times
- Background photo section map: works → Scan 29, exhibitions → Scan 30, program → Scan 34, cv → Scan

---

## Lightbox

- Generic `openLightbox(items, startIndex, title)` handles works, exhibitions, and public program docs
- Backdrop: frosted blur with gradient — transparent on left (menu glows through), dark on right
- Arrows sit on either side of the media (not screen edges)
- Special `trio` item type renders 3 videos side by side (used by FarCry Simulation)
- LOADING... indicator (animated cycling dots) shown until media fires canplay/load

---

## Image compression

All images resized to max 2000px on the long edge using macOS `sips`. Originals in ORIGINAL PHOTOS/ (not in git).

**Important:** macOS screenshot filenames contain a Unicode narrow no-break space (U+202F) before "am/pm" — rename them to simple names before adding to the project or they will fail to load on GitHub Pages.

To compress a single image:
```
sips -Z 2000 "path/to/image.jpg"
```
To batch compress a folder:
```
find "/Users/conr/Documents/website/Exhibitions/NEWFOLDER" -type f -name "*.jpg" -exec sips -Z 2000 {} \;
```
To rename macOS screenshots safely (use glob, not typed filename):
```
cd "/path/to/folder" && for f in Screenshot*.png; do mv "$f" new-name.png; done
```

---

## How to update the site

1. Edit `versions/index-2.html` or add files to relevant folders
2. Compress any new images with sips (see above), rename screenshots to clean names
3. In Terminal:
```
cd /Users/conr/Documents/website
cp versions/index-2.html index.html
sed -i '' 's|\.\./||g' index.html
sed -i '' '/<!-- DEV-ONLY-START -->/,/<!-- DEV-ONLY-END -->/d' index.html
git add .
git commit -m "describe what you changed"
git push
```
Note: the first `sed` strips the `../` path prefix. The second strips the dev-only reorder tool so it never appears on the live site.
4. Site updates at https://connor-evarts.github.io/Connor-Evarts/ within 1–5 minutes

---

## Adding new content

### New selected work
1. Add folder to Selected Works/ with images/video
2. Add a `.work-item` div in the HTML (Selected Works section)
3. Add entry to `workFiles` object in the JS
- Video title card: `<video src="..." muted loop autoplay playsinline></video>`
- Image title card: `<img src="..." loading="lazy">`

### New exhibition with photos
1. Add folder to Exhibitions/ with photos, compress with sips, rename any screenshots
2. Add `.ex-entry` block in the HTML (Exhibitions section)
3. Add JS block for the docs grid (copy the Theremonic pattern)

### New public program event with photos
1. Add `.prog-item` to the Public Programs section in HTML
2. Add hero image and docs grid markup (copy the Tectonic Noise pattern)
3. Add photos to Public Programs/[name]/ folder and compress
4. Add JS block (copy the Tectonic Noise pattern)

---

## ⚠️ Pick up here next session
- Do a visual pass of the live site — check all works in lightbox, exhibitions, and public programs for remaining image artifacts
- JS console error on live site: `Cannot access 'bgDuckMul' before initialization` at duckBackground — investigate and fix
- Consider making the site mobile friendly

## Known future tasks
- Add photos/media to Rīgorabana public program when available
- The repo is named Connor-Evarts (not Connor-Evarts.github.io) — this is fine, GitHub Pages still works via Settings → Pages

## What was done (this session)
- All exhibitions now use culled `Live/` subfolders for documentation photos (note capital L — GitHub Pages sensitive)
- BLISS: 10 live docs photos (38,44,46,50,55,58,63,65,66,69); video is now index 0 in lightbox, docs follow
- BLISS video: click opens lightbox (video first, then docs) — was play/pause
- Theremonic: 9 live docs photos from `THEREMONIC/Live/`; hero `_66A9060.jpg` moved into `Live/`
- Sentient: all 3 images moved into `Sentient/Live/`; paths updated in HTML + JS
- Emergence III: 6 live docs photos + hero from `Emergence III/Live/`; show-more button hidden (6 < 8)
- Hero images (Theremonic, Sentient, Emergence III) are now clickable — open lightbox at index 0
- Show-more buttons auto-hide when photo count ≤ 8 (INITIAL)

## What was done (last session)
- Fixed flags not loading on live site — path was `flags/` in HTML but folder is `Flags/` (GitHub Pages is case-sensitive on Linux)
- Always match folder capitalisation exactly — see Important Notes below

## What was done (previous session)
- Added acknowledgement of country overlay (Turrbal & Jagera peoples, flags bottom-left, credits, click to dismiss)
- Flags folder added: First Nations, Palestine, Queer Trans
- Replaced Vein video title card with GIF (Gifs/vein.gif) — 4.6MB, 600×400, 12fps, t=13–17s
- Cthonic Mechanism title card switched to image slideshow (cthonic-1 → cthonic-2)
- Works grid reordered: Anti Shadow, Vein, Touch Grass, Encoded Topography, Nyctophobia, FarCry, Fantasy Island, Iris Agate, Cthonic Mechanism, Aranea Daemon
- CV group exhibitions updated: added venue/org context, removed duplicate 2022 Emergence, corrected inFORM → QUT Graduate Showcase
- Fixed white/blue edge artifacts: anti-shadow-4 (5px left), anti-shadow-7 (2px right), aranea-1 (1px top), aranea-2 (6px top+right macOS chrome bleed)
- Added dev-only drag-to-reorder mode to index-2.html (Shift+D) — auto-stripped from live build by deploy sed command

## Important notes
- `.nojekyll` file in repo root is critical — without it GitHub Pages (Jekyll) silently blocks all files whose names start with `_` (affects all THEREMONIC + Emergence III photos)
- Audio is M4A not WAV — WAV original is gitignored
- All paths are case-sensitive on GitHub Pages (Linux): `Fonts/`, `Profile Photo/`, `Audio/`, `Touch Grass/`, `THEREMONIC/`, `Emergence III/`, `Sentient/`, `Live/` (exhibition live subfolders)
- Formspree contact form: ID `xrerqnly`, destination connor.andree.evarts@gmail.com. First submission requires Formspree verification email.
