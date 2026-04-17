# Connor Andree Evarts — Portfolio Website
## Project Notes

Live URL: https://connor-evarts.github.io
GitHub Repo: https://github.com/Connor-Evarts/Connor-Evarts.git
Local files: /Users/conr/Documents/website/

---

## What's been built

A single-file art portfolio website (index.html) with:
- Animated TV static background (canvas-based, 15fps, brighter in content area)
- Red border frame around the whole page
- MingLiU serif font in red throughout
- Sidebar: name + nav links + profile photo (centred between CV and email) + email/instagram
- Bloom/glow effect on active text (SVG filter, two-layer: wide halo + mid glow)
- Scroll-spy navigation (active link updates as you scroll)
- Default cursor everywhere; pointer only on Email/Instagram; red crosshair on profile photo

---

## Design values

- Red: `#e83535`
- Red mid (borders, lines): `rgba(232,53,53,0.45)`
- Red dim (subtle lines, separators): `rgba(232,53,53,0.18)`
- Background: pure black `#000`
- Static noise range: 0–23 brightness
- Static centre boost: `fadeIn * fadeOut * 14`
- Font stack: MingLiU, PMingLiU, STSong, Songti TC, Noto Serif, serif
- Sidebar width: 275px
- Bloom filter: wide glow stdDeviation=14 (1.4x red), mid glow stdDeviation=5 (1.5x red, trace green)

---

## File structure

```
website/
├── index.html              ← entire website (HTML + CSS + JS)
├── PROJECT.md              ← this file
├── .gitignore
├── audio/
│   └── Website Loop.wav    ← easter egg ambient loop
├── CV/
│   └── Connor Andree-Evarts Artist CV.pdf
├── Exhibitions/
│   ├── BLISS/
│   │   ├── BLISS Documentation/    ← 42 JPGs (signal assembly 5_4_25-30 to 73)
│   │   └── Vis Files/
│   │       └── Bliss.mp4
│   └── THEREMONIC/                 ← 20 JPGs (_66Axxxx, _MG_xxxx)
├── profile photo/
│   └── Scan 25.jpeg
├── Selected Works/
│   ├── Anti Shadow/                ← 8 PNGs
│   ├── Aranea_Daemon/              ← 3 PNGs
│   ├── Cthonic Mechanisim/         ← 2 PNGs + 1 MP4
│   ├── encoded topography/         ← 1 MP4
│   ├── FarCry Simulation/          ← 3 MP4s + 1 MOV
│   ├── Iris Agate/                 ← 1 MP4
│   ├── Nyctophobia/                ← 1 MP4
│   ├── touch grass/                ← 1 MOV + 3 JPGs
│   └── Vein/
│       ├── 1. Vein.mp4             ← compressed for web (was 212MB, now 14MB)
│       └── 1. Vein_original.mp4    ← original full quality (NOT in git)
├── Public Programs/                ← empty, ready for future photos
└── ORIGINAL PHOTOS/                ← full-res masters, DO NOT TOUCH, NOT in git
```

---

## Sections

### Selected Works
- 9 works in a grid (order): Anti Shadow, FarCry Simulation, Aranea Daemon, Cthonic Mechanism, Encoded Topography, Iris Agate, Nyctophobia, Vein, touch grass
- All video works autoplay looping on load (muted)
- Image works (Anti Shadow, Aranea Daemon) auto-slideshow: instant cut, 2.8s interval, desynced offsets, 2s first interval
- Clicking any work opens a lightbox with all images/videos for that work
- Lightbox: next/prev arrows flanking the content, keyboard nav (arrows + escape), item counter, close button
- Lightbox videos: no controls, click to pause/play, default cursor
- Vein and Nyctophobia play with sound in lightbox; all others muted
- FarCry Simulation: first lightbox slide = FC1 + FC2 + FC3 side by side (trio layout), then MVI_3069.MOV

### Exhibitions
- **BLISS (2025)**: featured video (autoplay, muted, loop, click to pause) + 42 documentation photos (8 shown, expandable). Photos open in lightbox.
- **Theremonic (2023)**: featured hero image (_66A9060) + 19 documentation photos (8 shown, expandable). Photos open in lightbox.
- Documentation grids always collapse to exactly one row
- Remaining exhibitions (inFORM, Sentient, Emergence x2) are text-only — no photos yet

