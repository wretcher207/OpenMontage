> status: active | one-liner: OSS agentic video platform, fork of calesthio/OpenMontage | next: reaper-daemon-drums is BROKEN - source has 35s of digital silence over the cold open and the payoff, needs the REAPER groove bounced or a re-record before anything else
# HANDOFF - OpenMontage

Upstream clone plus local work. Contribute changes upstream rather than
diverging.

## 2026-08-22 - WGYC custom sailboat cover, 8:07 long-form cut

**New delivery.** 8:07.6, 1920x1080, 30000/1001, -14.6 LUFS, -1.9 dBTP, BT.709.
Read `projects/wgyc-sailboat-cover/SAILBOAT-CUT.md` before revising it.

`C:/media/video/wgyc-sailboat-cover/final/2026-08-22_wgyc-sailboat-cover_review.mp4`

**Unauditioned - nobody has watched or listened to it.**

- Source is `C:/media/video/_inbox/wgyc-custom-sailboat-cover/` (35 clips,
  39:36, three days). It arrived with its own `FOOTAGE-INVENTORY.md`, which is
  accurate except on speech.
- **The inventory undercounts her speech: there are four to-camera clips, not
  two.** `IMG_2845` is a clean 19s intro and `IMG_2846` narrates the ratchet
  pocket, on top of the 0416/0425 pair the inventory lists. ~2:30 total. 2845
  became the cold open because of it. Transcribe before trusting a shot log.
- 51 of 55 timeline items are real footage; the other four are cards.
- **Portrait crop pans must be measured, not estimated.** All the shop footage
  is portrait-only and gets a per-shot 16:9 pan. Seven shots were wrong on the
  first pass and `IMG_0391` was framing shop ceiling instead of her hands. The
  action in the close clips sits 45-80% down the portrait frame. A 72-frame
  timeline contact sheet does NOT catch this - one midpoint frame per shot,
  tiled, does. Run that after any pan change.
- **The limiter sits at -3.0 dBFS on purpose.** AAC adds ~1.4 dB of intersample
  overshoot over the WAV sample peak, so limiting at -1.7 still produced a -0.3
  dBFS file, and trimming on the encode cost 1.3 LU. Headroom upstream is the
  fix. Do not raise it.
- Music is **placeholder and unauditioned**: three cues from
  `C:/media/audio/suno/unused-beds/`, picked on duration and marine-sounding
  filenames. That is the same method that failed on the cushions job. Needs
  David's ear.
- `IMG_0425` is one unbroken 42.7s take. It was two beats that both cut her off
  mid-sentence. If act four drags, cover it with `IMG_0424`; do not trim her.
- Still missing: `IMG_2806` and `IMG_2808` arrived at 224x128 and are the only
  coverage of pulling and trimming the finished pattern. Ask Camilla to re-send
  those two at original resolution.

## 2026-08-19 - WGYC outdoor cushions process cut, and a project directory vanished

**`projects/wgyc-outdoor-cushions-hermes/` is gone from disk.** It disappeared
during this session's build, between one successful run that read its music bed
and the next run minutes later. It was untracked (`projects/` is not in git), so
there is nothing to restore from, and the Recycle Bin was empty. No command in
the session deletes, moves or cleans; cause unknown. What went with it:
`build_v2.py`, `build_flow_short.py`, `SOCIAL-REV2.md`, `FLOW-SHORT.md`, the
checkpoints, the rendered card frames, the flow-review contact sheets, the two
`youtube-thumbnail-vertical-v2` files, and both Suno cues `porch-bed-A.mp3` and
`porch-bed-B.mp3`.

What survives: the two delivered masters in
`C:/media/video/wgyc-outdoor-cushions/final/`, every source photo and Flow clip
under `C:/media/photo/clients/wgyc/outdoor-cushions/`, and the card machinery,
which had been copied into the new project before the loss. **Rev 2 can no longer
be rebuilt identically**, because its bed is gone.

**New delivery, the process cut.** 36.800s, 1080x1920, -14.0 LUFS, -0.9 dBTP,
BT.709 limited. Read `projects/wgyc-outdoor-cushions-process/PROCESS-CUT.md`
before revising it. The `-process-review.mp4` file beside it is rev 1 of the same
cut, superseded; it differs only in music and audio balance.

