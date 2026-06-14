# seg0003 function overview

This document is a standalone working inventory for `asm/seg003_code.s`. It is intentionally broad rather than final: each row lists a discovered `func3_*` entry point, its source line, approximate assembly span, current documentation status, and the best current note. Rows marked **TBD** have not yet received a dedicated reverse-engineering/comment pass.

## Progress snapshot

- Total `func3_*` entry points found: **688**.
- Functions with dedicated notes so far: **41**.
- Remaining functions needing detailed notes: **647**.
- Source of truth for line numbers: `asm/seg003_code.s`.

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
| 42 | `func3_800F1080` | 5426 | 76 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 43 | `func3_800F1190` | 5502 | 23 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 44 | `func3_800F11A4` | 5525 | 21 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 45 | `func3_800F11EC` | 5546 | 1681 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 46 | `func3_800F270C` | 7227 | 857 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 47 | `func3_800F323C` | 8084 | 421 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 48 | `func3_800F37A4` | 8505 | 88 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 49 | `func3_800F38D4` | 8593 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 50 | `func3_800F3978` | 8649 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 51 | `func3_800F3A00` | 8700 | 359 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 52 | `func3_800F3E88` | 9059 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 53 | `func3_800F3F64` | 9144 | 233 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 54 | `func3_800F4210` | 9377 | 104 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 55 | `func3_800F4338` | 9481 | 1166 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 56 | `func3_800F5000` | 10647 | 870 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 57 | `func3_800F5990` | 11517 | 136 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 58 | `func3_800F5AE8` | 11653 | 141 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 59 | `func3_800F5C34` | 11794 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 60 | `func3_800F5CF4` | 11857 | 373 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 61 | `func3_800F60D8` | 12230 | 174 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 62 | `func3_800F62B4` | 12404 | 79 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 63 | `func3_800F6384` | 12483 | 434 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 64 | `func3_800F6850` | 12917 | 128 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 65 | `func3_800F69AC` | 13045 | 196 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 66 | `func3_800F6BF4` | 13241 | 196 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 67 | `func3_800F6E48` | 13437 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 68 | `func3_800F6EE4` | 13496 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 69 | `func3_800F6F8C` | 13559 | 61 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 70 | `func3_800F7030` | 13620 | 53 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 71 | `func3_800F70C0` | 13673 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 72 | `func3_800F711C` | 13703 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 73 | `func3_800F715C` | 13733 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 74 | `func3_800F71E4` | 13784 | 457 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 75 | `func3_800F76E4` | 14241 | 298 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 76 | `func3_800F7A0C` | 14539 | 957 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 77 | `func3_800F8410` | 15496 | 33 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 78 | `func3_800F8458` | 15529 | 96 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 79 | `func3_800F8560` | 15625 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 80 | `func3_800F863C` | 15710 | 119 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 81 | `func3_800F878C` | 15829 | 104 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 82 | `func3_800F88BC` | 15933 | 123 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 83 | `func3_800F8A20` | 16056 | 183 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 84 | `func3_800F8C44` | 16239 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 85 | `func3_800F8E18` | 16414 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 86 | `func3_800F8EE0` | 16495 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 87 | `func3_800F8F34` | 16525 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 88 | `func3_800F8F88` | 16555 | 36 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 89 | `func3_800F8FF0` | 16591 | 40 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 90 | `func3_800F9074` | 16631 | 16 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 91 | `func3_800F9090` | 16647 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 92 | `func3_800F90F0` | 16681 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 93 | `func3_800F9138` | 16709 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 94 | `func3_800F9260` | 16793 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 95 | `func3_800F92F8` | 16851 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 96 | `func3_800F9320` | 16875 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 97 | `func3_800F937C` | 16914 | 95 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 98 | `func3_800F9494` | 17009 | 60 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 99 | `func3_800F9538` | 17069 | 16 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 100 | `func3_800F955C` | 17085 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 101 | `func3_800F9598` | 17109 | 68 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 102 | `func3_800F964C` | 17177 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 103 | `func3_800F96D0` | 17229 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 104 | `func3_800F98C4` | 17390 | 300 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 105 | `func3_800F9C74` | 17690 | 21 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 106 | `func3_800F9CA4` | 17711 | 83 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 107 | `func3_800F9D88` | 17794 | 25 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 108 | `func3_800F9DC0` | 17819 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 109 | `func3_800F9E7C` | 17882 | 173 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 110 | `func3_800FA04C` | 18055 | 73 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 111 | `func3_800FA104` | 18128 | 110 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 112 | `func3_800FA230` | 18238 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 113 | `func3_800FA2D8` | 18297 | 15 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 114 | `func3_800FA2FC` | 18312 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 115 | `func3_800FA338` | 18334 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 116 | `func3_800FA3BC` | 18390 | 383 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 117 | `func3_800FA8B8` | 18773 | 731 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 118 | `func3_800FB160` | 19504 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 119 | `func3_800FB1F4` | 19561 | 146 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 120 | `func3_800FB3D4` | 19707 | 223 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 121 | `func3_800FB68C` | 19930 | 94 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 122 | `func3_800FB76C` | 20024 | 76 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 123 | `func3_800FB838` | 20100 | 40 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 124 | `func3_800FB8A8` | 20140 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 125 | `func3_800FB90C` | 20183 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 126 | `func3_800FB940` | 20209 | 315 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 127 | `func3_800FBC98` | 20524 | 215 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 128 | `func3_800FBEF8` | 20739 | 68 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 129 | `func3_800FBFA0` | 20807 | 181 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 130 | `func3_800FC1D4` | 20988 | 763 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 131 | `func3_800FCB24` | 21751 | 55 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 132 | `func3_800FCBC4` | 21806 | 36 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 133 | `func3_800FCC2C` | 21842 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 134 | `func3_800FCC98` | 21885 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 135 | `func3_800FCD10` | 21932 | 580 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 136 | `func3_800FD3DC` | 22512 | 636 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 137 | `func3_800FDB50` | 23148 | 602 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 138 | `func3_800FE1DC` | 23750 | 190 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 139 | `func3_800FE418` | 23940 | 295 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 140 | `func3_800FE798` | 24235 | 61 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 141 | `func3_800FE854` | 24296 | 147 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 142 | `func3_800FE9E4` | 24443 | 64 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 143 | `func3_800FEAA0` | 24507 | 204 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 144 | `func3_800FED0C` | 24711 | 394 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 145 | `func3_800FF168` | 25105 | 340 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 146 | `func3_800FF554` | 25445 | 121 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 147 | `func3_800FF69C` | 25566 | 83 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 148 | `func3_800FF780` | 25649 | 9 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 149 | `func3_800FF798` | 25658 | 188 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 150 | `func3_800FF9B4` | 25846 | 142 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 151 | `func3_800FFB54` | 25988 | 405 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 152 | `func3_800FFFD8` | 26393 | 108 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block B

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 153 | `func3_801000FC` | 26501 | 155 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 154 | `func3_801002DC` | 26656 | 221 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 155 | `func3_8010057C` | 26877 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 156 | `func3_801005E4` | 26911 | 505 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 157 | `func3_80100BD0` | 27416 | 471 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 158 | `func3_80101110` | 27887 | 184 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 159 | `func3_80101334` | 28071 | 618 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 160 | `func3_80101A68` | 28689 | 194 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 161 | `func3_80101CAC` | 28883 | 550 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 162 | `func3_8010232C` | 29433 | 396 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 163 | `func3_801027F4` | 29829 | 132 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 164 | `func3_80102970` | 29961 | 372 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 165 | `func3_80102DCC` | 30333 | 383 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 166 | `func3_8010325C` | 30716 | 262 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 167 | `func3_8010355C` | 30978 | 49 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 168 | `func3_801035DC` | 31027 | 467 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 169 | `func3_80103B98` | 31494 | 270 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 170 | `func3_80103F04` | 31764 | 155 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 171 | `func3_801040D0` | 31919 | 46 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 172 | `func3_80104148` | 31965 | 122 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 173 | `func3_801042A4` | 32087 | 689 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 174 | `func3_80104A84` | 32776 | 62 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 175 | `func3_80104B3C` | 32838 | 289 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 176 | `func3_80104E74` | 33127 | 92 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 177 | `func3_80104F7C` | 33219 | 282 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 178 | `func3_801052C0` | 33501 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 179 | `func3_80105338` | 33548 | 139 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 180 | `func3_801054EC` | 33687 | 75 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 181 | `func3_801055CC` | 33762 | 283 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 182 | `func3_80105950` | 34045 | 176 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 183 | `func3_80105B5C` | 34221 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 184 | `func3_80105DD0` | 34419 | 318 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 185 | `func3_8010619C` | 34737 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 186 | `func3_80106284` | 34818 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 187 | `func3_8010638C` | 34907 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 188 | `func3_801064B0` | 35008 | 460 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 189 | `func3_80106A04` | 35468 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 190 | `func3_80106B9C` | 35595 | 152 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 191 | `func3_80106D68` | 35747 | 304 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 192 | `func3_80107148` | 36051 | 266 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 193 | `func3_80107498` | 36317 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 194 | `func3_801075B4` | 36402 | 170 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 195 | `func3_801077C4` | 36572 | 204 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 196 | `func3_801079EC` | 36776 | 238 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 197 | `func3_80107CC4` | 37014 | 66 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 198 | `func3_80107D70` | 37080 | 356 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 199 | `func3_80108118` | 37436 | 313 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 200 | `func3_80108478` | 37749 | 284 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 201 | `func3_801087D4` | 38033 | 102 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 202 | `func3_801088F8` | 38135 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 203 | `func3_80108AC0` | 38296 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 204 | `func3_80108CB0` | 38471 | 195 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 205 | `func3_80108EAC` | 38666 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 206 | `func3_80108EDC` | 38686 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 207 | `func3_80108FB4` | 38767 | 78 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 208 | `func3_80109084` | 38845 | 245 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 209 | `func3_80109354` | 39090 | 309 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 210 | `func3_801096C0` | 39399 | 390 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 211 | `func3_80109B08` | 39789 | 169 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 212 | `func3_80109CF0` | 39958 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 213 | `func3_80109E48` | 40085 | 187 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 214 | `func3_8010A034` | 40272 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 215 | `func3_8010A0DC` | 40330 | 208 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 216 | `func3_8010A2F0` | 40538 | 216 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 217 | `func3_8010A504` | 40754 | 40 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 218 | `func3_8010A560` | 40794 | 97 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 219 | `func3_8010A6A8` | 40891 | 90 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 220 | `func3_8010A7B0` | 40981 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 221 | `func3_8010A868` | 41046 | 209 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 222 | `func3_8010AA38` | 41255 | 146 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 223 | `func3_8010ABE4` | 41401 | 70 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 224 | `func3_8010D030` | 41471 | 370 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 225 | `func3_8010D374` | 41841 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 226 | `func3_8010D3BC` | 41865 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 227 | `func3_8010D460` | 41917 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 228 | `func3_8010D4B8` | 41948 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 229 | `func3_8010D590` | 42015 | 76 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 230 | `func3_8010D67C` | 42091 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 231 | `func3_8010D6B4` | 42111 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 232 | `func3_8010D714` | 42145 | 359 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 233 | `func3_8010DB94` | 42504 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 234 | `func3_8010DC20` | 42567 | 25 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 235 | `func3_8010DC6C` | 42592 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 236 | `func3_8010DDB8` | 42699 | 117 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 237 | `func3_8010DF38` | 42816 | 11 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 238 | `func3_8010DF54` | 42827 | 145 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 239 | `func3_8010E108` | 42972 | 316 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 240 | `func3_8010E4F0` | 43288 | 236 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 241 | `func3_8010E7A8` | 43524 | 775 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 242 | `func3_8010F0A8` | 44299 | 280 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 243 | `func3_8010F3CC` | 44579 | 256 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 244 | `func3_8010F68C` | 44835 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 245 | `func3_8010F740` | 44893 | 221 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 246 | `func3_8010F9D8` | 45114 | 181 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 247 | `func3_8010FBF8` | 45295 | 330 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 248 | `func3_8010FFE0` | 45625 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block C

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 249 | `func3_801100D8` | 45709 | 338 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 250 | `func3_801104E4` | 46047 | 695 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 251 | `func3_80110CF4` | 46742 | 367 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 252 | `func3_8011113C` | 47109 | 336 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 253 | `func3_801114F4` | 47445 | 222 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 254 | `func3_80111794` | 47667 | 100 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 255 | `func3_801118C4` | 47767 | 79 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 256 | `func3_801119A4` | 47846 | 151 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 257 | `func3_80111B74` | 47997 | 93 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 258 | `func3_80111C80` | 48090 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 259 | `func3_80111E88` | 48265 | 106 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 260 | `func3_80111FE0` | 48371 | 931 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 261 | `func3_80112AD8` | 49302 | 428 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 262 | `func3_80112FF0` | 49730 | 229 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 263 | `func3_80113284` | 49959 | 93 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 264 | `func3_80113380` | 50052 | 207 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 265 | `func3_8011361C` | 50259 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 266 | `func3_80113764` | 50360 | 220 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 267 | `func3_801139AC` | 50580 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 268 | `func3_80113A58` | 50643 | 82 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 269 | `func3_80113B5C` | 50725 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 270 | `func3_80113CA0` | 50837 | 160 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 271 | `func3_80113E78` | 50997 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 272 | `func3_80113EE8` | 51036 | 36 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 273 | `func3_80113F50` | 51072 | 341 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 274 | `func3_8011437C` | 51413 | 71 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 275 | `func3_8011444C` | 51484 | 135 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 276 | `func3_801145F8` | 51619 | 115 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 277 | `func3_80114758` | 51734 | 250 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 278 | `func3_80114A44` | 51984 | 138 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 279 | `func3_80114BF4` | 52122 | 182 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 280 | `func3_80114E30` | 52304 | 651 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 281 | `func3_801155DC` | 52955 | 231 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 282 | `func3_80115894` | 53186 | 493 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 283 | `func3_80115E6C` | 53679 | 457 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 284 | `func3_80116410` | 54136 | 41 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 285 | `func3_80116498` | 54177 | 178 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 286 | `func3_801166E8` | 54355 | 111 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 287 | `func3_8011683C` | 54466 | 250 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 288 | `func3_80116B5C` | 54716 | 81 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 289 | `func3_80116C50` | 54797 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 290 | `func3_80116CC4` | 54836 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 291 | `func3_80116DD0` | 54920 | 167 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 292 | `func3_80116FE0` | 55087 | 133 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 293 | `func3_8011718C` | 55220 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 294 | `func3_80117288` | 55305 | 304 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 295 | `func3_80117634` | 55609 | 49 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 296 | `func3_801176C0` | 55658 | 147 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 297 | `func3_8011789C` | 55805 | 146 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 298 | `func3_80117A6C` | 55951 | 258 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 299 | `func3_80117D84` | 56209 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 300 | `func3_80117E10` | 56256 | 203 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 301 | `func3_8011806C` | 56459 | 465 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 302 | `func3_801185F4` | 56924 | 86 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 303 | `func3_801186F4` | 57010 | 98 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 304 | `func3_80118824` | 57108 | 202 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 305 | `func3_80118A88` | 57310 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 306 | `func3_80118BC8` | 57411 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 307 | `func3_80118D60` | 57545 | 196 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 308 | `func3_80118FC8` | 57741 | 96 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 309 | `func3_801190F4` | 57837 | 316 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 310 | `func3_80119480` | 58153 | 197 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 311 | `func3_801196D0` | 58350 | 482 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 312 | `func3_80119C78` | 58832 | 416 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 313 | `func3_8011A170` | 59248 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 314 | `func3_8011A23C` | 59320 | 426 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 315 | `func3_8011A758` | 59746 | 230 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 316 | `func3_8011AA28` | 59976 | 151 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 317 | `func3_8011ABE4` | 60127 | 73 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 318 | `func3_8011ACB8` | 60200 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 319 | `func3_8011AD50` | 60247 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 320 | `func3_8011ADCC` | 60284 | 172 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 321 | `func3_8011AFBC` | 60456 | 246 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 322 | `func3_8011B278` | 60702 | 437 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 323 | `func3_8011B79C` | 61139 | 394 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 324 | `func3_8011BC18` | 61533 | 156 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 325 | `func3_8011BE14` | 61689 | 342 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 326 | `func3_8011C1F8` | 62031 | 102 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 327 | `func3_8011C324` | 62133 | 275 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 328 | `func3_8011C64C` | 62408 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 329 | `func3_8011C824` | 62569 | 122 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 330 | `func3_8011C9A4` | 62691 | 320 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 331 | `func3_8011CD84` | 63011 | 239 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 332 | `func3_8011D064` | 63250 | 109 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 333 | `func3_8011D1B8` | 63359 | 91 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 334 | `func3_8011D2D0` | 63450 | 169 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 335 | `func3_8011D4E4` | 63619 | 420 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 336 | `func3_8011D9B0` | 64039 | 164 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 337 | `func3_8011DBB0` | 64203 | 193 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 338 | `func3_8011DDF4` | 64396 | 192 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 339 | `func3_8011E044` | 64588 | 305 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 340 | `func3_8011E3D8` | 64893 | 129 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 341 | `func3_8011E540` | 65022 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 342 | `func3_8011E6DC` | 65165 | 83 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 343 | `func3_8011E7E4` | 65248 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 344 | `func3_8011E864` | 65285 | 117 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 345 | `func3_8011E9A8` | 65402 | 176 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 346 | `func3_8011EBA4` | 65578 | 272 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 347 | `func3_8011EEE4` | 65850 | 407 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 348 | `func3_8011F3F8` | 66257 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 349 | `func3_8011F4A0` | 66313 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 350 | `func3_8011F538` | 66363 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 351 | `func3_8011F78C` | 66561 | 309 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 352 | `func3_8011FB20` | 66870 | 121 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 353 | `func3_8011FC98` | 66991 | 202 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 354 | `func3_8011FEDC` | 67193 | 421 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block D

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 355 | `func3_801203C4` | 67614 | 341 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 356 | `func3_801207D8` | 67955 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 357 | `func3_80120848` | 67992 | 190 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 358 | `func3_80120A88` | 68182 | 138 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 359 | `func3_80120C38` | 68320 | 345 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 360 | `func3_80121070` | 68665 | 443 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 361 | `func3_801214E0` | 69108 | 193 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 362 | `func3_801216FC` | 69301 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 363 | `func3_80121764` | 69344 | 226 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 364 | `func3_80121A04` | 69570 | 201 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 365 | `func3_80121C50` | 69771 | 604 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 366 | `func3_80122328` | 70375 | 404 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 367 | `func3_80122800` | 70779 | 211 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 368 | `func3_80122A48` | 70990 | 158 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 369 | `func3_80122C50` | 71148 | 318 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 370 | `func3_80123004` | 71466 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 371 | `func3_80123174` | 71600 | 506 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 372 | `func3_80123744` | 72106 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 373 | `func3_801238A8` | 72222 | 70 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 374 | `func3_8012396C` | 72292 | 784 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 375 | `func3_801242A4` | 73076 | 714 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 376 | `func3_80124AA8` | 73790 | 303 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 377 | `func3_80124E2C` | 74093 | 87 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 378 | `func3_80124F14` | 74180 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 379 | `func3_80124F54` | 74208 | 201 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 380 | `func3_80125160` | 74409 | 215 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 381 | `func3_80125404` | 74624 | 101 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 382 | `func3_80125510` | 74725 | 29 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 383 | `func3_80125568` | 74754 | 136 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 384 | `func3_801256C4` | 74890 | 357 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 385 | `func3_80125B08` | 75247 | 461 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 386 | `func3_80126050` | 75708 | 1049 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 387 | `func3_80126C90` | 76757 | 338 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 388 | `func3_8012705C` | 77095 | 482 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 389 | `func3_801275C0` | 77577 | 273 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 390 | `func3_801278FC` | 77850 | 137 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 391 | `func3_80127AA0` | 77987 | 860 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 392 | `func3_801284C8` | 78847 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 393 | `func3_80128580` | 78914 | 76 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 394 | `func3_80128660` | 78990 | 38 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 395 | `func3_801286C0` | 79028 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 396 | `func3_80128708` | 79055 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 397 | `func3_8012875C` | 79083 | 253 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 398 | `func3_80128A8C` | 79336 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 399 | `func3_80128AD8` | 79360 | 175 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 400 | `func3_80128CD4` | 79535 | 280 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 401 | `func3_8012901C` | 79815 | 347 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 402 | `func3_80129428` | 80162 | 144 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 403 | `func3_801295E0` | 80306 | 579 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 404 | `func3_80129C74` | 80885 | 237 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 405 | `func3_80129F5C` | 81122 | 744 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 406 | `func3_8012A86C` | 81866 | 320 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 407 | `func3_8012AC30` | 82186 | 478 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 408 | `func3_8012B1F8` | 82664 | 564 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 409 | `func3_8012B8C8` | 83228 | 586 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 410 | `func3_8012C008` | 83814 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 411 | `func3_8012C1CC` | 83957 | 5 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 412 | `func3_8012C1D4` | 83962 | 131 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 413 | `func3_8012C36C` | 84093 | 364 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 414 | `func3_8012C75C` | 84457 | 180 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 415 | `func3_8012C9AC` | 84637 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 416 | `func3_8012CB50` | 84780 | 78 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 417 | `func3_8012CC2C` | 84858 | 308 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 418 | `func3_8012D024` | 85166 | 91 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 419 | `func3_8012D118` | 85257 | 241 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 420 | `func3_8012D3B4` | 85498 | 567 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 421 | `func3_8012D9E0` | 86065 | 1358 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 422 | `func3_8012E9C0` | 87423 | 1105 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 423 | `func3_8012F734` | 88528 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 424 | `func3_8012F7C4` | 88575 | 155 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 425 | `func3_8012F980` | 88730 | 589 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block E

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 426 | `func3_8013000C` | 89319 | 209 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 427 | `func3_8013026C` | 89528 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 428 | `func3_80130488` | 89726 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 429 | `func3_801305B4` | 89842 | 61 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 430 | `func3_80130650` | 89903 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 431 | `func3_8013067C` | 89931 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 432 | `func3_801306C0` | 89958 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay/system block F

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 433 | `func3_GetPlayerHealth` | 89997 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay block E

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 434 | `func3_80130730` | 90019 | 149 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 435 | `func3_801308E0` | 90168 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 436 | `func3_80130968` | 90225 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 437 | `func3_801309F4` | 90281 | 235 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 438 | `func3_80130C68` | 90516 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 439 | `func3_80130D00` | 90573 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 440 | `func3_80130D34` | 90595 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 441 | `func3_80130D70` | 90617 | 125 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 442 | `func3_80130EC8` | 90742 | 110 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 443 | `func3_8013100C` | 90852 | 30 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 444 | `func3_80131048` | 90882 | 698 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 445 | `func3_80131840` | 91580 | 527 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 446 | `func3_80131E54` | 92107 | 500 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 447 | `func3_80132428` | 92607 | 325 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 448 | `func3_801327C0` | 92932 | 84 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 449 | `func3_801328AC` | 93016 | 74 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 450 | `func3_8013297C` | 93090 | 108 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 451 | `func3_80132AA0` | 93198 | 324 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 452 | `func3_80132E2C` | 93522 | 413 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 453 | `func3_801332F0` | 93935 | 70 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 454 | `func3_801333C4` | 94005 | 374 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 455 | `func3_80133834` | 94379 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 456 | `func3_8013397C` | 94495 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 457 | `func3_80133A34` | 94558 | 25 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 458 | `func3_80133A6C` | 94583 | 148 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 459 | `func3_80133C00` | 94731 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 460 | `func3_80133D2C` | 94820 | 881 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 461 | `func3_80134850` | 95701 | 233 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 462 | `func3_80134AA0` | 95934 | 95 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 463 | `func3_80134BB0` | 96029 | 863 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 464 | `func3_80135504` | 96892 | 400 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 465 | `func3_8013591C` | 97292 | 108 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 466 | `func3_80135A34` | 97400 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 467 | `func3_80135B60` | 97507 | 253 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 468 | `func3_80135E28` | 97760 | 43 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 469 | `func3_80135E90` | 97803 | 86 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 470 | `func3_80135F70` | 97889 | 163 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 471 | `func3_8013614C` | 98052 | 1166 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 472 | `func3_80136E8C` | 99218 | 643 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 473 | `func3_801375E4` | 99861 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 474 | `func3_80137710` | 99973 | 415 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 475 | `func3_80137BD8` | 100388 | 179 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 476 | `func3_80137DD4` | 100567 | 128 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 477 | `func3_80137F50` | 100695 | 533 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 478 | `func3_80138504` | 101228 | 478 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 479 | `func3_801391B0` | 101706 | 166 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 480 | `func3_80139380` | 101872 | 94 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 481 | `func3_8013949C` | 101966 | 97 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 482 | `func3_801395BC` | 102063 | 389 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 483 | `func3_80139AD4` | 102452 | 593 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 484 | `func3_8013A198` | 103045 | 341 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 485 | `func3_8013A584` | 103386 | 92 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 486 | `func3_8013A690` | 103478 | 981 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 487 | `func3_8013B238` | 104459 | 249 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 488 | `func3_8013B4F4` | 104708 | 181 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 489 | `func3_8013B6FC` | 104889 | 66 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 490 | `func3_8013B7BC` | 104955 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 491 | `func3_8013B7F0` | 104981 | 360 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 492 | `func3_8013BBFC` | 105341 | 44 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 493 | `func3_8013BC68` | 105385 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 494 | `func3_8013BD88` | 105492 | 528 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 495 | `func3_8013C360` | 106020 | 99 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 496 | `func3_8013C46C` | 106119 | 71 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 497 | `func3_8013C528` | 106190 | 303 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 498 | `func3_8013C888` | 106493 | 200 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 499 | `func3_8013CA9C` | 106693 | 486 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 500 | `func3_8013D09C` | 107179 | 275 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 501 | `func3_8013D3C4` | 107454 | 261 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 502 | `func3_8013D6B4` | 107715 | 247 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 503 | `func3_8013D954` | 107962 | 130 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 504 | `func3_8013DAC4` | 108092 | 106 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 505 | `func3_8013DBE8` | 108198 | 147 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 506 | `func3_8013DDAC` | 108345 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 507 | `func3_8013DE6C` | 108410 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 508 | `func3_8013DFE0` | 108544 | 190 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 509 | `func3_8013E200` | 108734 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 510 | `func3_8013E35C` | 108861 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 511 | `func3_8013E40C` | 108920 | 19 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 512 | `func3_8013E434` | 108939 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 513 | `func3_8013E460` | 108959 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 514 | `func3_8013E490` | 108981 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 515 | `func3_8013E4C0` | 109001 | 17 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 516 | `func3_8013E4E8` | 109018 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 517 | `func3_8013E56C` | 109069 | 87 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 518 | `func3_8013E660` | 109156 | 118 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 519 | `func3_8013E7AC` | 109274 | 236 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 520 | `func3_8013EA60` | 109510 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 521 | `func3_8013EAF8` | 109560 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 522 | `func3_8013EB40` | 109582 | 18 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 523 | `func3_8013EB78` | 109600 | 22 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 524 | `func3_8013EBB4` | 109622 | 20 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 525 | `func3_8013EBF4` | 109642 | 19 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 526 | `func3_8013EC30` | 109661 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 527 | `func3_8013EC74` | 109688 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 528 | `func3_8013EDB4` | 109795 | 589 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 529 | `func3_8013F4A0` | 110384 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 530 | `func3_8013F4B4` | 110394 | 37 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 531 | `func3_8013F500` | 110431 | 18 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 532 | `func3_8013F524` | 110449 | 21 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 533 | `func3_8013F564` | 110470 | 14 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 534 | `func3_8013F580` | 110484 | 14 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 535 | `func3_8013F598` | 110498 | 11 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 536 | `func3_8013F5B0` | 110509 | 24 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 537 | `func3_8013F5E4` | 110533 | 59 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 538 | `func3_8013F67C` | 110592 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 539 | `func3_8013F6AC` | 110619 | 16 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 540 | `func3_8013F6E0` | 110635 | 75 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 541 | `func3_8013F7B8` | 110710 | 41 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 542 | `func3_8013F830` | 110751 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 543 | `func3_8013F880` | 110782 | 56 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 544 | `func3_8013F930` | 110838 | 99 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 545 | `func3_8013FA64` | 110937 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 546 | `func3_8013FB14` | 110995 | 137 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 547 | `func3_8013FCBC` | 111132 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 548 | `func3_8013FE30` | 111266 | 62 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 549 | `func3_8013FEF0` | 111328 | 161 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
## Unreviewed gameplay/system block F

