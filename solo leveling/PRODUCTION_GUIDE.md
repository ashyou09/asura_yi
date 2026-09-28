# 🛠️ Standard Operating Procedure (SOP): Autonomous Solo Leveling Short Production

A complete technical manual for generating future short-form edits (`random_shot_X/`) in the **Solo Leveling** pipeline.

---

## ⚡ The Clean Delivery Standard

Every short-form folder (`random_shot_X/`) delivers strictly **3 clean, self-contained files**:

```text
random_shot_X/
├── Solo_Leveling_Random_Shot_X_Edit.mp4       # 1. 1080x1920 9:16 Beat-Synced Full Audio Short (~21s)
├── Solo_Leveling_Random_Shot_X_Edit_MUTED.mp4 # 2. Clean Muted Master for native in-app audio selection
├── UPLOAD_GUIDE.md                           # 3. Ready YouTube Shorts & Instagram Reels Viral Kit
└── project_notes.md                          # 4. Millisecond Cue Sheet & Camera Math Manifest
```

---

## 🚀 One-Command Autonomous Workflow

To generate any future shot (e.g., Shot 2, Shot 3):

### Phase 1: Storyboard & Audio Selection
1. Open `Solo_Leveling_Shorts_Stories.txt` and select the target storyboard.
2. Select the matching phonk track from `assets/music/` (e.g. *NEON BLADE*, *METAMORPHOSIS*, *Murder In My Mind*).
3. Set the FFmpeg offset so the master 808 drop lands at **09.85s**.

---

### Phase 2: Frame Selection & Visual Grading
1. Select 6–7 high-impact 1080×1920 action frames from `assets/anime_frames/` or extract key moments from the chapter full video.
2. Apply high-contrast anime aura grading:
   - Enhance contrast by **1.22x**.
   - Boost color saturation by **1.25x** to make Jin-Woo’s electric blue eye glow and purple shadow flames pop.

---

### Phase 3: Automated Video Assembly via Python & FFmpeg
Use the custom rendering engine `render_random_shot_X.py`:
1. **Dynamic Camera Math**:
   - `zoom_in`: Linear interpolation `1.0 + 0.09 * progress`.
   - `shake_drop`: Sinusoidal offset with exponential decay:
     ```python
     shake_fade = max(0, 1.0 - (f_idx - DROP_FRAME) / (FPS * 1.3))
     dx = int(math.sin(f_idx * 2.0) * 35 * shake_fade)
     dy = int(math.cos(f_idx * 2.4) * 30 * shake_fade)
     ```
   - `flash`: 4-frame white bloom overlay on beat impact.
2. **Dual-Pass Kinetic Typography**:
   - Outer dilated text pass with alpha `0.6` followed by crisp white/cyan core text.
   - Rounded translucent backing boxes (`#05080F` with alpha `0.88`) with `#00F0FF` borders.
3. **Master Muxing**:
   - Full Audio MP4 with 1.2s smooth outro fade.
   - Separate Clean Muted MP4 (`-an -c:v copy`).

---

### Phase 4: FFmpeg Master Assembly Commands

```bash
# 1. Full Audio Master
/opt/homebrew/bin/ffmpeg -y \
  -r 30 -i tmp_frames/frame_%05d.jpg \
  -ss 11.69 -t 21.00 -i assets/music/neon_blade.mp3 \
  -c:v libx264 -preset fast -crf 18 -pix_fmt yuv420p \
  -c:a aac -b:a 256k -af "afade=t=out:st=19.8:d=1.2" \
  Solo_Leveling_Random_Shot_X_Edit.mp4

# 2. Clean Muted Master
/opt/homebrew/bin/ffmpeg -y \
  -i Solo_Leveling_Random_Shot_X_Edit.mp4 \
  -an -c:v copy \
  Solo_Leveling_Random_Shot_X_Edit_MUTED.mp4
```

---

### Phase 5: Documentation & Workspace Hygiene
1. Write `UPLOAD_GUIDE.md` with 3 high-CTR title hooks, descriptions, hashtags, and pinned comment.
2. Write `project_notes.md` documenting exact timestamps.
3. Purge `tmp_frames/` directory immediately.
