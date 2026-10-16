> status: active | latest recorded production work: ChatGPT reinstall revision 3 | next: inspect the requested project's files and outstanding human review before revising or publishing

# OpenMontage current handoff

## Repository snapshot, September 12, 2026

Local branch `fix/music-capability-discovery` at `2d1d89b` when this handoff was condensed. `fork` is the personal fork; `origin` is upstream. Verify current Git state before development. This update does not claim a new render, watchthrough, upstream PR status or deployment.

## Production entrypoints

`WORKFLOW.md` is the local production contract. `C:/Users/wretc/.codex/shared-skills/video-production/SKILL.md` is the shared recorded-release workflow; Claude now resolves to the same directory. Its client reference overrides Dead Pixel branding, voice and music defaults for client work. Preserve editorial judgment and explicit source/audio/sync requirements.

Editable work is in `projects/<slug>/`; delivery is under `C:/media/video/<slug>/final/`. Projects and local workflow notes are intentionally outside upstream Git tracking. A clean Git status is not proof that production material has a recoverable off-device backup.

## Latest dated production records

- ChatGPT reinstall revision3: David rejected revision2 on framing. The 50/50 hero split crushed the ChatGPT window into half a frame where beginner UI text is not legible, every crop was letterboxed into black wedges, and the cold open ran the finished shopping list from 7:09 under the generic hook, with a stray annotation tooltip resident through the whole list chapter. Revision3 is picture only: `projects/chatgpt-reinstall/r3_build.py` with `r3/edl.json`, reusing the r2 mix and captions byte for byte, so runtimes and caption timing are unchanged. Three framings now carry it - screen full frame, screen plus a bordered camera card, and camera at its recorded portrait framing over a darkened surround for talk beats, since any 16:9 crop of that close phone shot is a face punch-in. Eighteen framings are hand-authored in `fitcrop`. Short is camera full frame with the screen as a card. Delivered to `C:/media/video/chatgpt-reinstall/final/revision-3/`. Start at `projects/chatgpt-reinstall/r3/REVISION-NOTES.md`. Human watch and listen still pending; audio was not re-touched so the revision2 listening gate stands unmet.

- Astra Celine Dion revision2: David rejected revision1 as unintentional and visually ugly. Rebuilt long1:58.6 and Short54.5s in `C:/media/video/astra-celine-dion/final/revision-2/`; build montage cut 42s to 22.6s on legible Serum/REAPER crops, labels now DPD cards with hold windows, listening section shows the live playhead and mixer, lanczos throughout, verdict/signoff cropped above REAPER's OFFLINE reference track. Sources are `projects/astra-celine-dion/edl2.py`, `build2.py`, `subs2.py`; revision1 preserved. Decode, frame review and camera-sync checks passed; audible playback still required. Nothing published.

- ChatGPT reinstall: September12 long8:34.7 and Short46.9s, two thumbnails and complete multi-platform packages in `C:/media/video/chatgpt-reinstall/final/`. Editable EDL and checks in `projects/chatgpt-reinstall/`. Full decode and numerical sync/loudness checks passed; human watch/listen remains because this session could not hear audio. No publishing.

- Astra full jam: September 11 revision 3 covers portrait-camera framing, dead air and bed levels. Start with `projects/astra-full-jam/` and its final exports. The complete September 11 records are at the beginning of the history file.
- Astra riff release: September 10 record includes long video, companion Short, thumbnails and posting packages, with remaining human watch/listen approval recorded.
- Astra REAPER mix: September 8 revision 3 replaces the large cream overlays with compact dark cards. Preserve the recovered camera-audio ending and recorded mic-failure disclosure. Earlier revisions remain retained.
- Wellcraft: selected generated conform/proxy media was deliberately removed September 8. Rebuild using `projects/wgyc-camper-top/conform.py` before rerendering. Missing intermediates are not missing camera originals.
- Signals and Static: seven silent vertical cuts have source ledgers; do not reuse a source across those cuts without changing the brief.

Treat review status in these records as historical until the user or actual delivery record confirms it. Uploading and publishing are separate actions.

## Development and older work

Consult the requested feature in the repository, not old handoff claims about open PRs or test counts. Older music-selector and WGYC blocker notes are retained but have not been revalidated here.

## History

The complete previous handoff is preserved byte-for-byte in `handoff-history-2026-09-12.md`. It contains both newer entries near the top and older append-only entries near the bottom; search by date/project rather than assuming file order indicates recency.

September 12 system sweep: condensed this entrypoint without changing edits, original footage or delivered masters.

- Astra Dystropia (September 13): long 4:20 and Short 53.6s cut against the September 12 YouTube analysis, in `C:/media/video/astra-dystropia/final/` with draft descriptions, chapters, verified links and multi-platform copy. Editable `projects/astra-dystropia/` (`edl.py`, `build.py`, `copy/labels.json`). Overlays are PIL-rendered dark cards (Inter SemiBold) and rounded highlight boxes mapped from source coordinates; Short text beats use a new `stack` mode. Boundary audit fixed four clipped joins. Human watch/listen pending; nothing published.
- Astra Dystropia revision 2 (September 13): David rejected rev1 (random MC77 cold open, crops hanging off screen and zoomed into grain, AI-looking cards, long crash section, phone-audio outro, lips ahead of sound). Rev2 in `C:/media/video/astra-dystropia/final/revision-2/` (long 3:35.3, Short 49.8s): no cold open, every long screen shot is the full uncropped screen, camera in a bottom-left box on talk/listen shots, captions on picture, only Before/With cards, crash cut to "on one tonight", Karacter shot dropped (he removed it in session), outro cut because the desk mic is digital silence there, camera picture delayed 2 frames. Rev1 sources in `projects/astra-dystropia/r1-backup/`; stills reviewed in `review2/final/`. Per-video editing rule memories were archived to `projects/_archived-video-rules-2026-09-13/` at David's request. Human watch/listen pending.
