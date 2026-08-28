> status: active | one-liner: OSS agentic video platform, fork of calesthio/OpenMontage | next: claude-band-reaper-daemon is DELIVERED 2026-08-27 - 6:25.9 long-form master, 53.0s vertical Short, both thumbnails and the social package, all in C:/media/video/claude-band-reaper-daemon/final/, revised twice after David caught edit points landing inside words - and NOBODY HAS WATCHED EITHER CUT END TO END, which is the only open item; codex-reaper-daemon is DELIVERED (4m24.1s master plus a 49.7s vertical SHORT delivered 2026-08-24, both in C:/media/video/codex-reaper-daemon/final/) and BOTH need David's watch before upload; the master's .srt has one wrong word at cue 56 - it says "See, Codex officially sucks at this shit" and the source says "Yeah," - not fixed yet; the delivered ox-alpha Short is 96 kHz AAC from a loudnorm/aac interaction, harmless in playback but wrong in a master, rebuild fixes it; Ox Alpha SHORT is built and delivered (47.2s vertical, needs David's watch); the Ox Alpha LONG-FORM cut is still parked on its 11-box human safety sweep and nothing long-form is delivered; WGYC sailboat is DONE - rev2 and the Short are both audited by David, public on YouTube, and rev2 is with Camilla; the beds shipped as-is; reaper-daemon-drums is BROKEN - source has 35s of digital silence over the cold open and the payoff, needs the REAPER groove bounced or a re-record before anything else
# HANDOFF - OpenMontage

Upstream clone plus local work. Contribute changes upstream rather than
diverging.

## 2026-08-27 - claude-band-reaper-daemon: long form, Short, thumbnails, package

**Done end to end, then revised twice after David watched it.** He asks Claude
Code, through his own REAPER Daemon, to write a metal song in REAPER section by
section, and reacts live. One riff comes back usable, the chorus comes back
comically bad, the breakdown comes back closest to right. His verdict: "the
potential's there, but I don't think AI is replacing musicians anytime soon."

**Delivered, everything in one folder** at
`C:/media/video/claude-band-reaper-daemon/final/`:

- `2026-08-27_claude-band-reaper-daemon_master.mp4` - **385.90s (6:25.9)**,
  11577 frames, 1920x1080, 30fps CFR, -14.7 LUFS, LRA 4.6, -1.9 dBTP, BT.709,
  AAC 48 kHz stereo, 140 MB
- `..._master.srt` - 115 cues
- `..._short_master.mp4` - **53.00s**, 1590 frames, 1080x1920, 30fps CFR,
  -14.6 LUFS, LRA 5.6, -2.0 dBTP, captions burned in, 39 MB
- `..._short_master.srt` - 25 cues
- `..._thumb-16x9.jpg` and `..._short_thumb-9x16.jpg`
- `SOCIAL.md`

Chapters, read off the delivered file: 0:00 / 0:22 / 1:11 / 3:16 / 4:52 / 5:47.

**Social package in the vault**, `C:/Users/wretc/second-brain` (the checkout
Obsidian has open, on `main`): `content/claude-band-reaper-daemon-video-social.md`
(YouTube, Facebook, X) and `...-short-social.md` (YouTube Short, Instagram,
TikTok), both `status: draft`, both pushed.

**Build projects** are `projects/claude-band-reaper-daemon/` and
`-short/`, both gitignored like every other project here.
`projects/claude-band-reaper-daemon/RUN-REPORT.md` is the full account and each
project's `README.md` is its paper trail. Read them before revising the cut.

### Verified, and how

- Frame counts on both delivered files match their own `picture.mp4` exactly,
  and both are 30fps CFR / 48 kHz AAC / BT.709. Probed on the delivered files.
- Per-beat loudness measured on the DELIVERED long cut: 7 bed-alone beats at
  -18.0 to -19.8 (1.8 LU spread, 3.3 to 5.1 LU under program).
- Captions matched against a transcription of each delivered file's OWN audio:
  96/115 and 23/25. **The remaining flags are the verifier's own transcription
  drifting a word across a cue boundary, not dropped clips** - three of them,
  including the worst-looking one, were checked directly against the delivered
  audio and are correct.
- Black-run scan: 7 on the long cut (the six cards plus the ident's own black
  head), 1 on the Short (the end card).
- **Safety swept three times**: 376 camera + 664 screen frames at 2 fps on rev1,
  then only the newly added material on rev2 (70 frames) and rev3 (87 frames).
  Every sheet was looked at. No vape, no taskbar, no title bar, no paths, no
  credentials.
- **Assertion over every piece**: none ends inside its own last word, none
  begins inside a word (except a beat's own hand-pinned opening, which is an
  editorial choice), and none gained a word the edit excluded.

### Assumed, not verified

Nothing about the files. **Nobody has watched either cut end to end** except
David's two partial passes, which is how both revisions happened.

### Traps

- **`concat -c copy` does not conform timebases.** `cards.mjs` writes its own,
  so the concatenated picture read 11331 frames at an average 30.27 fps and the
  delivery encode reconciled it against the audio by silently dropping 547
  frames. Nothing errored and the frame-count assertion passed, because the
  count was right. `build.py` now re-encodes cards through the project encoder,
  checks container DURATION against frames/fps, and forces `-fps_mode cfr`.
  **Do not remove any of the three.**
- **An out-point snapped off the burst map ends INSIDE the last word.** At
  `burst_db` -48 a word's final consonant has already decayed below threshold.
  27 of 74 pieces did it; David heard two. `cut._extend()` and `cut._pull_in()`
  fix both edges. **`_pull_in` must stay restricted to parts after the first** -
  applied to a beat's opening it drags in words the cut deliberately starts
  after (a stray "Claude?", "so", "better", "sometimes").
- **Whisper stretches the last word of a segment to the segment end**, so a
  word can come back 2.3 seconds long. `tighten()` measures pauses as
  `next.start - this.end`, and an inflated end makes a real pause vanish: it
  collapsed a three-part beat into one and left five seconds of dead air.
  `cut.GAP_WORDS` clamps ends to the burst they start in for gap detection, and
  `cut.EDIT_WORDS` caps them at 600 ms for the edit repairs. **The two clamps
  are different on purpose and neither can be used for the other's job.**
- **Window size is itself a transcription variable.** The reaction beat took
  five passes. At 110s it read "Yeah, how about all that"; at 40s "about all
  that"; at 28s "How about all that". Cut into 2-to-11-second windows it reads
  what he says: "Hmm. I don't know about all that. I don't know about all that."
  Every wider pass lost the same three words. When passes disagree, narrow the
  window before believing any of them.
- **Never point a thumbnail pass at a delivery that burns in captions.** Codex's
  first 9:16 used a screengrab of the delivered Short and put "WHAT THE FUCK" in
  the thumbnail.
- **`workspace/second-brain/bonefish` is a stale clone**, 28 commits behind main
  and still carrying the Content Desk subsystem main removed in a93f887. The
  package went there first by mistake and was removed. The live vault is
  `C:/Users/wretc/second-brain`.
- **The camera's audio reads as unusable at 1s RMS and is not.** A raw waveform
  correlation on the clap slate locks the offset at +28.548s.

### Left for David

1. **Watch both, with ears.** The only open item.
2. His call on the agent's Recents list, legible on screen and naming a client
   by shorthand ("wygc"). That client's work is already public on this channel.
3. Two PNGs appeared in `final/` at 23:55-23:56 on 08-27,
   `...-thumbnail-horizontal-generated.png` and `...-vertical-generated.png`.
   Not from this run and not touched.

## 2026-08-24 - codex-reaper-daemon: the 49.7s vertical Short is delivered

**This is the Short only. The 4m24 master is untouched.** Both now need the
same thing from him: a watch, with ears.

- **Delivered:**
  `C:/media/video/codex-reaper-daemon/final/2026-08-24_codex-reaper-daemon-short_master.mp4`
  plus a matching `.srt`. 49.7s, 1080x1920, 30fps CFR, -14.5 LUFS, -1.54 dBTP,
  BT.709, AAC 48 kHz, 70 MB.
- **Build:** `projects/codex-reaper-daemon-short/` (gitignored, like the other
  short projects). `build.py` makes it, `verify.py` checks it without trusting
  it. `README.md` there is the paper trail - read it before touching the cut.
- **Cut from the RAWS, not from the master.** The master's picture is a
  composite with the phone camera burned in as a 300x375 inset, so a vertical
  crop of it would either clip the inset or lose his face. Going back to the
  raw means the phone file is native 9:16 and fills the frame at exactly 0.5x
  with no crop at all. Every in and out still descends from the master's
  `edl.py`.
- **The Short IS the before/after.** Flat pink block of 127-velocity drum hits,
  hard cut, jagged human shape - both off a 540x540 crop of the REAPER MIDI
  editor. The master's timelapse is dropped: sampled at 8s spacing inside that
  crop the picture barely moves.
- **The audio path was positive-controlled before the first build.** VO +
  REAPER desktop summed with `amix normalize=0` nulls against the master's own
  edit source at -56 dB, so the master's per-clip gains carry over meaning what
  they meant.
- **Two bugs found in the sibling ox-alpha Short's build script**, both fixed
  here and both still in that delivered master: it writes 96 kHz AAC (loudnorm
  outputs 192 kHz and the encoder picks the nearest rate it has), and
  `loudnorm` in linear mode only warns about a true-peak overshoot rather than
  stopping it - the first build here landed -0.29 dBTP against a -1.5 request.
- **The master's caption is wrong in one place.** Cue 56 of
  `2026-08-23_codex-reaper-daemon_master.srt` reads "See, Codex officially
  sucks at this shit." Three window transcriptions of the raw VO and the burst
  map all say "Yeah,". The Short captions it correctly; the master was left
  alone because it is a different deliverable.
- **The sibling Short's bed level did not transfer.** Its -3.0 dB put this
  cut's bed-alone card beats LOUDER than the voice. Set to -10.0 by
  measurement, which lands them 4.2 and 3.3 LU under program.
- **Verified:** 29/29 caption cues matched against a transcription of the
  delivered file's own audio, per-beat loudness scan, black-frame scan (three
  runs, all three are the cards), 52 QC frames, and a 2fps full-frame sweep of
  all six camera windows. The vape span the master constrains is 146s clear of
  the nearest kept material.
