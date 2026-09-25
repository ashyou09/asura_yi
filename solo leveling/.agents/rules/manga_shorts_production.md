---
name: Manga Video & Short Production Guidelines
description: Master rules for creating full-length landscape recap videos and music-only promo shorts from manga/manhwa.
---

# Manga Production Guidelines: Full Video & Promo Short

Whenever asked to create a video for any chapter or story arc, you MUST automatically produce BOTH a **Full Recap Video** and a **Promo Short** organized into separate dedicated subfolders under that chapter.

---

## 1. Directory Structure
Every chapter MUST be structured with two dedicated subfolders:
```
[Series Name]/chapter [X]/
├── full video/
│   ├── [Series]_Chapter_[X]_Full_Video.mp4  (16:9 Landscape 1920x1080)
│   ├── narration.md                         (Full scene-by-scene text)
│   └── audio_en/                            (TTS clips & master mix)
└── short/
    └── [Series]_Chapter_[X]_Promo_Short.mp4 (9:16 Vertical 1080x1920)
```

---

## 2. Full Video Production (16:9 Landscape)
- **Format:** 1920x1080 Landscape widescreen.
- **Panel Slicing:** Process the continuous webtoon strip and cleanly extract all individual story panels/scenes. Never blindly crop fixed heights or leave out important story beats.
- **Visual Presentation:**
  - Center the panel in high definition.
  - Apply an ambient, Gaussian-blurred, dimmed backdrop (`radius=25, brightness=0.35`) derived from that exact panel to eliminate ugly black borders and create depth.
- **Dynamic Camera Moves:**
  - **Ken Burns Zoom-In (1.0x -> 1.15x):** For close-ups, emotional tension, roars, and climactic strikes.
  - **Ken Burns Zoom-Out (1.15x -> 1.0x):** For wide reveals, shockwaves, and aftermath scenes.
  - **Vertical Slide / Pan:** For tall panels and full-body character reveals so viewers see the entire artwork from top to bottom.
- **Narration & Pacing:**
  - **Pacing:** Natural, human conversational pace (+0% rate) with subtle pauses between panels so listeners can easily follow every detail. Never rush.
  - **Language:** English (`en-US-ChristopherNeural` or specified voice).
  - **Tone:** Engaging, descriptive, serious, and informative.
  - **Audio Mix:** Voice at ~1.25x volume with subtle, atmospheric background music (e.g. `space_song.mp3`) at 4-5% volume.

---

## 3. Promo Short Production (9:16 Vertical)
- **Format:** 1080x1920 Vertical Shorts format.
- **Duration:** 20 to 30 seconds of high-intensity hook.
- **Audio:** **MUSIC ONLY** (no voiceover / zero talking). Use iconic high-energy phonk / trailer tracks (e.g., `neon_blade.mp3`, `metamorphosis.mp3`, `murder_in_my_mind.mp3`).
- **Editing & Hooks:**
  - **Beat Syncing:** Rapid cuts synced to the music beats (0.7s to 1.5s per shot).
  - **Dynamic Edits:** White flashes on impacts, punch zooms, subtle screen shakes, and dramatic color tints (e.g. red vignette during fatal strikes).
  - **Structure:**
    1. *Buildup (0-6s):* Ominous presence, wide shot, glowing eyes.
    2. *Drop (6-18s):* Fast-paced combat chaos, broken shields, brutal strikes, shattered attacks.
    3. *Cliffhanger (18-25s):* Fatal climax, shock expression, dramatic fade-to-black leaving the viewer desperate to watch the full video.

---

## 4. Documentation
Always generate and maintain `narration.md` inside `full video/` detailing every scene index, camera move, and spoken script for easy verification.
