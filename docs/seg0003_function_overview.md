# seg0003 function overview

This document is a standalone working inventory for `asm/seg003_code.s`. It is intentionally broad rather than final: each row lists a discovered `func3_*` entry point, its source line, approximate assembly span, current documentation status, and the best current note. Rows marked **TBD** have not yet received a dedicated reverse-engineering/comment pass.

## Progress snapshot

- Total `func3_*` entry points found: **688**.
- Functions with dedicated notes so far: **61**.
- Remaining functions needing detailed notes: **627**.
- Source of truth for line numbers: `asm/seg003_code.s`.
- Latest completed batch: rows **52–61** (`func3_800F3E88` through `func3_800F60D8`) now have first-pass notes and corresponding `asm/seg003_code.s` annotations.

## How to use this tracker

- Treat **Documented/partially documented** as "has a first-pass note/comment", not as a final decompilation-quality name.
- Treat **TBD** as the queue for future passes; each batch should update both `asm/seg003_code.s` comments and the corresponding row here.
- Keep the `Line` and `Approx. span` columns in sync with `asm/seg003_code.s` after comment-only edits, since downstream line numbers move frequently during this documentation pass.

## Spirit meter / HUD opening block

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 1 | `func3_UpdateSpiritMeterHud` | 7 | 1 lines | Documented/partially documented | Spirit meter HUD update entry point; aliases directly into func3_800ED020. |
| 2 | `func3_800ED020` | 8 | 927 lines | Documented/partially documented | Updates player spirit/special HUD meters, pulse animation, flash blending, and related per-player meter state. |
| 3 | `func3_800EDC0C` | 935 | 154 lines | Documented/partially documented | Resets a player SPECIAL flash counter after the low-time blink interval completes. |
| 4 | `func3_800EDE38` | 1089 | 333 lines | Documented/partially documented | Continues spirit/special HUD rendering and meter-state update logic. |
| 5 | `func3_800EE284` | 1422 | 29 lines | Documented/partially documented | Small helper in the spirit/HUD region; needs full pass to name precisely. |
| 6 | `func3_800EE2D8` | 1451 | 51 lines | Documented/partially documented | Small helper in the spirit/HUD region; needs full pass to name precisely. |
| 7 | `func3_800EE37C` | 1502 | 343 lines | Documented/partially documented | Spirit/HUD helper handling meter or flash-state calculations; needs full pass. |
| 8 | `func3_800EE774` | 1845 | 42 lines | Documented/partially documented | Spirit/HUD helper; likely state or visual reset around the meter update block. |
| 9 | `func3_800EE7E8` | 1887 | 122 lines | Documented/partially documented | Spirit/HUD helper; likely computes or stores meter display attributes. |
| 10 | `func3_800EE954` | 2009 | 420 lines | Documented/partially documented | Large spirit/HUD routine coordinating per-player meter drawing/update behavior. |
| 11 | `func3_800EEE6C` | 2429 | 5 lines | Documented/partially documented | Tiny wrapper/helper in the HUD/referee transition area. |
| 12 | `func3_800EEE74` | 2434 | 7 lines | Documented/partially documented | Tiny wrapper/helper in the HUD/referee transition area. |
| 13 | `func3_800EEE7C` | 2441 | 74 lines | Documented/partially documented | Tiny wrapper/helper in the HUD/referee transition area. |
| 14 | `func3_800EEF44` | 2515 | 248 lines | Documented/partially documented | Initializes or updates a small HUD/referee-related state block; needs full pass. |
## Referee overlays and big-message helpers

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 15 | `func3_800EF294` | 2763 | 113 lines | Documented/partially documented | Initializes referee overlay globals/frame state before the referee update routines. |
| 16 | `func3_800EF3B4` | 2876 | 9 lines | Documented/partially documented | Tiny wrapper into the referee frame updater. |
| 17 | `func3_800EF3BC` | 2885 | 243 lines | Documented/partially documented | Advances and renders active referee overlay frame sequences, including slide-out/inactive behavior. |
| 18 | `func3_800EF698` | 3128 | 151 lines | Documented/partially documented | Starts a referee animation state and special-cases state 9 to queue FIGHT/round/final-round big messages. |
| 19 | `func3_800EF834` | 3279 | 44 lines | Documented/partially documented | Starts the rope-break referee animation and queues the ROPE BREAK big-message when allowed. |
| 20 | `func3_800EF898` | 3323 | 42 lines | Documented/partially documented | Starts the two-count referee animation and queues the TWO COUNT big-message when allowed. |
| 21 | `func3_800EF8FC` | 3365 | 15 lines | Documented/partially documented | Starts a referee animation wrapper without installing a big-message script. |
| 22 | `func3_800EF91C` | 3380 | 18 lines | Documented/partially documented | Starts a pinfall/count-related referee animation wrapper. |
| 23 | `func3_800EF93C` | 3398 | 83 lines | Documented/partially documented | Queues/starts a down-points referee/big-message variant with active-message and suppression gates. |
| 24 | `func3_800EFA0C` | 3481 | 85 lines | Documented/partially documented | Queues/starts a points-style referee/big-message variant, computing an auxiliary message offset. |
| 25 | `func3_800EFADC` | 3566 | 80 lines | Documented/partially documented | Queues/starts another points-style referee/big-message variant with suppression checks. |
| 26 | `func3_800EFBAC` | 3646 | 23 lines | Documented/partially documented | Clears the active referee animation and seeds the inactive/slide-out timer. |
| 27 | `func3_800EFBD4` | 3669 | 29 lines | Documented/partially documented | Refreshes/replays the round-start/fight referee flow by invoking state 9 again. |
## Match scene lifecycle, transforms, and camera framing

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 28 | `func3_800EFC10` | 3698 | 19 lines | Documented/partially documented | Entry wrapper for match/arena setup, including option setup before the main continuation. |
| 29 | `func3_800EFC4C` | 3717 | 292 lines | Documented/partially documented | Main match setup continuation: scene/object allocation, per-slot init, HUD setup, and sound/table setup. |
| 30 | `func3_800EFFFC` | 4009 | 37 lines | Documented/partially documented | Small setup helper near match-scene initialization; needs full pass. |
| 31 | `func3_800F0054` | 4046 | 237 lines | Documented/partially documented | Per-frame match scene update: suppression cache, transform push, slot updates, stage/HUD hooks, and buffer flip. |
| 32 | `func3_800F032C` | 4283 | 44 lines | Documented/partially documented | Begins match-scene teardown/cleanup sequence. |
| 33 | `func3_800F03A0` | 4327 | 34 lines | Documented/partially documented | Teardown continuation that releases or resets remaining match-scene resources. |
| 34 | `func3_800F03E4` | 4361 | 49 lines | Documented/partially documented | Per-object transform update/copy helper used by the match scene. |
| 35 | `func3_800F045C` | 4410 | 33 lines | Documented/partially documented | Copies/negates transform components between buffers for scene/camera use. |
| 36 | `func3_800F04B0` | 4443 | 43 lines | Documented/partially documented | Derives and stores participant/focus indices for later camera or scene logic. |
| 37 | `func3_800F051C` | 4486 | 13 lines | Documented/partially documented | Tiny helper around focus/index storage. |
| 38 | `func3_800F0528` | 4499 | 329 lines | Documented/partially documented | Processes queued focus/masking events and dispatches camera/selection updates. |
| 39 | `func3_800F08E8` | 4828 | 138 lines | Documented/partially documented | Computes camera framing from selected/focused participants by scanning positions and deriving bounds/targets. |
| 40 | `func3_800F0A90` | 4966 | 131 lines | Documented/partially documented | Continuation of camera framing: clamps/scales derived radius and handles close-up fallback cases. |
| 41 | `func3_800F0C40` | 5097 | 329 lines | Documented/partially documented | Continuation of camera framing with additional participant-distance checks before final target writes. |
## Unreviewed gameplay block A

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 42 | `func3_800F1080` | 5426 | 80 lines | Documented/partially documented | Final camera-target smoothing/export block shared with func3_800F08E8; eases the live distance component and mirrors camera globals into the render-facing transform block with sign flips. |
| 43 | `func3_800F1190` | 5506 | 25 lines | Documented/partially documented | Epilogue label for the camera-target helper; restores callee-saved floating-point registers and returns rather than acting as an independent routine. |
| 44 | `func3_800F11A4` | 5531 | 21 lines | Documented/partially documented | Full-prologue entry for a two-participant camera framing mode; saves state before entering the shared body at func3_800F11EC. |
| 45 | `func3_800F11EC` | 5552 | 1681 lines | Documented/partially documented | Shared two-wrestler camera body: reads a pair descriptor, measures X/Y/Z separation from cached positions, derives midpoint/zoom buckets, and writes/smooths camera targets. |
| 46 | `func3_800F270C` | 7233 | 867 lines | Documented/partially documented | Alternate camera framing/update path: decodes a camera selector/flags, blends focus anchors with pair midpoints and mode presets, and smooths/exports camera globals. |
| 47 | `func3_800F323C` | 8100 | 427 lines | Documented/partially documented | Continuation of func3_800F270C that eases orbit angle, applies boundary checks, and converts angle/radius into pending X/Z camera targets. |
| 48 | `func3_800F37A4` | 8527 | 90 lines | Documented/partially documented | Continuation label inside func3_800F270C for easing bss3_8015D928 toward its pending distance target. |
| 49 | `func3_800F38D4` | 8617 | 59 lines | Documented/partially documented | Fade-in helper for the small overlay/color buffer: raises alpha toward 0xff, writes RGBA, clears the object hidden/disabled bit, and reports progress. |
| 50 | `func3_800F3978` | 8676 | 58 lines | Documented/partially documented | Fade-out helper paired with func3_800F38D4: lowers alpha, updates RGBA, and sets the object hidden/disabled bit once faded out. |
| 51 | `func3_800F3A00` | 8734 | 363 lines | Documented/partially documented | Builds the per-player broad-action context, runs shared per-frame maintenance hooks, then dispatches through ptrTbl_BroadActionRoutines using the current broad action id. |
| 52 | `func3_800F3E88` | 9097 | 89 lines | Documented/partially documented | Broad action 0x00 pre-match/no-control setup: installs neutral standing/apron idle animations, refreshes cosmetic/ring state, then waits for the global start flag before switching to normal idle/walk. |
| 53 | `func3_800F3F64` | 9186 | 237 lines | Documented/partially documented | Broad action 0x01 idle/walking dispatcher: handles taunts, apron/ring/outside transitions, battle royal entrants/outside-loss rules, tag/lumberjack gates, and normal movement fallback. |
| 54 | `func3_800F4210` | 9423 | 107 lines | Documented/partially documented | Continuation within idle/walk action for outside/apron match-rule checks; routes eligible cases to broad action 0x87 or continues normal location/control handling. |
| 55 | `func3_800F4338` | 9530 | 1170 lines | Documented/partially documented | Common idle/walk maintenance continuation: clears transient targets/timers, runs shared animation/movement hooks, tries context-specific handlers, and falls back to regular player-control processing. |
| 56 | `func3_800F5000` | 10700 | 874 lines | Documented/partially documented | Continuation for leapfrog/drop-down primary action: marks evasion during the active window, finds the paired runner, can trigger the secondary leapfrog/drop action, and resumes running updates. |
| 57 | `func3_800F5990` | 11574 | 140 lines | Documented/partially documented | Grapple-breakup action body: records interrupted animation kind, picks recovery animations/follow-up broad actions from small tables, and advances through breakup subtypes. |
| 58 | `func3_800F5AE8` | 11714 | 144 lines | Documented/partially documented | Grapple-breakup animation installer that applies the selected recovery animation with apron/location playback mode and advances the subtype. |
| 59 | `func3_800F5C34` | 11858 | 67 lines | Documented/partially documented | Downed/on-ground action state machine: initializes wake-up timers and lying animations, manages recoverability flags, handles get-up/top-rope/dizzy reactions, and battle-royal outside-loss cases. |
| 60 | `func3_800F5CF4` | 11925 | 376 lines | Documented/partially documented | Downed-state setup continuation that checks recovery eligibility, toggles recoverability flags, and advances into lying-animation/recovery subtypes. |
| 61 | `func3_800F60D8` | 12301 | 178 lines | Documented/partially documented | Standing/apron dizzy action: applies movement damping, installs dizzy/slumped animations, waits for recovery gates, then plays undizzy animations or returns control. |
| 62 | `func3_800F62B4` | 12479 | 79 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 63 | `func3_800F6384` | 12558 | 434 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 64 | `func3_800F6850` | 12992 | 128 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 65 | `func3_800F69AC` | 13120 | 196 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 66 | `func3_800F6BF4` | 13316 | 196 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 67 | `func3_800F6E48` | 13512 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 68 | `func3_800F6EE4` | 13571 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 69 | `func3_800F6F8C` | 13634 | 61 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 70 | `func3_800F7030` | 13695 | 53 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 71 | `func3_800F70C0` | 13748 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 72 | `func3_800F711C` | 13778 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 73 | `func3_800F715C` | 13808 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 74 | `func3_800F71E4` | 13859 | 457 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 75 | `func3_800F76E4` | 14316 | 298 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 76 | `func3_800F7A0C` | 14614 | 957 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 77 | `func3_800F8410` | 15571 | 33 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 78 | `func3_800F8458` | 15604 | 96 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 79 | `func3_800F8560` | 15700 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 80 | `func3_800F863C` | 15785 | 119 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 81 | `func3_800F878C` | 15904 | 104 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 82 | `func3_800F88BC` | 16008 | 123 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 83 | `func3_800F8A20` | 16131 | 183 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 84 | `func3_800F8C44` | 16314 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 85 | `func3_800F8E18` | 16489 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 86 | `func3_800F8EE0` | 16570 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 87 | `func3_800F8F34` | 16600 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 88 | `func3_800F8F88` | 16630 | 36 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 89 | `func3_800F8FF0` | 16666 | 40 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 90 | `func3_800F9074` | 16706 | 16 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 91 | `func3_800F9090` | 16722 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 92 | `func3_800F90F0` | 16756 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 93 | `func3_800F9138` | 16784 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 94 | `func3_800F9260` | 16868 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 95 | `func3_800F92F8` | 16926 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 96 | `func3_800F9320` | 16950 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 97 | `func3_800F937C` | 16989 | 95 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 98 | `func3_800F9494` | 17084 | 60 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 99 | `func3_800F9538` | 17144 | 16 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 100 | `func3_800F955C` | 17160 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 101 | `func3_800F9598` | 17184 | 68 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 102 | `func3_800F964C` | 17252 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 103 | `func3_800F96D0` | 17304 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 104 | `func3_800F98C4` | 17465 | 300 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 105 | `func3_800F9C74` | 17765 | 21 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 106 | `func3_800F9CA4` | 17786 | 83 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 107 | `func3_800F9D88` | 17869 | 25 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 108 | `func3_800F9DC0` | 17894 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 109 | `func3_800F9E7C` | 17957 | 173 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 110 | `func3_800FA04C` | 18130 | 73 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 111 | `func3_800FA104` | 18203 | 110 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 112 | `func3_800FA230` | 18313 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 113 | `func3_800FA2D8` | 18372 | 15 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 114 | `func3_800FA2FC` | 18387 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 115 | `func3_800FA338` | 18409 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 116 | `func3_800FA3BC` | 18465 | 383 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 117 | `func3_800FA8B8` | 18848 | 731 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 118 | `func3_800FB160` | 19579 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 119 | `func3_800FB1F4` | 19636 | 146 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 120 | `func3_800FB3D4` | 19782 | 223 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 121 | `func3_800FB68C` | 20005 | 94 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 122 | `func3_800FB76C` | 20099 | 76 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 123 | `func3_800FB838` | 20175 | 40 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 124 | `func3_800FB8A8` | 20215 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 125 | `func3_800FB90C` | 20258 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 126 | `func3_800FB940` | 20284 | 315 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 127 | `func3_800FBC98` | 20599 | 215 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 128 | `func3_800FBEF8` | 20814 | 68 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 129 | `func3_800FBFA0` | 20882 | 181 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 130 | `func3_800FC1D4` | 21063 | 763 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 131 | `func3_800FCB24` | 21826 | 55 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 132 | `func3_800FCBC4` | 21881 | 36 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 133 | `func3_800FCC2C` | 21917 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 134 | `func3_800FCC98` | 21960 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 135 | `func3_800FCD10` | 22007 | 580 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 136 | `func3_800FD3DC` | 22587 | 636 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 137 | `func3_800FDB50` | 23223 | 602 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 138 | `func3_800FE1DC` | 23825 | 190 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 139 | `func3_800FE418` | 24015 | 295 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 140 | `func3_800FE798` | 24310 | 61 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 141 | `func3_800FE854` | 24371 | 147 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 142 | `func3_800FE9E4` | 24518 | 64 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 143 | `func3_800FEAA0` | 24582 | 204 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 144 | `func3_800FED0C` | 24786 | 394 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 145 | `func3_800FF168` | 25180 | 340 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 146 | `func3_800FF554` | 25520 | 121 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 147 | `func3_800FF69C` | 25641 | 83 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 148 | `func3_800FF780` | 25724 | 9 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 149 | `func3_800FF798` | 25733 | 188 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 150 | `func3_800FF9B4` | 25921 | 142 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 151 | `func3_800FFB54` | 26063 | 405 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 152 | `func3_800FFFD8` | 26468 | 108 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block B

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 153 | `func3_801000FC` | 26576 | 155 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 154 | `func3_801002DC` | 26731 | 221 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 155 | `func3_8010057C` | 26952 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 156 | `func3_801005E4` | 26986 | 505 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 157 | `func3_80100BD0` | 27491 | 471 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 158 | `func3_80101110` | 27962 | 184 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 159 | `func3_80101334` | 28146 | 618 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 160 | `func3_80101A68` | 28764 | 194 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 161 | `func3_80101CAC` | 28958 | 550 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 162 | `func3_8010232C` | 29508 | 396 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 163 | `func3_801027F4` | 29904 | 132 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 164 | `func3_80102970` | 30036 | 372 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 165 | `func3_80102DCC` | 30408 | 383 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 166 | `func3_8010325C` | 30791 | 262 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 167 | `func3_8010355C` | 31053 | 49 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 168 | `func3_801035DC` | 31102 | 467 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 169 | `func3_80103B98` | 31569 | 270 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 170 | `func3_80103F04` | 31839 | 155 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 171 | `func3_801040D0` | 31994 | 46 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 172 | `func3_80104148` | 32040 | 122 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 173 | `func3_801042A4` | 32162 | 689 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 174 | `func3_80104A84` | 32851 | 62 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 175 | `func3_80104B3C` | 32913 | 289 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 176 | `func3_80104E74` | 33202 | 92 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 177 | `func3_80104F7C` | 33294 | 282 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 178 | `func3_801052C0` | 33576 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 179 | `func3_80105338` | 33623 | 139 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 180 | `func3_801054EC` | 33762 | 75 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 181 | `func3_801055CC` | 33837 | 283 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 182 | `func3_80105950` | 34120 | 176 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 183 | `func3_80105B5C` | 34296 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 184 | `func3_80105DD0` | 34494 | 318 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 185 | `func3_8010619C` | 34812 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 186 | `func3_80106284` | 34893 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 187 | `func3_8010638C` | 34982 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 188 | `func3_801064B0` | 35083 | 460 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 189 | `func3_80106A04` | 35543 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 190 | `func3_80106B9C` | 35670 | 152 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 191 | `func3_80106D68` | 35822 | 304 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 192 | `func3_80107148` | 36126 | 266 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 193 | `func3_80107498` | 36392 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 194 | `func3_801075B4` | 36477 | 170 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 195 | `func3_801077C4` | 36647 | 204 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 196 | `func3_801079EC` | 36851 | 238 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 197 | `func3_80107CC4` | 37089 | 66 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 198 | `func3_80107D70` | 37155 | 356 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 199 | `func3_80108118` | 37511 | 313 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 200 | `func3_80108478` | 37824 | 284 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 201 | `func3_801087D4` | 38108 | 102 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 202 | `func3_801088F8` | 38210 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 203 | `func3_80108AC0` | 38371 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 204 | `func3_80108CB0` | 38546 | 195 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 205 | `func3_80108EAC` | 38741 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 206 | `func3_80108EDC` | 38761 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 207 | `func3_80108FB4` | 38842 | 78 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 208 | `func3_80109084` | 38920 | 245 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 209 | `func3_80109354` | 39165 | 309 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 210 | `func3_801096C0` | 39474 | 390 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 211 | `func3_80109B08` | 39864 | 169 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 212 | `func3_80109CF0` | 40033 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 213 | `func3_80109E48` | 40160 | 187 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 214 | `func3_8010A034` | 40347 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 215 | `func3_8010A0DC` | 40405 | 208 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 216 | `func3_8010A2F0` | 40613 | 216 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 217 | `func3_8010A504` | 40829 | 40 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 218 | `func3_8010A560` | 40869 | 97 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 219 | `func3_8010A6A8` | 40966 | 90 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 220 | `func3_8010A7B0` | 41056 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 221 | `func3_8010A868` | 41121 | 209 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 222 | `func3_8010AA38` | 41330 | 146 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 223 | `func3_8010ABE4` | 41476 | 70 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 224 | `func3_8010D030` | 41546 | 370 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 225 | `func3_8010D374` | 41916 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 226 | `func3_8010D3BC` | 41940 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 227 | `func3_8010D460` | 41992 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 228 | `func3_8010D4B8` | 42023 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 229 | `func3_8010D590` | 42090 | 76 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 230 | `func3_8010D67C` | 42166 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 231 | `func3_8010D6B4` | 42186 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 232 | `func3_8010D714` | 42220 | 359 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 233 | `func3_8010DB94` | 42579 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 234 | `func3_8010DC20` | 42642 | 25 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 235 | `func3_8010DC6C` | 42667 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 236 | `func3_8010DDB8` | 42774 | 117 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 237 | `func3_8010DF38` | 42891 | 11 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 238 | `func3_8010DF54` | 42902 | 145 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 239 | `func3_8010E108` | 43047 | 316 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 240 | `func3_8010E4F0` | 43363 | 236 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 241 | `func3_8010E7A8` | 43599 | 775 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 242 | `func3_8010F0A8` | 44374 | 280 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 243 | `func3_8010F3CC` | 44654 | 256 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 244 | `func3_8010F68C` | 44910 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 245 | `func3_8010F740` | 44968 | 221 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 246 | `func3_8010F9D8` | 45189 | 181 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 247 | `func3_8010FBF8` | 45370 | 330 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 248 | `func3_8010FFE0` | 45700 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block C

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 249 | `func3_801100D8` | 45784 | 338 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 250 | `func3_801104E4` | 46122 | 695 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 251 | `func3_80110CF4` | 46817 | 367 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 252 | `func3_8011113C` | 47184 | 336 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 253 | `func3_801114F4` | 47520 | 222 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 254 | `func3_80111794` | 47742 | 100 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 255 | `func3_801118C4` | 47842 | 79 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 256 | `func3_801119A4` | 47921 | 151 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 257 | `func3_80111B74` | 48072 | 93 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 258 | `func3_80111C80` | 48165 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 259 | `func3_80111E88` | 48340 | 106 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 260 | `func3_80111FE0` | 48446 | 931 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 261 | `func3_80112AD8` | 49377 | 428 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 262 | `func3_80112FF0` | 49805 | 229 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 263 | `func3_80113284` | 50034 | 93 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 264 | `func3_80113380` | 50127 | 207 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 265 | `func3_8011361C` | 50334 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 266 | `func3_80113764` | 50435 | 220 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 267 | `func3_801139AC` | 50655 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 268 | `func3_80113A58` | 50718 | 82 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 269 | `func3_80113B5C` | 50800 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 270 | `func3_80113CA0` | 50912 | 160 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 271 | `func3_80113E78` | 51072 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 272 | `func3_80113EE8` | 51111 | 36 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 273 | `func3_80113F50` | 51147 | 341 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 274 | `func3_8011437C` | 51488 | 71 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 275 | `func3_8011444C` | 51559 | 135 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 276 | `func3_801145F8` | 51694 | 115 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 277 | `func3_80114758` | 51809 | 250 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 278 | `func3_80114A44` | 52059 | 138 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 279 | `func3_80114BF4` | 52197 | 182 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 280 | `func3_80114E30` | 52379 | 651 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 281 | `func3_801155DC` | 53030 | 231 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 282 | `func3_80115894` | 53261 | 493 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 283 | `func3_80115E6C` | 53754 | 457 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 284 | `func3_80116410` | 54211 | 41 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 285 | `func3_80116498` | 54252 | 178 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 286 | `func3_801166E8` | 54430 | 111 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 287 | `func3_8011683C` | 54541 | 250 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 288 | `func3_80116B5C` | 54791 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 289 | `func3_80116C50` | 54872 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 290 | `func3_80116CC4` | 54911 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 291 | `func3_80116DD0` | 54995 | 167 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 292 | `func3_80116FE0` | 55162 | 133 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 293 | `func3_8011718C` | 55295 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 294 | `func3_80117288` | 55380 | 304 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 295 | `func3_80117634` | 55684 | 49 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 296 | `func3_801176C0` | 55733 | 147 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 297 | `func3_8011789C` | 55880 | 146 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 298 | `func3_80117A6C` | 56026 | 258 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 299 | `func3_80117D84` | 56284 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 300 | `func3_80117E10` | 56331 | 203 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 301 | `func3_8011806C` | 56534 | 465 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 302 | `func3_801185F4` | 56999 | 86 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 303 | `func3_801186F4` | 57085 | 98 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 304 | `func3_80118824` | 57183 | 202 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 305 | `func3_80118A88` | 57385 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 306 | `func3_80118BC8` | 57486 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 307 | `func3_80118D60` | 57620 | 196 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 308 | `func3_80118FC8` | 57816 | 96 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 309 | `func3_801190F4` | 57912 | 316 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 310 | `func3_80119480` | 58228 | 197 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 311 | `func3_801196D0` | 58425 | 482 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 312 | `func3_80119C78` | 58907 | 416 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 313 | `func3_8011A170` | 59323 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 314 | `func3_8011A23C` | 59395 | 426 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 315 | `func3_8011A758` | 59821 | 230 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 316 | `func3_8011AA28` | 60051 | 151 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 317 | `func3_8011ABE4` | 60202 | 73 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 318 | `func3_8011ACB8` | 60275 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 319 | `func3_8011AD50` | 60322 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 320 | `func3_8011ADCC` | 60359 | 172 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 321 | `func3_8011AFBC` | 60531 | 246 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 322 | `func3_8011B278` | 60777 | 437 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 323 | `func3_8011B79C` | 61214 | 394 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 324 | `func3_8011BC18` | 61608 | 156 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 325 | `func3_8011BE14` | 61764 | 342 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 326 | `func3_8011C1F8` | 62106 | 102 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 327 | `func3_8011C324` | 62208 | 275 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 328 | `func3_8011C64C` | 62483 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 329 | `func3_8011C824` | 62644 | 122 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 330 | `func3_8011C9A4` | 62766 | 320 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 331 | `func3_8011CD84` | 63086 | 239 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 332 | `func3_8011D064` | 63325 | 109 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 333 | `func3_8011D1B8` | 63434 | 91 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 334 | `func3_8011D2D0` | 63525 | 169 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 335 | `func3_8011D4E4` | 63694 | 420 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 336 | `func3_8011D9B0` | 64114 | 164 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 337 | `func3_8011DBB0` | 64278 | 193 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 338 | `func3_8011DDF4` | 64471 | 192 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 339 | `func3_8011E044` | 64663 | 305 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 340 | `func3_8011E3D8` | 64968 | 129 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 341 | `func3_8011E540` | 65097 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 342 | `func3_8011E6DC` | 65240 | 83 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 343 | `func3_8011E7E4` | 65323 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 344 | `func3_8011E864` | 65360 | 117 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 345 | `func3_8011E9A8` | 65477 | 176 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 346 | `func3_8011EBA4` | 65653 | 272 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 347 | `func3_8011EEE4` | 65925 | 407 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 348 | `func3_8011F3F8` | 66332 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 349 | `func3_8011F4A0` | 66388 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 350 | `func3_8011F538` | 66438 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 351 | `func3_8011F78C` | 66636 | 309 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 352 | `func3_8011FB20` | 66945 | 121 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 353 | `func3_8011FC98` | 67066 | 202 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 354 | `func3_8011FEDC` | 67268 | 421 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block D

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 355 | `func3_801203C4` | 67689 | 341 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 356 | `func3_801207D8` | 68030 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 357 | `func3_80120848` | 68067 | 190 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 358 | `func3_80120A88` | 68257 | 138 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 359 | `func3_80120C38` | 68395 | 345 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 360 | `func3_80121070` | 68740 | 443 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 361 | `func3_801214E0` | 69183 | 193 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 362 | `func3_801216FC` | 69376 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 363 | `func3_80121764` | 69419 | 226 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 364 | `func3_80121A04` | 69645 | 201 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 365 | `func3_80121C50` | 69846 | 604 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 366 | `func3_80122328` | 70450 | 404 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 367 | `func3_80122800` | 70854 | 211 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 368 | `func3_80122A48` | 71065 | 158 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 369 | `func3_80122C50` | 71223 | 318 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 370 | `func3_80123004` | 71541 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 371 | `func3_80123174` | 71675 | 506 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 372 | `func3_80123744` | 72181 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 373 | `func3_801238A8` | 72297 | 70 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 374 | `func3_8012396C` | 72367 | 784 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 375 | `func3_801242A4` | 73151 | 714 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 376 | `func3_80124AA8` | 73865 | 303 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 377 | `func3_80124E2C` | 74168 | 87 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 378 | `func3_80124F14` | 74255 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 379 | `func3_80124F54` | 74283 | 201 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 380 | `func3_80125160` | 74484 | 215 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 381 | `func3_80125404` | 74699 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 382 | `func3_80125510` | 74800 | 29 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 383 | `func3_80125568` | 74829 | 136 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 384 | `func3_801256C4` | 74965 | 357 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 385 | `func3_80125B08` | 75322 | 461 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 386 | `func3_80126050` | 75783 | 1049 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 387 | `func3_80126C90` | 76832 | 338 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 388 | `func3_8012705C` | 77170 | 482 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 389 | `func3_801275C0` | 77652 | 273 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 390 | `func3_801278FC` | 77925 | 137 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 391 | `func3_80127AA0` | 78062 | 860 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 392 | `func3_801284C8` | 78922 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 393 | `func3_80128580` | 78989 | 76 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 394 | `func3_80128660` | 79065 | 38 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 395 | `func3_801286C0` | 79103 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 396 | `func3_80128708` | 79130 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 397 | `func3_8012875C` | 79158 | 253 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 398 | `func3_80128A8C` | 79411 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 399 | `func3_80128AD8` | 79435 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 400 | `func3_80128CD4` | 79610 | 280 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 401 | `func3_8012901C` | 79890 | 347 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 402 | `func3_80129428` | 80237 | 144 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 403 | `func3_801295E0` | 80381 | 579 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 404 | `func3_80129C74` | 80960 | 237 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 405 | `func3_80129F5C` | 81197 | 744 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 406 | `func3_8012A86C` | 81941 | 320 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 407 | `func3_8012AC30` | 82261 | 478 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 408 | `func3_8012B1F8` | 82739 | 564 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 409 | `func3_8012B8C8` | 83303 | 586 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 410 | `func3_8012C008` | 83889 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 411 | `func3_8012C1CC` | 84032 | 5 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 412 | `func3_8012C1D4` | 84037 | 131 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 413 | `func3_8012C36C` | 84168 | 364 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 414 | `func3_8012C75C` | 84532 | 180 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 415 | `func3_8012C9AC` | 84712 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 416 | `func3_8012CB50` | 84855 | 78 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 417 | `func3_8012CC2C` | 84933 | 308 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 418 | `func3_8012D024` | 85241 | 91 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 419 | `func3_8012D118` | 85332 | 241 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 420 | `func3_8012D3B4` | 85573 | 567 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 421 | `func3_8012D9E0` | 86140 | 1358 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 422 | `func3_8012E9C0` | 87498 | 1105 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 423 | `func3_8012F734` | 88603 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 424 | `func3_8012F7C4` | 88650 | 155 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 425 | `func3_8012F980` | 88805 | 589 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block E

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 426 | `func3_8013000C` | 89394 | 209 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 427 | `func3_8013026C` | 89603 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 428 | `func3_80130488` | 89801 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 429 | `func3_801305B4` | 89917 | 61 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 430 | `func3_80130650` | 89978 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 431 | `func3_8013067C` | 90006 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 432 | `func3_801306C0` | 90033 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay/system block F

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 433 | `func3_GetPlayerHealth` | 90072 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block E

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 434 | `func3_80130730` | 90094 | 149 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 435 | `func3_801308E0` | 90243 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 436 | `func3_80130968` | 90300 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 437 | `func3_801309F4` | 90356 | 235 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 438 | `func3_80130C68` | 90591 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 439 | `func3_80130D00` | 90648 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 440 | `func3_80130D34` | 90670 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 441 | `func3_80130D70` | 90692 | 125 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 442 | `func3_80130EC8` | 90817 | 110 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 443 | `func3_8013100C` | 90927 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 444 | `func3_80131048` | 90957 | 698 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 445 | `func3_80131840` | 91655 | 527 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 446 | `func3_80131E54` | 92182 | 500 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 447 | `func3_80132428` | 92682 | 325 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 448 | `func3_801327C0` | 93007 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 449 | `func3_801328AC` | 93091 | 74 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 450 | `func3_8013297C` | 93165 | 108 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 451 | `func3_80132AA0` | 93273 | 324 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 452 | `func3_80132E2C` | 93597 | 413 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 453 | `func3_801332F0` | 94010 | 70 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 454 | `func3_801333C4` | 94080 | 374 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 455 | `func3_80133834` | 94454 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 456 | `func3_8013397C` | 94570 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 457 | `func3_80133A34` | 94633 | 25 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 458 | `func3_80133A6C` | 94658 | 148 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 459 | `func3_80133C00` | 94806 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 460 | `func3_80133D2C` | 94895 | 881 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 461 | `func3_80134850` | 95776 | 233 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 462 | `func3_80134AA0` | 96009 | 95 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 463 | `func3_80134BB0` | 96104 | 863 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 464 | `func3_80135504` | 96967 | 400 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 465 | `func3_8013591C` | 97367 | 108 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 466 | `func3_80135A34` | 97475 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 467 | `func3_80135B60` | 97582 | 253 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 468 | `func3_80135E28` | 97835 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 469 | `func3_80135E90` | 97878 | 86 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 470 | `func3_80135F70` | 97964 | 163 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 471 | `func3_8013614C` | 98127 | 1166 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 472 | `func3_80136E8C` | 99293 | 643 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 473 | `func3_801375E4` | 99936 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 474 | `func3_80137710` | 100048 | 415 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 475 | `func3_80137BD8` | 100463 | 179 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 476 | `func3_80137DD4` | 100642 | 128 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 477 | `func3_80137F50` | 100770 | 533 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 478 | `func3_80138504` | 101303 | 478 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 479 | `func3_801391B0` | 101781 | 166 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 480 | `func3_80139380` | 101947 | 94 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 481 | `func3_8013949C` | 102041 | 97 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 482 | `func3_801395BC` | 102138 | 389 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 483 | `func3_80139AD4` | 102527 | 593 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 484 | `func3_8013A198` | 103120 | 341 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 485 | `func3_8013A584` | 103461 | 92 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 486 | `func3_8013A690` | 103553 | 981 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 487 | `func3_8013B238` | 104534 | 249 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 488 | `func3_8013B4F4` | 104783 | 181 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 489 | `func3_8013B6FC` | 104964 | 66 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 490 | `func3_8013B7BC` | 105030 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 491 | `func3_8013B7F0` | 105056 | 360 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 492 | `func3_8013BBFC` | 105416 | 44 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 493 | `func3_8013BC68` | 105460 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 494 | `func3_8013BD88` | 105567 | 528 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 495 | `func3_8013C360` | 106095 | 99 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 496 | `func3_8013C46C` | 106194 | 71 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 497 | `func3_8013C528` | 106265 | 303 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 498 | `func3_8013C888` | 106568 | 200 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 499 | `func3_8013CA9C` | 106768 | 486 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 500 | `func3_8013D09C` | 107254 | 275 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 501 | `func3_8013D3C4` | 107529 | 261 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 502 | `func3_8013D6B4` | 107790 | 247 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 503 | `func3_8013D954` | 108037 | 130 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 504 | `func3_8013DAC4` | 108167 | 106 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 505 | `func3_8013DBE8` | 108273 | 147 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 506 | `func3_8013DDAC` | 108420 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 507 | `func3_8013DE6C` | 108485 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 508 | `func3_8013DFE0` | 108619 | 190 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 509 | `func3_8013E200` | 108809 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 510 | `func3_8013E35C` | 108936 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 511 | `func3_8013E40C` | 108995 | 19 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 512 | `func3_8013E434` | 109014 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 513 | `func3_8013E460` | 109034 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 514 | `func3_8013E490` | 109056 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 515 | `func3_8013E4C0` | 109076 | 17 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 516 | `func3_8013E4E8` | 109093 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 517 | `func3_8013E56C` | 109144 | 87 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 518 | `func3_8013E660` | 109231 | 118 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 519 | `func3_8013E7AC` | 109349 | 236 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 520 | `func3_8013EA60` | 109585 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 521 | `func3_8013EAF8` | 109635 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 522 | `func3_8013EB40` | 109657 | 18 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 523 | `func3_8013EB78` | 109675 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 524 | `func3_8013EBB4` | 109697 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 525 | `func3_8013EBF4` | 109717 | 19 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 526 | `func3_8013EC30` | 109736 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 527 | `func3_8013EC74` | 109763 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 528 | `func3_8013EDB4` | 109870 | 589 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 529 | `func3_8013F4A0` | 110459 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 530 | `func3_8013F4B4` | 110469 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 531 | `func3_8013F500` | 110506 | 18 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 532 | `func3_8013F524` | 110524 | 21 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 533 | `func3_8013F564` | 110545 | 14 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 534 | `func3_8013F580` | 110559 | 14 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 535 | `func3_8013F598` | 110573 | 11 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 536 | `func3_8013F5B0` | 110584 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 537 | `func3_8013F5E4` | 110608 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 538 | `func3_8013F67C` | 110667 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 539 | `func3_8013F6AC` | 110694 | 16 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 540 | `func3_8013F6E0` | 110710 | 75 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 541 | `func3_8013F7B8` | 110785 | 41 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 542 | `func3_8013F830` | 110826 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 543 | `func3_8013F880` | 110857 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 544 | `func3_8013F930` | 110913 | 99 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 545 | `func3_8013FA64` | 111012 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 546 | `func3_8013FB14` | 111070 | 137 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 547 | `func3_8013FCBC` | 111207 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 548 | `func3_8013FE30` | 111341 | 62 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 549 | `func3_8013FEF0` | 111403 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay/system block F

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 550 | `func3_801400F8` | 111564 | 502 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 551 | `func3_80140808` | 112066 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 552 | `func3_8014088C` | 112116 | 29 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 553 | `func3_801408D8` | 112145 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 554 | `func3_80140944` | 112184 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 555 | `func3_801409B0` | 112223 | 194 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 556 | `func3_80140BB4` | 112417 | 13 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 557 | `func3_80140BC0` | 112430 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 558 | `func3_80140CF8` | 112542 | 12 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 559 | `func3_80140D18` | 112554 | 148 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 560 | `func3_80140ED8` | 112702 | 270 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 561 | `func3_80141248` | 112972 | 73 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 562 | `func3_8014133C` | 113045 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 563 | `func3_80141384` | 113072 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 564 | `func3_801413FC` | 113122 | 62 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 565 | `func3_80141490` | 113184 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 566 | `func3_801414A0` | 113194 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 567 | `func3_80141514` | 113245 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 568 | `func3_8014158C` | 113292 | 105 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 569 | `func3_801416A0` | 113397 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 570 | `func3_8014173C` | 113455 | 284 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 571 | `func3_80141A5C` | 113739 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 572 | `func3_80141AD0` | 113791 | 162 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 573 | `func3_80141C90` | 113953 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 574 | `func3_80141E0C` | 114096 | 11 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 575 | `func3_80141E2C` | 114107 | 8 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 576 | `func3_80141E40` | 114115 | 401 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 577 | `func3_80142340` | 114516 | 235 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 578 | `func3_8014261C` | 114751 | 410 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 579 | `func3_80142BA0` | 115161 | 17 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 580 | `func3_80142BCC` | 115178 | 12 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 581 | `func3_80142BE0` | 115190 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 582 | `func3_80142C74` | 115241 | 69 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 583 | `func3_80142D40` | 115310 | 153 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 584 | `func3_80142EE0` | 115463 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 585 | `func3_80142F20` | 115489 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 586 | `func3_80142F64` | 115516 | 696 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 587 | `func3_801437E0` | 116212 | 229 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 588 | `func3_80143B00` | 116441 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 589 | `func3_80143D30` | 116639 | 115 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 590 | `func3_80143E38` | 116754 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 591 | `func3_80143EB0` | 116793 | 17 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 592 | `func3_80143ED8` | 116810 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 593 | `func3_80144020` | 116937 | 183 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 594 | `func3_80144214` | 117120 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 595 | `func3_8014426C` | 117154 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 596 | `func3_80144304` | 117212 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 597 | `func3_80144340` | 117238 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 598 | `func3_801443C8` | 117301 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 599 | `func3_80144414` | 117340 | 275 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 600 | `func3_80144710` | 117615 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 601 | `func3_801447F4` | 117704 | 201 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 602 | `func3_80144A10` | 117905 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 603 | `func3_80144AB0` | 117970 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 604 | `func3_80144B60` | 118037 | 426 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 605 | `func3_80145098` | 118463 | 698 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 606 | `func3_80145840` | 119161 | 1671 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 607 | `func3_80146C28` | 120832 | 53 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 608 | `func3_80146CB0` | 120885 | 628 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 609 | `func3_80147414` | 121513 | 246 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 610 | `func3_801476EC` | 121759 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 611 | `func3_801477A8` | 121831 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 612 | `func3_80147830` | 121883 | 274 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 613 | `func3_80147B20` | 122157 | 715 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 614 | `func3_80148360` | 122872 | 226 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 615 | `func3_80148610` | 123098 | 75 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 616 | `func3_801486E0` | 123173 | 88 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 617 | `func3_801487D8` | 123261 | 38 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 618 | `func3_80148838` | 123299 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 619 | `func3_80148884` | 123330 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 620 | `func3_801489AC` | 123446 | 86 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 621 | `func3_80148A94` | 123532 | 104 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 622 | `func3_80148BD4` | 123636 | 165 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 623 | `func3_80148DB8` | 123801 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 624 | `func3_80148E00` | 123832 | 446 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 625 | `func3_801492D0` | 124278 | 123 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 626 | `func3_80149450` | 124401 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 627 | `func3_8014951C` | 124473 | 46 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 628 | `func3_80149590` | 124519 | 88 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 629 | `func3_8014967C` | 124607 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 630 | `func3_80149770` | 124692 | 32 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 631 | `func3_801497C0` | 124724 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 632 | `func3_801497D0` | 124734 | 77 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 633 | `func3_80149894` | 124811 | 725 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 634 | `func3_8014A0B0` | 125536 | 267 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 635 | `func3_8014A3DC` | 125803 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 636 | `func3_8014A600` | 126001 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 637 | `func3_8014A740` | 126113 | 242 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 638 | `func3_8014A9FC` | 126355 | 861 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 639 | `func3_8014B37C` | 127216 | 721 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 640 | `func3_8014BB98` | 127937 | 412 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 641 | `func3_8014C050` | 128349 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 642 | `func3_8014C1B4` | 128483 | 316 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 643 | `func3_8014C54C` | 128799 | 873 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 644 | `func3_8014CFC0` | 129672 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 645 | `func3_8014D03C` | 129723 | 895 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 646 | `func3_8014DC30` | 130618 | 284 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 647 | `func3_8014DF78` | 130902 | 136 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 648 | `func3_8014E100` | 131038 | 64 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 649 | `func3_8014E198` | 131102 | 269 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 650 | `func3_8014E4A0` | 131371 | 74 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 651 | `func3_8014E570` | 131445 | 119 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 652 | `func3_8014E6C8` | 131564 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 653 | `func3_8014E784` | 131631 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 654 | `func3_8014E81C` | 131688 | 104 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 655 | `func3_8014E948` | 131792 | 129 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 656 | `func3_8014EABC` | 131921 | 220 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 657 | `func3_8014ED54` | 132141 | 149 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 658 | `func3_8014EF0C` | 132290 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 659 | `func3_8014EFE4` | 132362 | 80 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 660 | `func3_8014F0B8` | 132442 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 661 | `func3_8014F1F0` | 132549 | 153 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 662 | `func3_8014F3AC` | 132702 | 266 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 663 | `func3_8014F6C8` | 132968 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 664 | `func3_8014F820` | 133084 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 665 | `func3_8014F8AC` | 133135 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 666 | `func3_8014F8E4` | 133163 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 667 | `func3_8014F914` | 133189 | 74 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 668 | `func3_8014F9D8` | 133263 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 669 | `func3_8014FAD4` | 133352 | 260 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 670 | `func3_8014FDB0` | 133612 | 266 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 671 | `func3_80150084` | 133878 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 672 | `func3_80150130` | 133943 | 100 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 673 | `func3_80150230` | 134043 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 674 | `func3_80150238` | 134053 | 128 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 675 | `func3_801503B4` | 134181 | 154 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 676 | `func3_80150580` | 134335 | 33 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 677 | `func3_801505D8` | 134368 | 114 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 678 | `func3_80150738` | 134482 | 217 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 679 | `func3_801509CC` | 134699 | 119 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 680 | `func3_80150B6C` | 134818 | 66 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 681 | `func3_80150C28` | 134884 | 79 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 682 | `func3_80150D3C` | 134963 | 23 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 683 | `func3_80150D7C` | 134986 | 152 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 684 | `func3_80150F8C` | 135138 | 152 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 685 | `func3_80151148` | 135290 | 135 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 686 | `func3_80151308` | 135425 | 29 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 687 | `func3_8015134C` | 135454 | 184 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 688 | `func3_80151554` | 135638 | 12123 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