`C:/media/video/wgyc-outdoor-cushions/final/2026-08-19_wgyc-outdoor-cushions-process-rev4-review.mp4`

- **The outdoor cushion job has 8:28 of 1080p footage**, ten clips `DSCF0746` to
  `DSCF0761`, filed under `C:/media/video/wgyc-camper-top-wellcraft-v20/raw/`.
  The camper-top SHOTLOG resolved them as this job on 2026-08-17 and a frame
  check confirms it. Neither earlier cushion cut used any of it.
- 69.8% of this cut is real footage against the social cut's ~17%. No generated
  clips.
- Music went three rounds. `porch-bed-B.mp3` is gone with the directory. A cue
  picked on tempo and loudness range, `sawdust-bench`, got "sounds a bit porny"
  back, which no measurement would have caught. The cut now runs on
  `Porchlight Parcel.mp3`, generated to a folk and indie brief, copied into the
  project. **Do not pick a cue on numbers or on its filename.**
- Its tempo drifts 104.5 to 101.4 bpm, so `BEAT` is measured over the window the
  cut actually uses and `MUSIC_SS` is a detected onset, not `k * BEAT`.
- Rev 1 had the bed raw and the shop layer 19 dB under it, which is inaudible.
  Both bed and shop are normalised now, 7 dB apart.
- **The shop layer is off (`USE_SHOP = False`) and should stay off.** The cut's
  original premise was that the natural sound carries it. It does not. Three
  passes at the balance all left something audible that David heard as a second
  piece of music; he settled it by putting the cue over the picture on its own,
  which sounds right. The room takes are 16 kHz mono at -27 to -43 LUFS and no
  level for them adds anything. `build_process.py stems` writes both layers
  separately if anyone wants to hear what was dropped.
- Do not re-litigate this by measuring. Three of the four audio revs on this cut
  were driven by numbers and all three were wrong; the one that worked came from
  David listening.
- Unauditioned: nobody has watched or listened to it.

## 2026-08-19 - vigil deleted, all skills removed, reaper-daemon cut is broken

Read `projects/reaper-daemon-drums/README.md` before touching that project; a
prior session's claim that the take-2 playback measured -27 LUFS is FALSE and is
corrected there.

- **The delivered master is not usable.** The joined source is exact digital
  silence ~849-884s, which is the cold-open groove and the payoff listen. The
  master opens on 6.5s of silence and its payoff sits ~15 dB under speech.
  Not fixable by re-editing.
- **`vigil` is banned and its file is deleted.** David rejected it four times.
  Every `projects/*/bed.py` carries a hard `BANNED_CUES` guard that exits 1
  rather than build with it. Do not restore it or weaken the guard.
- vigil was stripped from four already-shipped projects' PLANs, so those cuts
  no longer rebuild identically. David was told and does not want it reverted.
- **Every skill on the machine was deleted except `drum-humanize`**, at David's
  instruction. That includes `recording-cutdown`. `.claude/skills`,
  `.agents/skills` and `skills/` are gone from this repo (tracked in git,
  restore with `git checkout -- <dir>` if he asks, not before).

## 2026-08-18 - WGYC vertical YouTube thumbnail rev 2

Current thumbnail files under
`projects/wgyc-outdoor-cushions-hermes/assets/`:

- `youtube-thumbnail-vertical-v2.jpg`: upload-ready 1080 x 1920 JPEG, 744,748
  bytes, no EXIF metadata.
- `youtube-thumbnail-vertical-v2.png`: lossless 1080 x 1920 master.

Rev 1 was rejected because the before/after images felt undersized and the
maker's circular head crop looked awkward. Rev 2 uses three large stacked
scenes: old cushions, a tight finished-porch reveal, and a natural wide workshop
portrait with the supplied logo. The comparison remains truthful because the
source set has no same-angle porch-before photo. Full-size and 270 x 480
small-size renders were visually checked. David's visual acceptance is the only
remaining gate.

## 2026-08-18 - WGYC outdoor cushions, social rev 2

Rev 1 read cheap and off-brand, so it was re-cut rather than patched. Review
master:

`C:/media/video/wgyc-outdoor-cushions/final/2026-08-18_wgyc-outdoor-cushions-social-rev2-review.mp4`

18.500s, 1080x1920, 30fps (555 frames), BT.709 limited, -14.0 LUFS, -0.9 dBTP
decoded. Read `projects/wgyc-outdoor-cushions-hermes/SOCIAL-REV2.md` before
revising it. The five things worth carrying forward:

- **ffmpeg `drawbox` + `drawtext` is the cheap look.** A hard-edged slab across
  the frame with no motion is the strongest "generated, not designed" tell there
  is. The cards are now rendered from `cards/cards.html` in headless Chrome as
  transparent PNG sequences, driven by a `seek(t)` function so frames are
  deterministic.
- **WGYC's real tokens are on the live site**, and rev 1's `#003764` navy and
  `#F0C36A` gold were neither of them: `--hull-navy #1a2332`,
  `--hull-slate #2c3e50`, `--accent #ff4757`, Oswald headings, Source Serif 4
  body.
- **Centre-cropping a landscape still to 9:16 picks the middle of the frame, not
  the subject.** That is the whole reason rev 1's maker shot was a propane
  heater. Every crop in rev 2 is a window sampled from the subject and then
  checked as a rendered frame, head and tail.
- **The Google Flow clips are 720x1280** and everything else is 3024px or
  better. Rev 1 gave the softest pixels the longest shot. Rev 2 keeps Flow to
  2.6s of 18.5s.
- **Round cut boundaries off the cumulative beat, not per shot.** Per-shot
  rounding drifted the last cut 0.1s off the grid.
- **Check every still at 1:1, out of the delivered file, not as a 1080 render.**
  Downscaling to 1080 hides motion blur, and two shots shipped soft before this
  got caught. `IMG_0108`, `IMG_0117` and `IMG_0102` are all shake-blurred despite
  A and B grades in the audit CSV; those grades are about composition, not focus.
  `IMG_0113` and `IMG_0103` are the sharp frames of the same subjects.
- **Size the `zoompan` plate to the shot's actual max zoom, never a fixed 2x**,
  or every still gets upscaled and then downscaled again for nothing.

Copy is Camilla's Register B built on her own camper-top formula, with the
Office line 207-300-5253. Music is `porch-bed-B.mp3` from Suno v5.5 (Premier
plan, 20 credits), used from 37.0s. That offset was picked from an energy
envelope, not by ear, so it is the first thing to change.

Nobody has watched or listened to it.

## 2026-08-18 - WGYC outdoor cushions, Flow social cut (rev 1, superseded)

Built a separate 18.96s 9:16 social derivative from the Google Flow exports and
real cushion-job assets. Review master:

`C:/media/video/wgyc-outdoor-cushions/final/2026-08-18_wgyc-outdoor-cushions-flow-short-review.mp4`

1080x1920, 30fps, BT.709 limited, -21.2 LUFS, -9.2 dBTP. No paid calls and no
generated music. The unchanged maker photo and original foam-cutting MOV are
the only human/action evidence; both zombie generations and all AI jigsaw
alternates are excluded. Audio rev 2 removed a mistakenly looped workshop bed
that put cutter grinding behind the whole edit; porch ambience now sits near
silence and the real cutter enters only from 6.4 to 9.8 seconds. Read
`projects/wgyc-outdoor-cushions-hermes/FLOW-SHORT.md` before revising. Human
watch/listen is the remaining acceptance gate.

## 2026-08-18 - WGYC camper top, the 9:16 Short

`projects/wgyc-camper-top-short/`, master at
`C:/media/video/wgyc-camper-top/final/2026-08-18_wgyc-camper-top-short.mp4`
(44.1s, 1080x1920, 30fps, BT.709 limited, -14.3 LUFS) with its `.srt` beside it.
This is the "Shorts later" item the redux deferred.

Cut from the redux's DELIVERED picture, not from `master.avi`, because the rev 5
hull-registration redactions live in those pixels and the camera is 1080p either
way, so going back to raw buys nothing for a vertical crop. Read the project
README before touching it; the three things most likely to bite a next session
are in there:

- **Crops are per shot and two of them were wrong first.** A 608px window out of
  1920 placed off a single mid-frame put `lapse` entirely on her backside with no
  work in frame. Sample the window, not the midpoint.
- **Colour is converted at cut time here, not at deliver**, because the piece
  mixes full-range BT.601 camera clips, a full-range Remotion card and an RGB
  PIL plate. Verified equal to the long cut: card ground (23,32,46) in both.
- **ASS captions**: alpha is inverted (`00` opaque), `force_style` margins are in
  PlayRes units not pixels, and an abbreviated Style `Format:` line silently
  drops the outline. All three failed quietly.
- **ffmpeg's native AAC encoder overshoots at 192k on this material.** The PCM
  mix peaks at -2.5 dBFS and the 192k file decodes back at +2.3 dBFS. Fixed by
  going to 256k on the same encoder. Nothing upstream of the encoder shows it,
  so check the DECODED peak, not the mix.

Nobody has watched or listened to it. Levels are measured and every shot was
checked as a frame; the cue choice and the cut rhythm are unauditioned.

Created 2026-08-14.


## 2026-08-18 — delivered colour was full range, fixed in the skill

`deliver` never converted colour. Everything upstream of it is concat-copied, so
delivered files carried whatever the source declared: camera MJPEG is full range
BT.601, and `yuvj` is deprecated enough that players ignore the flag, assume
limited range, and stretch the levels. A WGYC card ground rendered `#1a2332`
showed up near-black (`#0b1626`) on screen with the pixels correct all along.

Fixed in `recording-cutdown`'s `montage.py` (`~/.claude`, commit `73bda2f`), not
here: `cmd_deliver` now converts to BT.709 limited, tags all three fields, and
prints the delivered colour with an OK/BAD verdict. The `scale` filter carries no
`in_*` flags so screen captures already in BT.709 pass through untouched.

WGYC rev5 was re-encoded rather than re-cut since its pixels were fine:
`C:/media/video/wgyc-camper-top/final/2026-08-17_wgyc-camper-top-rev5-rec709_review.mp4`.
That is the copy to watch. Clips in `projects/wgyc-camper-top-redux/clips/` still
carry the old tags, which is correct — they should match their source, and the
single conversion happens at deliver.

## Agent contract

`WORKFLOW.md` (untracked, fork-local) is the whole contract and it is one page.
`AGENT_GUIDE.md`, `pipeline_defs/` and `skills/` are upstream reference, not
binding here. `PROJECTS-LOCAL.md` (untracked) holds delivery records and
per-project facts.

## Workflow reset, 2026-08-16

David's call. The fork had four stacked layers of video rules: upstream's
mandatory pipeline system, a fork-local file that existed mainly to cancel it,
the global cutting skill, and a set of per-video memory rules generalised from
single past jobs. The layers contradicted each other and the output showed it.

All of it collapsed into `WORKFLOW.md`: four non-negotiables covering money and
honesty, and otherwise the agent's judgment stated in a sentence per video. No
route table, no per-type rule sets, no forced gates.

**Shelved, deliberately, do not rebuild without asking:** the video-type router.
The previous plan was to split the cutdown path into named types (talking head,
craft b-roll, event coverage, performance, montage) each with its own selection
logic, audio contract, pacing and card rules. That is the exact "arbitrary rules
for different things" this reset removed. The underlying observation still
stands and is worth knowing: `~/.claude/skills/recording-cutdown/` is
transcript-driven end to end (filler removal, rambling removal, word-boundary
cut points, webcam PIP handling), so it fits a talking head and fits nothing
else well. Treat that as a known limitation to work around per job, not as a
spec to implement.

**Also ruled out 2026-08-16, do not re-propose:** integrating the third-party
`AgriciDaniel/claude-youtube` skill (14 YouTube strategy and packaging commands).
Evaluated and dropped.

## Open work

- `music_selector` needs tests, then an upstream PR. Branch
  `fix/music-capability-discovery` carries it (809fce0, 9e6f370) and will
  conflict on pull. Upstream PR #464 (the docs half) is open.
- WGYC camper-top build is in progress and blocked on the client sending usable
  finished-top media. Plan is `WGYC-BUILD-HANDOFF.md`; facts are in
  `PROJECTS-LOCAL.md`.
