# 🛠️ Standard Operating Procedure (SOP): Autonomous Action Manhwa Video Production

A complete technical manual for generating future chapters of **I Killed an Academy Player** autonomously with high-energy beat-synced visuals and zero copyright friction.

---

## ⚡ The Clean Delivery Standard

Every chapter folder (`episode_X/`) delivers strictly **3 clean, self-contained files**:

```text
episode_X/
├── IKAAP_Episode_X_Edit.mp4          # 1. 1080x1920 9:16 Beat-Synced Manhwa Master Video (~20s)
├── UPLOAD_GUIDE.md                   # 2. Ready YouTube & Instagram Copy-Paste Viral Kit
└── project_notes.md                  # 3. Millisecond Cue Sheet, Storyboard & Technical Manifest
```

---

## 🚀 One-Command Autonomous Workflow

To generate any future episode (e.g. Episode 5, Episode 6), execute the following 5-phase pipeline:

### Phase 1: Script Selection & Beat Alignment
1. Open `IKAAP_Shorts_Stories.txt` and select the target episode.
2. Select the matching phonk track from `assets/music/` (e.g., *METAMORPHOSIS*, *NEON BLADE*, *Keraunos*).
3. Identify the master beat drop timestamp (e.g., 9.85s).
4. Divide the 20-second edit into 6–7 cinematic story beats:
   - **Scene 1 (Hook)**: The mystery, threat, or dead rival.
   - **Scene 2 (Tension)**: Looming danger or system alert.
   - **Scene 3 (Rising Escalation)**: Panic or realization building to drop.
   - **Scene 4 (💥 Beat Drop Impact)**: Awakening of Sacred Precepts / Golden chains.
   - **Scene 5 (Climax Strike)**: Full-power spear thrust / earth shattering strike.
   - **Scene 6 (Protagonist Aura)**: Extreme close-up of blazing eyes & smirk.
   - **Scene 7 (Loop Outro)**: Stride toward the next destination.

---

### Phase 2: 9:16 Full-Color Panel Generation
Generate 6–7 vertical (9:16) panels using `generate_image` strictly matching the **Character Model Sheet in `README.md`**:
- Art style prompt token: `Action manhwa webtoon style, AsuraScans tier, crisp black ink linework, saturated digital coloring, glowing volumetric particles, dramatic lighting`.
- Maintain character consistency: Corin Locke's dark brown messy hair, sharp amber eyes, charcoal academy gear, steel spear, and golden sun runes.

---

### Phase 3: Automated Video Assembly via Python & FFmpeg
Use the custom rendering engine `render_episode_X.py` which executes:
1. **Dynamic Camera Math**:
   - `zoom_in`: Linear interpolation `1.0 + 0.10 * progress`.
   - `shake_drop`: Sinusoidal offset with exponential decay:
     ```python
     shake_fade = max(0, 1.0 - (f_idx - DROP_FRAME) / (FPS * 1.2))
     dx = int(math.sin(f_idx * 1.8) * 35 * shake_fade)
     dy = int(math.cos(f_idx * 2.2) * 30 * shake_fade)
     ```
   - `flash`: 4-frame white bloom overlay on beat impact.
2. **Kinetic Typography & Pill Backings**:
   - Dual-pass glow rendering: outer dilated text pass with alpha `0.6` followed by crisp white/colored core text.
   - Rounded translucent backing boxes (`#0A0A0F` with alpha `0.85`) to ensure 100% legibility against busy combat art.
3. **Audio Synchronization & Fade**:
   - Stream copy or high-bitrate AAC (256 kbps) synced with 1.2-second smooth outro fade.

---

### Phase 4: FFmpeg Master Assembly Command

```bash
/opt/homebrew/bin/ffmpeg -y \
  -r 30 \
  -i tmp_frames/frame_%05d.jpg \
  -ss 0.00 -t 20.50 \
  -i assets/music/metamorphosis.mp3 \
  -c:v libx264 -preset fast -crf 18 -pix_fmt yuv420p \
  -c:a aac -b:a 256k -af "afade=t=out:st=19.3:d=1.2" \
  IKAAP_Episode_X_Edit.mp4
```

---

### Phase 5: Documentation & Cleanup
1. Generate `UPLOAD_GUIDE.md` with 3 click-engineered titles, hook-first description, tag list, and pinned comment.
2. Generate `project_notes.md` with complete millisecond timeline and color palette.
3. Purge all intermediate frame files (`tmp_frames/`) to keep directory lightweight and clean.