- **Left for David:** watch it start to finish. Same gate the master is on.

## 2026-08-23 - codex-reaper-daemon: delivered, 4m24, needs his ears

**New piece, done end to end today.** Codex driving the REAPER Daemon on two
jobs in one live session: humanize a MIDI drum track (it nails it) and write
mirrored automation across a stereo guitar pair (it does not, then eventually
does after a lot of hand-holding). `review` returns PASS.

- **Masters:** `C:/media/video/codex-reaper-daemon/final/` -
  `2026-08-23_codex-reaper-daemon_master.mp4`, 264.10s, 1920x1080, 30fps CFR,
  irregular=0, -14.2 LUFS, -1.9 dBTP, BT.709 limited, 2.6 Mbps, 82 MB, plus its
  `.srt` (73 hand-corrected cues) and a 15fps halfrate agent artifact.
- **Read `projects/codex-reaper-daemon/README.md` before touching the cut.** It
  carries the measured clocks, the framing reasoning, the six defects `script`
  caught, and the safety constraint below.
- **A green vape device was on screen at 204s of the first cut** and is now
  gone. It sat inside the `lapse_wait` timelapse; the window moved from source
  1220-1430 at 42x to **1230-1325 at 19x**, same 5.00s exactly. The device is at
  source 1336-1337 with hand-to-mouth to 1346. **Do not widen that window.**
