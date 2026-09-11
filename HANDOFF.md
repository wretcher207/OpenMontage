> status: active | one-liner: OSS agentic video platform, fork of calesthio/OpenMontage | next: astra-reaper-mix REV3 is DELIVERED 2026-09-08 - same 4:30.3 cut as rev2 but the page-wide cream overlay panel is replaced with compact dark text cards, the mic-cut disclosure moved to the top so it no longer stacks on captions, and all 16 overlay lines were rewritten in David's voice; rev2 and original 6:18.9 retained; the SHORT got the same card treatment as short_rev3 (50.9s, cuts and audio unchanged, new mic-cut card), 50.9s Short, SRTs and social copy in C:/media/video/astra-reaper-mix/final/; BOTH THUMBNAILS REVISED using David's selected smiling candidate 2 at camera 12:20.4; both videos pass raw-source sync and frame checks, one subtitle timing defect fixed; recovered camera audio supplies the ending because both clean mics stop at 970.6s; END-TO-END HUMAN WATCH/LISTEN APPROVAL IS STILL OUTSTANDING; signals-static-uap is DELIVERED through cut 07 - 2026-09-07 added 06-under-the-surface (43.2s) and 07-held-in-the-box (43.5s), both silent 9:16, in C:/media/video/signals-and-static/final/ plus projects/signals-static-uap/out/; the whole 133-file archive is now screened so there is no unscreened pool left; POST-COPY.md carries captions and hashtags for all seven, work/ledger.py regenerates CLIP-LEDGER.md and FAILS if a source file appears in two cuts, and NOBODY HAS WATCHED ANY OF THE SEVEN END TO END; claude-learn-by-example is BUILT 2026-08-28 - 2:49.9 long-form master plus a 54.8s vertical Short, both in C:/media/video/claude-learn-by-example/final/, VO-later (script is next to the master), NOBODY HAS WATCHED EITHER CUT; claude-band-reaper-daemon is DELIVERED 2026-08-27 - 6:25.9 long-form master, 53.0s vertical Short, both thumbnails and the social package, all in C:/media/video/claude-band-reaper-daemon/final/, revised twice after David caught edit points landing inside words - and NOBODY HAS WATCHED EITHER CUT END TO END, which is the only open item; codex-reaper-daemon is DELIVERED (4m24.1s master plus a 49.7s vertical SHORT delivered 2026-08-24, both in C:/media/video/codex-reaper-daemon/final/) and BOTH need David's watch before upload; the master's .srt has one wrong word at cue 56 - it says "See, Codex officially sucks at this shit" and the source says "Yeah," - not fixed yet; the delivered ox-alpha Short is 96 kHz AAC from a loudnorm/aac interaction, harmless in playback but wrong in a master, rebuild fixes it; Ox Alpha SHORT is built and delivered (47.2s vertical, needs David's watch); the Ox Alpha LONG-FORM cut is still parked on its 11-box human safety sweep and nothing long-form is delivered; WGYC sailboat is DONE - rev2 and the Short are both audited by David, public on YouTube, and rev2 is with Camilla; the beds shipped as-is; reaper-daemon-drums is BROKEN - source has 35s of digital silence over the cold open and the payoff, needs the REAPER groove bounced or a re-record before anything else
# HANDOFF - OpenMontage

> current: astra-full-jam REV3 is DELIVERED 2026-09-11 (5:30 long, 51.4s Short; portrait camera handled correctly, dead air and restarts cut, bed at -20 dB, DPD cards). Next action is David's end-to-end watch and listen, then upload only if authorized.

## 2026-09-11 - Astra full jam revision 3: portrait camera, dead air, bed level

David rejected rev2 on playback: camera stretched, bed inaudible, dead air and his own restarts left in. Root cause of the stretch: the phone MOV reports 3840x2160 but carries rotation=90, so ffmpeg decodes it as 2160x3840 portrait; rev2 scaled that to 16:9. Codex's original 2160x1215 crop was a 16:9 window of the portrait frame, which is why it looked punched in. Rev2's preview frame was scaled the same wrong way, so the check passed a wrong picture.

Rev3 (`projects/astra-full-jam/build.py`, mirrored to the delivery's `working/edit-source/`): long camera cuts composite the live desktop (1056x570, left) with a 4:5 window of the portrait camera (864x1080, right) on DPD black, cards centered over the desktop half. Short camera-only cuts use the portrait frame natively; screen+camera cuts take a 5:4 window from the top. Bed raised from -31 to -20 dB. EDL trims: dropped `building` ("any second now"), the first take of the section-four note, the stray "Yeah" and 14s of silence in `freedom`, 5s at the end of `bridge`, 13s of the first-pass wait, 9s of the autosave search, 4s inside "Awesome / Thank God for backup saves". Long is now 5:29.967 (9,899 frames), Short 51.367s (1,541 frames). Chapters regenerated in `chapters.txt`, `SOCIAL-COPY.md`, and the long description (every chapter at least 10s). Loudness -18.8 / -18.5 LUFS, decode clean, every-cut frame boards inspected.

Still unwatched end to end by a human. Thumbnails were not regenerated.

## 2026-09-11 - Astra full jam revision 2: framing, bed, overlays

David rejected the Codex cut: camera cropped 1.8x into his face (grainy, uncomfortably close), a stock bed instead of Wretcher music, and overlays that ignored the workflow. Rev2 keeps every edit point, timing, and audio cut from the first delivery and changes only picture treatment, bed, and overlays. Overwrote `C:/media/video/astra-full-jam/final/` in place (long 6:46.767, Short 55.367s, same frame counts 12,203 / 1,661, -18.8 / -18.5 LUFS, -1.1 / -1.7 dBTP, full decode).

What changed in `projects/astra-full-jam/build.py` (gitignored, mirrored to `final/working/edit-source/`): long camera is the full 3840x2160 frame scaled to 1080p, no face crop. Bed is Wretcher `stigmergy-master.wav` 62 to 88s looped with crossfades (`bed/stigmergy-bed-loop.wav`), at -31 dB under speech, faded per cut, absent during REAPER playback. Overlays are DPD cards: DPD Display headline, Inter subline, `#0b0b0b` at 0.9, `#f2f2ef` text, `#7fa57a` hairline, sized to text via Pillow; long cards sit centered 72px above the bottom (no burned captions in the long), Short cards sit in a top zone with burned captions at the bottom of the camera zone so nothing stacks. Fonts converted from `C:/brand/dpd/fonts/*.woff2` to TTF in `projects/astra-full-jam/fonts/` with fontTools (now in the venv); libass gets `fontsdir=fonts` so Short captions render in Inter. Short layout: card zone, per-cut `focus` crop of the screen (chat window or arrange lanes, set in `edl.py`), 5:4 camera crop at y=1056; camera-only Short cuts use a 9:16 crop around the face. Two labels replaced after david-voice SCORE: "NO NETWORK, JUST FILES" and "ONE SNAPSHOT, EVERY CHANGE AT ONCE".

Verified: every-cut frame boards for both cuts inspected, caption font confirmed in the ass log, loudness and decode via `qa.py`. Thumbnails, SRTs, and social copy are unchanged from the first delivery. Nobody has watched either cut end to end; that remains the gate before upload.

## 2026-09-11 - Astra full jam release package

Delivered `C:/media/video/astra-full-jam/final/`: 6:46.767 horizontal long-form video, 55.367s independently composed vertical Short with burned captions, horizontal and vertical thumbnail masters plus upload JPGs, SRT sidecars, chapters, verified links, full social copy, and plain-text YouTube descriptions. Nothing was uploaded or published. Original desktop and camera recordings are unchanged.

Editorial arc: five guitar parts in Drop C at 126 BPM, request for Nolly Bass Library and RS Drums Monarch, REAPER Daemon local-file-bridge explanation, first playback, specific cymbal feedback, Astra's revision, REAPER crash, backup recovery, restored playback, final reaction, and conclusion. A continuity defect that ended on "There's no..." was caught before delivery; the cut now preserves the complete no-network-server explanation and the SRT wording was corrected to match it.

Verification: source ingest passed with caution because camera audio is only scratch. Picture sync uses the measured camera mapping with less than 1ms residual and no camera audio enters delivery. Both final MP4s fully decode. Long is 12,203 frames, 1920x1080, 30fps, H.264, BT.709 limited, stereo AAC 48kHz, -18.80 LUFS and -1.30 dBTP. Short is 1,661 frames, 1080x1920, otherwise the same delivery shape, -18.53 LUFS and -1.59 dBTP. Every-cut rendered frame boards and phone-size thumbnail boards were inspected. `qc-report.json`, SHA-256 inventory, ingest report, scripts, and manifests are in the delivery folder.

Public copy passed the David voice profile and remains draft. Vault notes: `second-brain/content/astra-full-jam-long.md` and `astra-full-jam-short.md`. Publishing dependency: after the long upload exists, attach it as the Short's Related video because Shorts description/comment URLs are not clickable. End-to-end human watch/listen approval remains outstanding and is the only acceptance gate before upload.

## 2026-09-10 - Astra riff release and reusable video workflow

Delivered `C:/media/video/astra-riff-band/final/`: 4:58.133 horizontal video, 59.833s vertical Short, both thumbnail formats/masters, captions, chapters, separate YouTube/Facebook/LinkedIn packages, paste-ready descriptions and link provenance. Editable project and detailed evidence: `projects/astra-riff-band/README.md`. Original footage unchanged; nothing uploaded. User requested prominent REAPER Daemon promotion and modern YouTube descriptions; those corrections are in `packaging.py`, delivered text and both vault drafts.

Wrap checked file inventory and existing QC reports: 8944/1795 frames, 30fps, stereo 48kHz, BT.709 limited, measured cut audio correlation above .997. Original delivery reports document decode, rendered frames and sampled sync; no end-to-end human listening approval. Next action: David's watchthrough, then upload if authorized. Set long upload as the Short's Related video before using the supplied Short description; profile-link setup is also pending.

Reusable `video-production` skill: `C:/Users/wretc/.codex/shared-skills/video-production/SKILL.md`; references contain a brief and owned-link inventory. `video-launch-package` now includes featured-tool promotion and current voice-profile path. Reusable prompt: `second-brain/prompts/dpd-recorded-video-release.md`. Workflow is agent-led, not a new unattended renderer. Skill validation passed; the workflow has not yet been exercised on a second shoot.

Wrap repaired a self-referential skill entry: `.agents/skills` and shared-skills paths resolve to the same files here, so writing a forwarding entry overwrote the actual skill. Full instructions restored; do not create a pointer back to that same path. Local WORKFLOW/LEARNINGS, skills and production assets are intentionally outside tracked OpenMontage source. No deployment occurred.

## 2026-09-08 - approved Wellcraft intermediate cleanup

David approved disk cleanup. Generated MOV/MP4 files under `C:/media/video/wgyc-camper-top-wellcraft-v20/working/conform/` and `working/proxies/` were deleted (16.37 GiB). All 40 camera clips selected by `projects/wgyc-camper-top/conform.py` exist. Raw footage and both Wellcraft final-export folders retained their file identities, sizes, and modification times; `parts.txt`, both selectmaps, `conform.py`, and `project.json` retained their SHA-256 hashes. Scripts and metadata remain.

Before rerendering the Wellcraft long or Short, regenerate `working/conform/conform.mov` with `.venv/Scripts/python.exe projects/wgyc-camper-top/conform.py` from the repository root. `project.json` still points to that intentionally removed intermediate. No regeneration was run during cleanup. Cleanup receipt and exact approved manifest are in `C:/Users/wretc/Documents/Codex/2026-09-08/i-d/outputs/`.

Upstream clone plus local work. Contribute changes upstream rather than
diverging.

## 2026-09-08 - astra-reaper-mix revision 3: overlay cards and rewritten copy

**Short rev3 (same day):** `C:/media/video/astra-reaper-mix/final/2026-09-08_astra-reaper-mix-short_rev3_master.mp4` plus SRT and `SHORT-REVISION-3-REPORT.md`. Same cards and rewritten copy, plus a mic-cut card on the verdict cut at chest height. `projects/astra-reaper-mix/short_revision3.py` rebuilds it. 6/6 audio, integrity, 6/6 picture pass; the verifier's resolution check keys on a folder named exactly `short`, so it was re-evaluated by hand (file is 1080x1920). The `card_label` branch in `build.py` now handles both kinds and the Short caption path is out-relative. Unwatched end to end.

David's verdict on rev2: flat, a white box covering the bottom of the screen, captions stacked on screen text, copy with no personality. Rev3 keeps every cut, timing, audio and caption from rev2 and changes only the overlays.

**Delivered:** `C:/media/video/astra-reaper-mix/final/2026-09-08_astra-reaper-mix_rev3_master.mp4` (145,047,836 bytes, 4:30.3), matching SRT, `SOCIAL-COPY-REV3.md` (rev2 copy with the filename swapped; chapters unchanged), `REVISION-3-REPORT.md`. Rev2, the original, the Short and thumbnails are untouched.

**What changed:** the 1600px cream `drawbox` panel became a dark card sized to its text via Pillow measurement (`card_label` branch in `build.py`), centered near the bottom with an amber accent line. The ending disclosure sits at y=60 above the burned captions. Label durations capped at 5 to 8s except Before/After (13s) and the disclosure (9s). All 16 labels rewritten; the david-voice scorer flagged six as stiff or spec-sheet flat and those were replaced before rendering. Full label table in `long-rev3/REVISION-REPORT.md`.

**Verification:** `verify_revision3.py` passes 26/26 audio cuts, integrity, 12/12 camera picture checks. 78 cut samples plus a full-size ending frame inspected on review boards. Nobody has watched rev3 end to end; that is David's next check.

**Rebuild:** `projects/astra-reaper-mix/revision3.py` (imports rev2's edit list), then `verify_revision3.py`, `review_revision3.py`, `deliver_revision3.py`, all from the checkout `.venv` (system Python lacks scipy). The media mirror under `working/edit-source/` had no cached clips, so the render there was a full rebuild from the `_inbox` sources.

## 2026-09-08 - astra-reaper-mix revision 2: tighter cut and readable explanations

David liked the original cuts but requested less dead space, explanations during the DAW shots, larger and brighter overlays away from the corner, and an explicit note explaining the switch to phone audio.

**Delivered revision:** `C:/media/video/astra-reaper-mix/final/2026-09-08_astra-reaper-mix_rev2_master.mp4` and matching SRT. Duration is **4:30.3**, down from 6:18.9. `SOCIAL-COPY-REV2.md` in the same folder has corrected chapters: before/after at 3:41, closing verdict at 4:07. The original video, Short and selected thumbnails remain intact.

The music-only listening sections are shorter. All spoken sections, the fader-intervention caveat and the matched 13-second before/13-second after comparison remain. Corner labels are replaced with centered 64px/54px dark text on solid light panels. The closing notice reads "My mic cut out / This ending uses my phone audio" for nine seconds above the existing closing captions.

**Verified on the revised MP4:** 8,109 frames with complete decode and continuous timestamps; 1920x1080, 30fps, H.264, stereo AAC at 48kHz. All 26 cuts pass raw-source audio alignment. Eleven of twelve camera cuts have decisive picture matches within one frame; the six-second listening reaction is visually inconclusive because it is nearly still, with no detected offset failure. All 78 opening/middle/end cut frames and one full-size ending frame were reviewed. All 61 spoken caption texts are preserved and retimed within cuts. Delivered copies pass SHA-256 comparison; video hash is `e7cd57aaf357cd523aac615cefc3d27ecd6480b15baad277371d8c5dfcca1c37`.

**Review limit:** Chrome's local-file security policy blocked playback, and no workaround was attempted. Revision 2 has not received an end-to-end human watch/listen. That remains David's next check.

**Rebuild:** `projects/astra-reaper-mix/revision2.py` writes `long-rev2/`, retaining the original FFmpeg/audio path. `verify_revision2.py`, `review_revision2.py`, and `deliver_revision2.py` cover verification and delivery. Scripts and revision artifacts/reports are mirrored under `C:/media/video/astra-reaper-mix/working/edit-source/`. The inherited production has no earlier pipeline checkpoints; the checkpoint writer refused the missing prerequisites. Schema-valid edit/report artifacts are saved directly, with that limitation documented in `long-rev2/REVISION-REPORT.md`. No historical approvals were fabricated. No uploads or paid services.

## 2026-09-08 - astra-reaper-mix: original YouTube package delivered

David's GPT-6 Astra / REAPER Daemon recording is cut to **6:18.9** for YouTube and **50.9 seconds** for the companion Short. Both MP4s, subtitle files, two thumbnails and `SOCIAL-COPY.md` are in `C:/media/video/astra-reaper-mix/final/`. The main filenames are `2026-09-08_astra-reaper-mix_master.mp4` and `2026-09-08_astra-reaper-mix-short_master.mp4`.

The edit includes the starting mix, actual processing and listening, David's fader intervention, playback inside Codex, the same passage before/after at matched listening level, and his basic-pass caveat. The Short is composed from raw camera and screen sources.

**Thumbnails revised with David's selection:** after rejecting the initial sleepy portrait and the subsequent 1019.8s portrait, David chose smiling candidate 2/B at camera 740.4s (12:20.4), looking toward the monitor. Both final thumbnail JPGs now use this reference, via native OpenAI image editing. The smile, relaxed eyes, head angle, full compositions and phone-size previews were visually checked. These are source-guided generated composites, not literal unchanged source-pixel cutouts. Horizontal is 1920x1080 / 301004 bytes; vertical is 1080x1920 / 314405 bytes. The selected original, native PNG masters, review board and exact prompts are mirrored under `C:/media/video/astra-reaper-mix/working/edit-source/`; unaltered candidate frames remain in `working/thumbnail-candidates/`. The rejected pair is preserved under `projects/astra-reaper-mix/thumbs/archive/rejected-alert-expression/`. Both videos, subtitles and the social copy are unchanged.

**Recovered ending:** both clean microphone recordings become silent at about 970.6s. The iPhone continues, so its audio supplies the closing verdict. It was conservatively restored and level-adjusted with the denoiser's measured latency compensated. The closing section has burned captions and remains roomier than the clean mic. A bounded Clarity Vx attempt failed in an isolated scratch host; no replacement plugin or paid service was used, and David's REAPER session was untouched.

**Verified:** all 26 long cuts and 6 Short cuts match raw-source audio; 65 active waveform windows have at most 0.0625ms residual offset. All 36 camera-picture samples match raw frames within one 30fps frame. All 130 injected 100ms alignment errors were detected. Complete frame decoding and timestamps pass: 11,367 long frames and 1,527 Short frames. Both are H.264, BT.709 limited, stereo AAC at 48kHz, with source metadata removed. Loudness is -18.8 LUFS / -2.5dBTP long and -18.4 LUFS / -3.4dBTP Short; both before/after passages measure -18.6 LUFS. No unexplained black runs.

The Short passed 16/16 automatic caption checks. The long initially flagged 8 of 62; narrower delivered-audio review found one actual timing error, which was fixed. Its final sidecar has 61 cues. Remaining flags were recognition differences and a self-correction condensed for readable captions. No clipped final spoken words were found. Rendered opening/middle/end frames of every cut were reviewed, plus browser playback; this is **not end-to-end human viewing/listening approval**, which remains the next action before upload, especially for the recovered camera dialogue.

**Rebuild and evidence:** `projects/astra-reaper-mix/` is gitignored. Scripts, transcripts, caption sources, restoration audio and QC evidence are mirrored to `C:/media/video/astra-reaper-mix/working/edit-source/`. `edl.py` and `build.py` reproduce both edits; read their README for the clip-cache caveat. `RUN-REPORT.md` and `FILES.json` in the final folder record acceptance, limitations and verified copy hashes. Original footage remains at the supplied `_inbox` paths, untouched.

Public copy is also in `second-brain/content/astra-reaper-mix-video-social.md` and `astra-reaper-mix-short-social.md`, with draft publication status and a content-index link. Those three vault changes were committed and pushed as `0fa82ac`; unrelated vault work was preserved. Native Obsidian indexing had not exposed the new notes when checked, although disk content and links were verified. Nothing was uploaded or published.

## 2026-09-07 - signals-static-uap: cuts 06 and 07 DELIVERED, archive fully screened

Two more 9:16 silent cuts for the Signals & Static TikTok channel, and the end of the
screening backlog.

**Delivered** in `projects/signals-static-uap/out/` and mirrored to
`C:/media/video/signals-and-static/final/`:

| File | Length | Upload | Master |
|---|---|---|---|
| `06-under-the-surface.mp4` | 43.2s | 36 MB | 104 MB |
| `07-held-in-the-box.mp4` | 43.5s | 34 MB | 118 MB |

Both 1080x1920, 30 fps CFR, h264 High, yuv420p, faststart, **no audio stream at all**.
Same shape as 01-05: CRF 21 capped at 12 Mbit/s for upload, CRF 18 master in
`out/masters/`. Same structure too: cold open on the strongest shot, Signals & Static
card at ~3s, twelve clips at 3.2-3.5s, card again at the end.

**06 Under the Surface** is the sea and night cut. Its two real shots are DOD_111719799,
an underwater camera descending through deep blue water with a lit point in it, and
DOD_111689115, a large dark circle sitting on the sea surface with a tracking box on it.
It opens and closes underwater so it loops. It is the darkest of the seven by some way.

**07 Held in the Box** is the sensor cut: every clip is something being held in a reticle
or a track box. It carries the only two colour shots left in the archive, a blue-hour
mountain silhouette (DOD_111764213) and a vertical phone video of orange lights over trees
(DOD_111764177, the only natively 9:16 file in the folder).

**Each cut uses 10 source files across 12 clips, and no source file appears in more than
one of the seven cuts.** That is now enforced by `work/ledger.py`, which regenerates
`out/CLIP-LEDGER.md` from `v1.json` .. `v7.json` and exits non-zero on any reuse. Current
state: 84 clips, 55 source files, 7 cuts, passing.

**The archive is fully screened.** The remaining 84 unscreened files all have a verdict
now, in `work/screen2.tsv`: 10 strong, 12 usable, 56 rejected, and one more audio-only
file. The old ledger said fourteen audio-only NASA-logo files; it is **fifteen**, it
missed `DOD_111689232`. An eighth cut is possible but would be scraping.

**Two new scripts next to `build.py`**, all three mirrored to
`C:/media/video/signals-and-static/working/` because `projects/` is gitignored:
`ledger.py` (regenerate the ledger, enforce the no-reuse rule) and `deliver.py` (move the
CRF 18 master to `out/masters/` and write the capped upload file). That second step
existed for 01-05 but had never been written down, so it had to be reconstructed.
`build.py` gained one optional per-clip field, `eq`, for lifting exposure on a dark source
before the shared grade runs.

**Naming inconsistency in the 2026-09-05 mirror, not fixed:** the five files in
`C:/media/.../final/` named `..._master.mp4` are actually the capped upload copies, and
the real CRF 18 masters were never mirrored. The two new cuts are mirrored as both
`_upload` and `_master` and those labels are accurate. Do not assume the 09-05 `_master`
files are masters.

**Verified how:** ffprobe on both delivered files for container, resolution, frame rate,
profile and the absence of an audio stream; 24-frame contact sheets of each rendered file
read for structure, subject visibility and transitions, twice, with three clips re-cut
after the first pass because they read as dead black or the subject was too small;
full-resolution frame pulls on the specific clips that were in doubt; and `ledger.py`
proving programmatically that no source file is shared across the seven cuts.

**Not verified:** nobody has watched cut 06 or cut 07 end to end in real time. That is
still true of the first five as well.

**Traps, all written up in `LEARNINGS.md` (fork-local, mirrored to
`C:/media/video/signals-and-static/working/`):** reading contact sheets through parallel
subagents is what killed the two previous sessions, so screen in the main session in
batches and append verdicts to a TSV after each; `mode:"wide"` always renders the picture
at 1080x810 no matter what you crop, so use `mode:"letterbox"` with a measured crop when a
source is square or natively vertical; `cropdetect` lies on the files with white borders
and on dark night footage, so measure the picture area from a thresholded frame instead;
and a `crop` band written `2*floor(ih*K)` needs K to be half the band you want, not the
band. Also: `build.py` writes the master only, `deliver.py` writes the upload copy, and
running the second on a stale master is easy to do while a rebuild is still going.

**Repo hygiene, done this session:** the 14GB of source media under `assets/` and the two
title-card mp4s are now in `.git/info/exclude`, fork-locally, same as `wgyc-assets/`. They
had been showing as untracked on every `git status` and were a real `git add -A` hazard on
a repo that contributes upstream. The files are untouched on disk.

**Thumbnails exist but were not made by this session.** TikTok covers for 06 and 07
landed in `C:/media/video/signals-and-static/final/thumbnails/` at 21:53 on 2026-09-07,
written by a different Claude session ("Two new TikTok videos from fresh UAP footage",
offline by the time this was noticed). They are 1080x1920, match the house style of the
01-05 covers, and use the two hero frames: the underwater blue for 06 and the white object
in the track box for 07. Source frames are in `working/thumbnail-06-07/`. **I did not
create them and did not verify how they were produced.** Look at them before posting. The
cuts, the ledger and the post copy were confirmed byte-identical to what this session
mirrored, so that session touched nothing but thumbnails.

Unrelated, pre-existing: the cut 05 cover is named
`signals-static-05-out-of-the-box-tiktok-cover.png` while cut 05 is "the-approach" and cut
07 is "held-in-the-box". Worth a rename before anyone confuses the two.

**Next action:** watch all seven cuts end to end, then post. Order in `POST-COPY.md` is
1, 3, 5, 2, 4, then 7, then 6.

## 2026-09-05 - signals-static-uap: five 9:16 UAP cuts DELIVERED (silent, video only)

First five cuts for the Signals & Static TikTok channel, built from the
Department of War UAP releases in `assets/ufo-videos-raw/` (133 files).
Channel rules came from `~/second-brain/projects/signals-and-static.md`.

**Delivered** in `projects/signals-static-uap/out/` and mirrored to
`C:/media/video/signals-and-static/final/`:

| File | Length | Size |
|---|---|---|
| `01-dark-spheres.mp4` | 46.9s | 44 MB |
| `02-locked-on.mp4` | 43.2s | 35 MB |
| `03-lights-in-the-dark.mp4` | 43.5s | 34 MB |
| `04-contact-over-water.mp4` | 40.3s | 30 MB |
| `05-the-approach.mp4` | 43.0s | 28 MB |

All five: 1080x1920, 30 fps CFR, h264 High, yuv420p, faststart, **no audio
stream at all** (David is scoring these with TikTok sounds). CRF 21 capped at
12 Mbit/s for upload; CRF 18 masters kept in `out/masters/`.

**Structure of every cut:** cold open on the strongest shot, Signals & Static
title card at ~3s (source 6.0-8.0s, where the mark is fully assembled), montage
of 10 to 13 clips at 3.3-3.5s each, close on the title card again (5.0-8.4s,
which carries its own fade to black). Transitions are 0.3s dissolves with 0.1s
near-cuts for punch and 0.4-0.5s fade-to-black around the title cards. One
unified grade and grain pass over the whole timeline.

**Both ends use the Signals & Static card, confirmed by David 2026-09-05 as what
he wanted.** The assets folder also holds `dpd-Title Sequence.mp4`, which reads
"DEAD PIXEL DESIGN" on screen and would breach the channel note's ban on Dead
Pixel and Wretcher branding on this account. It is not used anywhere in these
five and should not be.

**Screening:** all 133 sources were contact-sheeted (24 frames each) and read by
six parallel subagents. 14 files are audio recordings with a frozen NASA logo
and a scrolling waveform, no imagery at any point - listed in `CLIP-LEDGER.md`
so nobody screens them again. ~45 more were rejected as empty grey infrared,
mostly-redacted, out of focus, or ordinary surveillance with no anomaly.

**35 source files used across 60 clips, and no source file appears in more than
one video.** That is checked programmatically by the ledger generator, not by
hand.

**One speed change, disclosed:** in `05-the-approach` the disc in DOD_111830075
is only legible from about 20.7s to 21.2s, so it runs at 35% to open the cut and
50% later. Both are called out in the caption in `POST-COPY.md`.

**Build:** `projects/signals-static-uap/work/build.py` takes an EDL json
(`v1.json` .. `v5.json` in the same folder) and does normalize-then-xfade-chain.
Because `projects/` is gitignored here, `build.py` and the five EDLs are also
copied to `C:/media/video/signals-and-static/working/` so the recipe survives.

**Traps are in `LEARNINGS.md`** (fork-local, excluded like `WORKFLOW.md`). Read it
before touching this or any other ffmpeg cut. The two that cost the most: an xfade
`duration` below about 0.05s silently truncates the entire chain with exit code 0,
and `-t` must come before `-i` or the output is clipped before a `setpts` slowdown
can stretch it. Also in there: `-pattern_type glob` is unsupported in this ffmpeg
build, `drawtext` cannot take a Windows drive-letter font path, and more than about
4 parallel ffmpeg jobs against `assets/ufo-videos-raw/` saturates the disk badly
enough to hang unrelated shell commands.

**Verified how:** ffprobe for container, resolution, frame rate and the absence of
an audio stream on all five; sampled-frame contact sheets of each rendered file for
structure, subject visibility and transitions; a dense 6 fps sample across the
video 5 opening to confirm the disc beat and the fade to black; and a programmatic
check that no source file appears in more than one video.

**Not verified:** nobody has watched any of the five end to end. Everything above
was confirmed from contact sheets of the rendered files plus ffprobe, not from
playback.

## 2026-08-29 - stigmergy-visualizer: 88.000s master ASSEMBLED (silent, pre-song)

Music visualizer for David's retro original "Stigmergy" (HF/OpenAI-incident
mood). Concept doc: `C:/media/photo/personal/the-cathedral/stigmergy-video-concept.md`.
13 etched plates animated (lamp sway, paper-to-face, writhing hands, cathedral
self-build, hooded approach, pixelate dissolve, wax-seal press, agent refuses,
agent startled by watch, notes-stuffing, vast pullback, rotunda chair, the last
note in wind). Picked up after the Fable-5 (claude-fable-5) Claude Code
subagent fanout hit the session limit at ~08:13 with shot_13 unrendered and no
assembly.

**Delivered** at
`C:/Users/wretc/workspace/OpenMontage/projects/stigmergy-visualizer/renders/stigmergy_master.mp4`:
- **88.000 s, 2640 frames decoded, 1920x1080, 30 fps CFR, h264 yuv420p,
  BT.709 tagged, tv range, crf 16, 754 MB** (large because per-frame grade
  grain is incompressible by design - bible section 7 mandates it).
- All 13 hard cuts land on timeline frames (110/197/332/482/612/762/872/982/
  1112/1292/1652/2112 - shot 3 hits frame 197 = 6.575s as the concept demands).
- 12-frame cold fade-in from black; 30-frame fade-out ending at luma ~0.004
  on frame 2640.
- Unified grade applied once over all frames in-float before encode (filmic
  S-curve, x0.88 desat, static vignette, per-frame sigma-5 grain, one shared
  0.5-2 Hz flicker track), per MOTION-BIBLE section 7.

**Built by**: prepped assets + MOTION-BIBLE + timeline.json + 13 specs +
engine/anim.py + 13 shot builders were Fable 5's work (verified, not redone);
Hermes rendered `shot_13.mp4` (528f) and wrote `engine/assemble.py`
(the section-7 grade + concat), then encoded the master. Old `renders/smoke.mp4` and a
48-byte `shot_13.mp4` stub from the killed re-attempt were superseded.

**Not verified:** nobody has watched the master end to end. Video is SILENT by
design - the song is written but unmixed; mux it on later. Grade white-point
clips at 0.97 per bible "never full white" (shot 12's neon-cyan oculus is the
source plate's own style, not a grade defect).

**Left for David:** watch the master; mix "Stigmergy" and mux the bed in. The
OpenMontage venv still lacks scipy (shot code avoids it - fine as-is).

## 2026-08-28 - claude-learn-by-example: long form, Short, VO script

VO-later process film. He humanizes seven bars of drums by hand, Claude
learns the rest, he corrects the golden rule, they make it a skill.

**On disk, probed 2026-08-28 wrap** at
`C:/media/video/claude-learn-by-example/final/`:

- `2026-08-28_claude-learn-by-example_master.mp4` — **169.90s (2:49.9)**,
  5097 frames, 1920x1080, 30fps CFR, yuv420p tv BT.709, AAC 48 kHz,
  43,804,158 bytes
- `2026-08-28_claude-learn-by-example-short_master.mp4` — **54.80s**,
  1644 frames, 1080x1920, 30fps CFR, yuv420p tv BT.709, AAC 48 kHz,
  5,333,891 bytes
- `VO-SCRIPT.md` — timed to the long cut after the Magpie recut. Record
  to picture. Do not talk over listen / thall.

Inbox is empty. Raws in `.../raw/`. Build in gitignored
`projects/claude-learn-by-example/` and `-short/`. Read `RUN-REPORT.md`
before revising.

**Verified, and how**

- ffprobe on both files in `final/` (wrap): duration, frame count, 30fps,
  BT.709 limited, AAC 48 kHz match the numbers above.
- Magpie recut: prompt out at source 19.00, lapse_a in at 28.00. 1fps
  safety sheet of current `rough_v.mp4` is 170 frames. Program stills
  18–25s have no Magpie popup.
- EVALUATION LICENSE cropped off the long cut (y=24). Short MIDI crop was
  rebuilt from y=24 after the first Short showed the license bar.
- No Orca window on this tape (full 17:44 scan). No drawn circles.

**Not verified:** nobody has watched either cut with eyes or ears.

**Left for David:** watch both; record the VO from `VO-SCRIPT.md`; talking
head if he still wants it. Thumbnails are a paid Codex call, not made.

**Traps**

- Magpie opens at source 19.5s with unrelated clipboard text and a
  metr.org URL. Do not widen the prompt clip past 19.00. Second hit ~60s.
- `montage.py audio` on a mute-program mix program-trims the bed and
  boosts the drums. Mix bed at mus_alone, leave B-roll at recorded level,
  limiter only.
- Short MIDI crop at y=0 puts `EVALUATION LICENSE` back on screen. y=24.
- Bars 8+ leave flat 127 at **197.5s**, which is inside the wait lapse.
  The held after-shot is overlay-off at 348s. A recut that wants the
  write at full speed starts there.
- This HANDOFF edit is **uncommitted**. The repo is on
  `fix/music-capability-discovery` with hundreds of unrelated skill
  deletions. Do not commit video status onto that PR. Copied paper trail
  also lives next to the masters in `final/`.

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

## 2026-09-10: agent instruction audit

Updated the local agent guidance to use task-relevant references and the shared autonomy/voice-profile agreement. Product and taste requirements remain in the instructions. Verified the instruction diff and reference paths; application behavior was not part of this documentation audit. Full file-by-file record: `C:/Users/wretc/workspace/AGENTS-AUDIT-2026-09-10.md`.