| # | Function | Line | Approx. span | Status | Notes |
|---:|---|---:|---:|---|---|
| 550 | `func3_801400F8` | 111489 | 502 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 551 | `func3_80140808` | 111991 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 552 | `func3_8014088C` | 112041 | 29 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 553 | `func3_801408D8` | 112070 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 554 | `func3_80140944` | 112109 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 555 | `func3_801409B0` | 112148 | 194 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 556 | `func3_80140BB4` | 112342 | 13 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 557 | `func3_80140BC0` | 112355 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 558 | `func3_80140CF8` | 112467 | 12 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 559 | `func3_80140D18` | 112479 | 148 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 560 | `func3_80140ED8` | 112627 | 270 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 561 | `func3_80141248` | 112897 | 73 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 562 | `func3_8014133C` | 112970 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 563 | `func3_80141384` | 112997 | 50 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 564 | `func3_801413FC` | 113047 | 62 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 565 | `func3_80141490` | 113109 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 566 | `func3_801414A0` | 113119 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 567 | `func3_80141514` | 113170 | 47 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 568 | `func3_8014158C` | 113217 | 105 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 569 | `func3_801416A0` | 113322 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 570 | `func3_8014173C` | 113380 | 284 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 571 | `func3_80141A5C` | 113664 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 572 | `func3_80141AD0` | 113716 | 162 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 573 | `func3_80141C90` | 113878 | 143 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 574 | `func3_80141E0C` | 114021 | 11 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 575 | `func3_80141E2C` | 114032 | 8 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 576 | `func3_80141E40` | 114040 | 401 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 577 | `func3_80142340` | 114441 | 235 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 578 | `func3_8014261C` | 114676 | 410 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 579 | `func3_80142BA0` | 115086 | 17 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 580 | `func3_80142BCC` | 115103 | 12 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 581 | `func3_80142BE0` | 115115 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 582 | `func3_80142C74` | 115166 | 69 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 583 | `func3_80142D40` | 115235 | 153 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 584 | `func3_80142EE0` | 115388 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 585 | `func3_80142F20` | 115414 | 27 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 586 | `func3_80142F64` | 115441 | 696 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 587 | `func3_801437E0` | 116137 | 229 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 588 | `func3_80143B00` | 116366 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 589 | `func3_80143D30` | 116564 | 115 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 590 | `func3_80143E38` | 116679 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 591 | `func3_80143EB0` | 116718 | 17 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 592 | `func3_80143ED8` | 116735 | 127 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 593 | `func3_80144020` | 116862 | 183 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 594 | `func3_80144214` | 117045 | 34 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 595 | `func3_8014426C` | 117079 | 58 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 596 | `func3_80144304` | 117137 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 597 | `func3_80144340` | 117163 | 63 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 598 | `func3_801443C8` | 117226 | 39 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 599 | `func3_80144414` | 117265 | 275 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 600 | `func3_80144710` | 117540 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 601 | `func3_801447F4` | 117629 | 201 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 602 | `func3_80144A10` | 117830 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 603 | `func3_80144AB0` | 117895 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 604 | `func3_80144B60` | 117962 | 426 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 605 | `func3_80145098` | 118388 | 698 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 606 | `func3_80145840` | 119086 | 1671 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 607 | `func3_80146C28` | 120757 | 53 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 608 | `func3_80146CB0` | 120810 | 628 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 609 | `func3_80147414` | 121438 | 246 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 610 | `func3_801476EC` | 121684 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 611 | `func3_801477A8` | 121756 | 52 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 612 | `func3_80147830` | 121808 | 274 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 613 | `func3_80147B20` | 122082 | 715 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 614 | `func3_80148360` | 122797 | 226 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 615 | `func3_80148610` | 123023 | 75 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 616 | `func3_801486E0` | 123098 | 88 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 617 | `func3_801487D8` | 123186 | 38 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 618 | `func3_80148838` | 123224 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 619 | `func3_80148884` | 123255 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 620 | `func3_801489AC` | 123371 | 86 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 621 | `func3_80148A94` | 123457 | 104 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 622 | `func3_80148BD4` | 123561 | 165 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 623 | `func3_80148DB8` | 123726 | 31 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 624 | `func3_80148E00` | 123757 | 446 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 625 | `func3_801492D0` | 124203 | 123 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 626 | `func3_80149450` | 124326 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 627 | `func3_8014951C` | 124398 | 46 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 628 | `func3_80149590` | 124444 | 88 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 629 | `func3_8014967C` | 124532 | 85 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 630 | `func3_80149770` | 124617 | 32 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 631 | `func3_801497C0` | 124649 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 632 | `func3_801497D0` | 124659 | 77 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 633 | `func3_80149894` | 124736 | 725 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 634 | `func3_8014A0B0` | 125461 | 267 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 635 | `func3_8014A3DC` | 125728 | 198 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 636 | `func3_8014A600` | 125926 | 112 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 637 | `func3_8014A740` | 126038 | 242 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 638 | `func3_8014A9FC` | 126280 | 861 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 639 | `func3_8014B37C` | 127141 | 721 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 640 | `func3_8014BB98` | 127862 | 412 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 641 | `func3_8014C050` | 128274 | 134 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 642 | `func3_8014C1B4` | 128408 | 316 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 643 | `func3_8014C54C` | 128724 | 873 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 644 | `func3_8014CFC0` | 129597 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 645 | `func3_8014D03C` | 129648 | 895 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 646 | `func3_8014DC30` | 130543 | 284 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 647 | `func3_8014DF78` | 130827 | 136 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 648 | `func3_8014E100` | 130963 | 64 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 649 | `func3_8014E198` | 131027 | 269 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 650 | `func3_8014E4A0` | 131296 | 74 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 651 | `func3_8014E570` | 131370 | 119 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 652 | `func3_8014E6C8` | 131489 | 67 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 653 | `func3_8014E784` | 131556 | 57 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 654 | `func3_8014E81C` | 131613 | 104 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 655 | `func3_8014E948` | 131717 | 129 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 656 | `func3_8014EABC` | 131846 | 220 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 657 | `func3_8014ED54` | 132066 | 149 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 658 | `func3_8014EF0C` | 132215 | 72 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 659 | `func3_8014EFE4` | 132287 | 80 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 660 | `func3_8014F0B8` | 132367 | 107 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 661 | `func3_8014F1F0` | 132474 | 153 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 662 | `func3_8014F3AC` | 132627 | 266 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 663 | `func3_8014F6C8` | 132893 | 116 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 664 | `func3_8014F820` | 133009 | 51 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 665 | `func3_8014F8AC` | 133060 | 28 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 666 | `func3_8014F8E4` | 133088 | 26 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 667 | `func3_8014F914` | 133114 | 74 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 668 | `func3_8014F9D8` | 133188 | 89 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 669 | `func3_8014FAD4` | 133277 | 260 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 670 | `func3_8014FDB0` | 133537 | 266 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 671 | `func3_80150084` | 133803 | 65 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 672 | `func3_80150130` | 133868 | 100 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 673 | `func3_80150230` | 133968 | 10 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 674 | `func3_80150238` | 133978 | 128 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 675 | `func3_801503B4` | 134106 | 154 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 676 | `func3_80150580` | 134260 | 33 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 677 | `func3_801505D8` | 134293 | 114 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 678 | `func3_80150738` | 134407 | 217 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 679 | `func3_801509CC` | 134624 | 119 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 680 | `func3_80150B6C` | 134743 | 66 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 681 | `func3_80150C28` | 134809 | 79 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 682 | `func3_80150D3C` | 134888 | 23 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 683 | `func3_80150D7C` | 134911 | 152 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 684 | `func3_80150F8C` | 135063 | 152 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 685 | `func3_80151148` | 135215 | 135 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 686 | `func3_80151308` | 135350 | 29 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 687 | `func3_8015134C` | 135379 | 184 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
| 688 | `func3_80151554` | 135563 | 12123 lines | TBD | Unreviewed inventory entry; needs a dedicated analysis pass before naming/behavior can be trusted. |