- **The source is healthy, unlike reaper-daemon-drums.** Zero digital-silence
  stretches in the VO stem (positive-controlled), and the REAPER playback
  actually reached the recording this time, so the before/after drum listens are
  real audio.
- **The camera is a burned-in inset, not cutaways.** The screen capture has no
  webcam and the phone camera is a separate portrait file, so the edit source is
  a composite: screen at full frame plus a 300x375 camera inset at
  x=1576,y=661. Camera offset measured at +2.969s against the OBS/VO clock, 12ms
  drift across 25 minutes. `montage.py` was not modified.
- **Two things a future cut should know about the rig:** it is UNGATED (room
  floor -64 dB, `burst_db` -44, not the -52 default), and the REAPER playback
  lands 4-7 LU under his voice so listen clips need a gain. `listen` is capped
  at +5 dB by peak, not by taste; +8 hard-clipped it.
- Music is three original library cues (cold-front / nightline / undertow),
  loudness-matched before assembly, bed silent under both drum listens. No new
  cue was scored: REAPER was open with an unsaved project and `agentic-score`
  drives that same REAPER.
- **Open for David, not blocking:** nobody has watched it with ears. It is
  verified by measurement, by transcription of the built clips, by 46 QC frames,
  by a per-second level scan and by a per-second camera sweep. Also: he dropped
  `codex.jpg` and `reaper-logo.jpg` in the inbox and neither is usable as an
  overlay (checkerboard baked in as pixels, no alpha); they are unused.

## 2026-08-23 - Ox Alpha: the 47s vertical Short is built and delivered

**This is the Short only. The long-form cut is untouched and still parked** on
its 11-box human safety sweep, which nothing below unblocks.

- **Delivered:**
  `C:/media/video/ox-alpha-reaper-daemon-page/final/2026-08-23_ox-alpha-reaper-daemon-short_master.mp4`
  plus a matching `.srt`. 47.2s, 1080x1920, 30fps, -14.2 LUFS, LRA 5.2,
  TP -1.4 dBFS, BT.709. The 9:16 thumbnail that was already sitting in `final/`
  fits it ("WHO BUILT OX ALPHA?").
