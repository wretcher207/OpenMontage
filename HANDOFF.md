> status: active | one-liner: OSS agentic video platform, fork of calesthio/OpenMontage | next: Ox Alpha / REAPER Daemon page cut is revised on David's notes and parked on an 11-box human safety sweep (nothing delivered); WGYC sailboat long cut rev2 is built and verified (her framing note fixed) and needs sending to Camilla; the Short is undelivered and unauditioned; music is placeholder in both; reaper-daemon-drums is BROKEN - source has 35s of digital silence over the cold open and the payoff, needs the REAPER groove bounced or a re-record before anything else
# HANDOFF - OpenMontage

Upstream clone plus local work. Contribute changes upstream rather than
diverging.

## 2026-08-22 - Ox Alpha / REAPER Daemon page: finished cut, parked at the safety gate

Found 2026-08-23 by inspection; the session that built it left no handoff entry.
**It is not a mess and it is not half-built.** A complete 5:50 cut exists and
passes every automated check. It stopped at the one gate that needs human eyes.

Everything lives OUTSIDE this repo, which is why it is invisible here:
`C:/media/video/ox-alpha-reaper-daemon-page/`. There is no `projects/` entry.

- **The cut:** `working/edit-source/final.mp4` - 350.1s, 1920x1080, 30fps,
  -14.3 LUFS, -0.9 dBTP, BT.709 limited, 42 clips, 57 caption cues in
  `final.srt`. `final_15fps.mp4` beside it is an ad-hoc smaller copy, not a
  toolkit output. **`final/` is empty - nothing has been delivered.**
- **What blocks it:** `ms.py review .` returns `HOLD: 1 blocking: safety` -
  11 unticked boxes in `working/edit-source/safety/REPORT.md`. The sweep
  rendered 12 contact sheets covering all four sources at 10s spacing and then
  correctly refused to tick its own boxes. That is the honest state, not a bug.
  Ticking them requires looking at the sheets at full size.
- Known sweep targets it names: taskbar (kept, flagged), Magpie clipboard
  overlay with prompt history, `C:/Users/wretc/...` paths in git output during
  the rebuild lapse, and the browser bookmark sidebar in the reveal shots
  (removed by a `1664:936:224:100` PAGE crop - every reveal frame still needs
  verifying).
- **Profanity is already clear.** The safety report flags an f-word at raw WAV
  01:09, but it is in the source, not the cut: no profanity appears anywhere in
  `final.srt`. Checked, not assumed.
- Warning, not blocking: the bed is four Suno cues from
  `C:/media/audio/suno/unused-beds`, so it is generated, and `review` says so -
  generated music gets uploads claimed after they go live.
- Two other human items `review` will not do: look at all 42 frames in `qc/`,
  and watch the thing start to finish once.

**Revised 2026-08-23 on David's notes.** He watched it. Two defects, both real,
both fixed and verified; the cut is now 350.5s and `review` still holds only on
the safety sweep.

- **"Interesting" was cut off going into the ident.** `hook_off` ended at wav
  1557.60 and the word measures 1557.74-1558.22 - the cut landed 0.14s *before
  the word started*. Now `b=1558.95, fix_out=False`; the word lands 19.50-20.04
  with the ident at 20.733, so it has 0.69s of air. The out-snap was what pulled
  the point back into the silence ahead of the word.
- **A caption sat up for 16.5s and appeared 13s early.** One-word raw cue
  "Interesting." was treated as a flash cue and merged FORWARD into a cue 12.3s
  later, across the ident and a card. **Fixed in the shared toolkit**
  (`~/.agents/skills/recording-cutdown/scripts/montage.py`, backup
  `.bak-20260823`): `cmd_captions` gained `merge_gap` (default 2.0s) and now
  stretches a marooned flash cue in place instead of merging it across silence.
  **This changes caption output for every project that uses the toolkit.**
- **`srt` re-segments differently every run** - 68 raw cues became 80 with no
  audio change past 20.7s, mis-keying all 14 hand fixes. `expect_raw` caught it
  and refused. `captions.json` was re-mapped (15 fixes, `expect_raw: 80`).
  Budget for this after any rebuild that re-runs `srt`.
- David has no problem with the Suno bed, so treat `review`'s music warning as
  known and accepted, not as something to re-litigate.
- `working/edit-source/README.md` is genuinely good - source map, measured sync
  offsets with evidence, a WAV splice hazard at wav ~950-965, and a defects
  list. Read it before touching the cut.
- It depends on `C:/Users/wretc/.agents/skills/recording-cutdown/scripts/montage.py`,
  which still exists. The skill purge recorded below hit this repo's copies, not
  that one.

## 2026-08-23 - WGYC sailboat cover: rev2 fixes the sewing framing

**Camilla came back on the 8:07 cut.** At ~4:30 for about a minute and again at
~6:10, the sewing shots "cut out the needle and thread part of the machine" -
only the top of the machine and a bit of her head and shoulder. She asked
whether she had framed it that way.

**She had not. It was our crop.** The shop footage is portrait phone video that
gets a per-shot 16:9 pan, and those pans sat too high. Her originals hold the
needle, the presser foot and her hands in every one of the shots she named -
checked against the source frames, not assumed.