### Public Programs
- 2025: Rīgorabana, The Balawaia | An Extended Sound Performance: Dean Ansell — Fish Lane Town Square, Southbank
- 2024: Tectonic Noise | Sound response to Hannah Hallam-Eames' exhibition Time Tunnels — Outer Space, Fortitude Valley
- Ready to add photos/media when available

### CV
- PDF download link (CV/Connor Andree-Evarts Artist CV.pdf)
- Education: BFA QUT (2021–24), Bachelor of Audio Engineering SAE (2016–18)
- Solo Exhibitions: BLISS, Echo & Bounce, Woolongaba (2025)
- Group Exhibitions: Theremonic, inFORM, Sentient (2023), Emergence x2 (2022)
- Art Related Employment: QUT Visitor Services/Technician (2024–), Emergence Collective Co-Founder (2021–24), Outer Space Volunteer (2021–23)

---

## Profile photo interactions

- Canvas overlay with spring-physics dot shader (red dots, 8px grid, 0.7px radius)
- Dots attracted toward cursor within 40px radius, spring back on mouseleave
- Image tiles warp toward cursor (same spring displacement applied to photo pixels)
- Trail: last 7 frames of dot positions fade out behind movement
- Click imprints: clicking leaves a red crosshair at that position, fades over ~45 frames
- Custom red crosshair cursor (SVG data URL) on the profile wrap

### Easter egg
- 6 clicks on profile photo → red speaker icon appears bottom-right
- Hover speaker → volume slider slides up
- Slider controls volume of ambient audio loop (audio/Website Loop.wav)
- Loop uses 15-second crossfade: two audio instances alternate, fading in/out seamlessly

---

## Lightbox

- Generic `openLightbox(items, startIndex, title)` handles both works and exhibition docs
- Backdrop: frosted blur with gradient — transparent on left (menu glows through), dark on right
- Arrows sit on either side of the media (not screen edges)
- Special `trio` item type renders 3 videos side by side (used by FarCry Simulation)

---

## Image compression

All images in Exhibitions/ and Selected Works/ have been resized to max 2000px on the long edge using macOS `sips`. Average file size ~841KB. Originals stored in ORIGINAL PHOTOS/ (not in git).

To compress new images added in future, run in Terminal:
```
sips -Z 2000 "path/to/image.jpg"
```
Or to batch compress a whole folder:
```
find "/Users/conr/Documents/website/Exhibitions/NEWFOLDER" -type f \( -iname "*.jpg" -o -iname "*.png" \) -exec sips -Z 2000 {} --out {} \;
```

---

## How to update the site

1. Edit index.html (or add files to the relevant folders)
2. Compress any new images with sips (see above)
3. In Terminal:
```
cd /Users/conr/Documents/website
git add .
git commit -m "describe what you changed"
git push
```
4. Site updates at https://connor-evarts.github.io within ~1 minute

---

## Adding new content

### New selected work
1. Add folder to Selected Works/ with images/video
2. Add a `.work-item` div in the HTML (Selected Works section)
3. Add entry to `workFiles` object in the JS
- Video title card: `<video src="..." muted loop autoplay playsinline></video>`
- Image title card: `<img src="..." loading="lazy">`

### New exhibition with photos
1. Add folder to Exhibitions/ with photos
2. Compress photos (sips command above)
3. Add `.ex-entry` block in the HTML (Exhibitions section)
4. Add JS block for the docs grid (copy the Theremonic pattern)

### New public program event
1. Add `.prog-item` to the Public Programs section in HTML
2. Add photos/media to Public Programs/ folder when available

---

## Known future tasks
- Add photos/media to Public Program events when available
- GitHub Pages is live — future updates just need git push
- Consider TV turn-on intro animation (static resolves into page on load)
- The repo is named Connor-Evarts (not Connor-Evarts.github.io) — this is fine, GitHub Pages still works via Settings → Pages