- **Build:** `projects/ox-alpha-reaper-daemon-short/` (gitignored, like the
  other short projects). One file, `build.py`, EDL included. `README.md` there
  is the paper trail; read it before touching the cut.
- **Every in and out is inherited from the long-form `edl.py`**, cut from the
  same raw and the same authoritative WAV. Three pins moved and each says why
  at the beat: `hook` is split across its own 3.4s hole, the free-week thesis
  loses its middle, and `reveal_open` drops from 7.5s to 3.6s because the hero
  stops moving at src 562.
- **It carries LESS exposure than the long-form cut, deliberately.** The
  argument beats are on the PHONE, not on screen, because the master's full
  frame shows the bookmarks bar and `C:/Users/wretc/...` paths and a vertical
  punch-in makes that text MORE legible, not less. The only screen material is
  the PAGE crop the master's own report already clears, and its bottom edge is
  12 rows tighter so the 8px taskbar sliver the master carries is gone. Swept
  all 10.1s of page material at 2fps and all 25.4s of face material at 1fps;
  sheets are in `projects/ox-alpha-reaper-daemon-short/qc/`.
- **No profanity in this cut** - checked against the transcript in every window
  used, not just against the srt.
- **The bed is Suno**, two of the master's own four cues, so the upload needs
  claiming after it goes live. Level was set by measuring three duck settings,
  not by ear; numbers are in the README.
- **`It works too. It's functional.` is deliberately NOT in the cut.** Its own
  mapped picture is a GitHub repo page, not the product page - he had tabbed
  away. Using the line would have meant importing a picture from elsewhere in
  the timeline under a claim about the page working.
- **Left for David:** watch it start to finish. That is the one gate a build
  cannot close.

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

**Rev 2 is delivered, public, and audited.** David watched and listened to it
2026-08-23, sent it to Camilla, and published it. The 9:16 Short is public too.
Nothing here is pending.

**Rev 2:**
`C:/media/video/wgyc-sailboat-cover/final/2026-08-23_wgyc-sailboat-cover_rev2.mp4`
487.55s, 1920x1080, 30000/1001, -14.6 LUFS, -2.1 dBTP, BT.709, 7.7 Mbps, 485 MB.

- Nine pans moved: IMG_0402 x2, 0406, 0407, 0408 x3, 0424 x2. Values and method
  are in `projects/wgyc-sailboat-cover/SAILBOAT-CUT.md`; `edl.py.bak-20260823`
  holds the old ones.
- The 0402 pair was outside her note - David approved adding it. Its trimming
  beat had the snips and most of her hands out of frame.
- **Audio and timeline are untouched.** Same duration, same `renders/mix.wav`,
  so sync is exactly what she already heard. **The bed shipped as-is** - the
  three Suno cues picked on duration and filename went out and David passed them
  on his own listen, so the placeholder is now the released mix. Do not swap it.
- Verified by pulling frames from the finished file at 258, 266, 274, 282, 292,
  304, 316, 375 and 388s. Needle or presser foot plus her hands in all nine.
- **The midpoint contact sheet does not catch this.** A midpoint frame of a
  badly panned sewing shot still reads as a competent shot of a sewing machine.
  Ask "is the needle in frame?" of every machine shot by name.
- **`build.py mux` is not the deliverable.** It stream-copies the crf-16 shots
  and lands at 12.5 Mbps / 780 MB. Rev 2 was re-encoded from `picture.mp4` at
  crf 19 / preset slow / maxrate 9M / faststart to reach 7.7 Mbps, matching
  rev1's 7.0 Mbps. Do that on every future revision.
- Rev 1 stays in `final/` for comparison.
- **Published:** long https://youtu.be/wl2E8Hs8osY, Short
  https://youtube.com/shorts/7wlCBlXr4Do (also in `PROJECTS-LOCAL.md`).

## 2026-08-23 - WGYC sailboat cover, the 9:16 Short

**New delivery.** 39.8s, 1080x1920, 30000/1001, -14.5 LUFS, -2.7 dBTP, BT.709.
Read `projects/wgyc-sailboat-short/SHORT-CUT.md` before revising it.

`C:/media/video/wgyc-sailboat-cover/final/2026-08-23_wgyc-sailboat-cover-short_review.mp4`
(`.srt` beside it; the same five cues are burned in.)

**Audited and published 2026-08-23.** David watched and listened; it is public.

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