**Rev 2, built and verified, not yet sent:**
`C:/media/video/wgyc-sailboat-cover/final/2026-08-23_wgyc-sailboat-cover_rev2.mp4`
487.55s, 1920x1080, 30000/1001, -14.6 LUFS, -2.1 dBTP, BT.709, 7.7 Mbps, 485 MB.

- Nine pans moved: IMG_0402 x2, 0406, 0407, 0408 x3, 0424 x2. Values and method
  are in `projects/wgyc-sailboat-cover/SAILBOAT-CUT.md`; `edl.py.bak-20260823`
  holds the old ones.
- The 0402 pair was outside her note - David approved adding it. Its trimming
  beat had the snips and most of her hands out of frame.
- **Audio and timeline are untouched.** Same duration, same `renders/mix.wav`,
  so sync and the placeholder bed are exactly what she already heard. The music
  is still unauditioned placeholder and she has not commented on it.
- Verified by pulling frames from the finished file at 258, 266, 274, 282, 292,
  304, 316, 375 and 388s. Needle or presser foot plus her hands in all nine.
- **The midpoint contact sheet does not catch this.** A midpoint frame of a
  badly panned sewing shot still reads as a competent shot of a sewing machine.
  Ask "is the needle in frame?" of every machine shot by name.
- **`build.py mux` is not the deliverable.** It stream-copies the crf-16 shots
  and lands at 12.5 Mbps / 780 MB. Rev 2 was re-encoded from `picture.mp4` at
  crf 19 / preset slow / maxrate 9M / faststart to reach 7.7 Mbps, matching
  rev1's 7.0 Mbps. Do that on every future revision.
- Rev 1 stays in `final/` for comparison. Nobody has watched rev2 end to end.

## 2026-08-23 - WGYC sailboat cover, the 9:16 Short

**New delivery.** 39.8s, 1080x1920, 30000/1001, -14.5 LUFS, -2.7 dBTP, BT.709.
Read `projects/wgyc-sailboat-short/SHORT-CUT.md` before revising it.

`C:/media/video/wgyc-sailboat-cover/final/2026-08-23_wgyc-sailboat-cover-short_review.mp4`
(`.srt` beside it; the same five cues are burned in.)

**Unauditioned - nobody has watched or listened to it.**

- **Every source in it is natively 9:16, so there is no crop and no upscale
  anywhere.** IMG_0480 and IMG_0408 are 4K portrait and downscale 2x; the rest
  are 1080x1920 and go in 1:1. Pixel for pixel the Short is sharper than the
  8:07 film it came from, which is the reverse of the usual Short trade.
- **The cost:** the boat and the whole patterning act are out. That coverage is
  the landscape IMG_28xx clips (two of them only 1280x720). `build.py` refuses a
  non-9:16 source rather than centre-cropping it. IMG_2845 is landscape too, so
  its opening and closing lines are used as voice-over over IMG_0480 picture.
- Four shots were re-timed after a frame check: IMG_0391 at 31s is a
  motion-blurred whip through the room, IMG_0385 at 35s is a wide of dead floor.
  **`build.py sheet` writes one midpoint frame per shot**, and a 200px tile is
  still too small to see motion blur - pull the suspects at 400px+.
- **Program loudness is two-pass loudnorm.** Single-pass landed -15.5 against a
  -14.0 target; loudnorm has no lookahead over a 40s program. Do not fix a level
  miss here with a blanket gain, re-measure.
- Music is `bed-a.wav` from the long cut and carries its placeholder problem
  unchanged: picked on duration and a marine-sounding filename. Needs David's ear.
- The Short's end card carries the site plus "Find us on Facebook", same as the
  long cut's. `strips/_card_end.png` in the long-cut project does NOT show that
  line: it is a frame grabbed before the line animates in, not the finished
  card. Check the delivered file, not a card still.

## 2026-08-22 - WGYC custom sailboat cover, 8:07 long-form cut

**New delivery.** 8:07.6, 1920x1080, 30000/1001, -14.6 LUFS, -1.9 dBTP, BT.709.
Read `projects/wgyc-sailboat-cover/SAILBOAT-CUT.md` before revising it.

`C:/media/video/wgyc-sailboat-cover/final/2026-08-22_wgyc-sailboat-cover_review.mp4`

**SENT TO CAMILLA 2026-08-23, as built.** David sent this file to the client
without an internal watch or listen first, and is waiting on her reaction. So
the placeholder music below went out with it. Two consequences for whoever picks
this up: any revision request from her is feedback on a cut nobody here has
audited, and if her note is about feel, pace or tone, **suspect the bed before
the edit** - it was picked on filename, which is the method that has already
failed once on this client.

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
- Still missing: `IMG_2806` (1:54, pulling the film pattern off the hull and
  folding it) and `IMG_2808` (3:13, final marking, trimming, loading it into the
  vehicle). 5:07 covering the one step that joins the boat to the shop, and both
  cuts jump straight over it. **Verified, not assumed:** `IMG_2807` is the 720p
  clip from the same minute and it stays on the film while it is still on the
  boat, so nothing else in the drop covers the pull-off. Both are 224x128 at
  15 fps / 64 kbps - iMessage recompression, so the originals are almost
  certainly intact on her phone; ask for AirDrop or an iCloud link. Their audio
  is useless either way (2806 silent, 2808 is her talking to the dog). They are
  landscape, so a re-send helps the 8:07 film and does nothing for the Short.
  No ask has been sent - David is waiting to hear back from her first.

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
