# Solo Leveling Production Rules & Instructions

This document governs all automated video generation exclusively within the `solo leveling/` series directory. Every agent operating here must adhere strictly to these rules.

## Core Mandate: Automatic Dual Output (Full Video + Promo Short)
Whenever the user requests video creation for ANY chapter or story arc in Solo Leveling:
1. **Automatically produce BOTH:**
   - A **Full Detailed Recap Video** (16:9 Landscape)
   - A **Music-Only Promo Short** (9:16 Vertical)
2. **Never require the user to ask separately.** Produce both automatically in the standard directory structure.

---

## Directory Organization
Every chapter must strictly follow this folder hierarchy:
```
solo leveling/chapter [X]/
├── full video/
│   ├── Solo_Leveling_Chapter_[X]_Full_Video.mp4  (16:9 Landscape - 1920x1080)
│   ├── narration.md                              (Complete scene-by-scene script)
│   └── audio_en/                                 (Intermediate audio files)
└── short/
    └── Solo_Leveling_Chapter_[X]_Promo_Short.mp4 (9:16 Vertical - 1080x1920)
```

---

## Pipeline Standards

### 1. Panel Extraction & Slicing
- Raw webtoon strips are continuous images (~100,000+ pixels tall) split arbitrarily by downloaders with blank or 10-pixel spacers.
- **NEVER** map scenes directly to downloaded raw image filenames.
- **ALWAYS** detect actual panel boundaries using whitespace/blackspace/row-variance or slice into distinct, logical story scenes.
- Every single plot beat and panel must be covered without skipping.

### 2. Full Video (16:9 Landscape 1920x1080)
- **Resolution:** 1920x1080 Landscape widescreen.
- **Atmospheric Background:** Never leave plain black borders. Create an ambient, Gaussian-blurred (`radius=25`), dimmed (`brightness=0.35`) backdrop from that exact panel to create a rich 3D depth-of-field effect.
- **Dynamic Camera Moves:**
  - **Ken Burns Zoom-In (1.0x -> 1.15x):** Close-ups, expressions, dramatic tension, roars.
  - **Ken Burns Zoom-Out (1.15x -> 1.0x):** Wide-angle reveals, shockwaves, aftermath.
  - **Vertical Slide / Pan:** Tall action panels and full-body character reveals smoothly pan from top to bottom so all artwork is clearly visible.
- **Narration & Pacing:**
  - **Language:** English (`en-US-ChristopherNeural` default).
  - **Pacing:** Natural, human conversational pace (**+0% rate**). Do NOT speed up (+15% or fast-forward). Include a subtle pause (0.35s) between panels so listeners can absorb the art and narrative.
  - **Audio Mix:** Voice at ~1.25x volume with subtle, atmospheric background music (e.g. `space_song.mp3`) at 4-5% volume.
- **Documentation:** Always generate `narration.md` inside `full video/` documenting the complete script and camera move for every scene.

### 3. Promo Short (9:16 Vertical 1080x1920)
- **Resolution:** 1080x1920 Vertical Shorts format.
- **Duration:** 20 to 30 seconds of high-intensity hook.
- **Audio:** **MUSIC ONLY** (no voiceover / zero talking). Use iconic high-energy phonk / trailer tracks (e.g., `neon_blade.mp3`, `metamorphosis.mp3`, `murder_in_my_mind.mp3`).
- **Editing Style:**
  - Fast, rhythmic cuts synced to the music beats (0.7s to 1.5s per shot).
  - White impact flashes on beat drops.
  - Punch zooms and screen shakes for heavy impacts.
  - Tension tints (e.g., red vignette on fatal strikes).
  - Dramatic fade-to-black leaving a cliffhanger hook for the full video.

### 4. Workspace Hygiene
- Immediately delete temporary raw video streams and temp audio files after muxing.
- Never leave broken, partial, or failed render files in output directories.
