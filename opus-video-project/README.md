# Opus Video Project

A reusable system for producing animated explainer videos. Code (how things move)
is kept separate from content (what each video says) and from media (what it shows),
so a new video means new content, not new code.

## Structure

```
opus-video-project/
├── assets/            Visual media used inside videos
│   ├── images/        Photos, screenshots, raster graphics
│   ├── icons/         Small UI/symbol icons (prefer SVG)
│   ├── logos/         Brand and partner logos
│   ├── illustrations/ Larger vector artwork and characters
│   ├── backgrounds/   Full-frame backgrounds and textures
│   └── footage/       Video clips (stock, screen recordings)
├── audio/
│   ├── music/         Background music beds
│   ├── sfx/           Whooshes, clicks, pops, UI sounds
│   └── voiceover/     Narration files, one folder per video
├── fonts/             Font files (.ttf/.otf/.woff2) + licenses
├── reference/         Planning material — never rendered
│   ├── scripts/       Narration and video scripts
│   ├── storyboards/   Sketches, frame plans, shot lists
│   └── moodboard/     Style inspiration, competitor examples
├── content/           Per-video data (text, timings, scene order)
│   └── _template/     Starter content to copy for a new video
├── src/               The reusable animation engine
│   ├── theme/         Design tokens: colors, type scale, spacing
│   ├── animations/    Easing curves, timing presets, motion helpers
│   ├── transitions/   Scene-to-scene transitions (fade, wipe, slide)
│   ├── components/    Building blocks: titles, captions, callouts, charts
│   ├── scenes/        Scene templates composed from components
│   ├── videos/        Video compositions: wire content into scenes
│   └── utils/         Shared helpers (timing math, asset loading)
└── output/            Generated files — safe to delete and re-render
    ├── renders/       Final exported videos
    ├── previews/      Low-res / draft renders for review
    └── stills/        Exported frames (thumbnails, posters)
```

## How the layers fit together

1. **theme** + **animations** define the look and motion language.
2. **components** use them to build reusable on-screen elements.
3. **scenes** arrange components into templates (intro, bullet list, comparison, outro…).
4. **content/<video-name>/** supplies the actual text, assets and timings.
5. **videos** combine a content folder with scenes and render to **output/**.

## Conventions

- New video: copy `content/_template/` to `content/<video-name>/`.
- File names: lowercase-kebab-case (`product-intro.mp3`, `hero-bg.png`).
- Store voiceover per video: `audio/voiceover/<video-name>/`.
- Nothing in `reference/` or `output/` should be imported by `src/`.
- `.gitkeep` files only keep empty folders in version control; delete once a folder has real files.
