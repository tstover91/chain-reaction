# Chain Reaction

A small 3D arcade crash prototype: pull back on the green car and release, then time your Aftershock to keep the pileup going.

Version 0.22 replaces ringing collision sounds with short metal/thud mixes, adds
wood sounds for fences, makes glass occasional and softens the chain chime.

Version 0.22.1 removes the chain/combo chime completely, keeping crash sounds
and visual score feedback.

Version 0.23 uses Kenney Sci-Fi Sounds for varied vehicle explosions and a
stronger Aftershock crunch/bass. The CC0 pack license is included in `licenses/`.

Version 0.24 restores timed rounds: fifteen seconds to launch (then auto-launch),
twenty seconds of incoming traffic and a twenty-eight-second round limit after
launch. Pause stops the clocks. Timed-format best scores are stored separately.

Version 0.25 adds a faster 500-point police target and marked explosive cargo
truck, with approach warnings. A third Aftershock requires five new destruction
awards after the second blast. All maps share these rules and the 24-car cap.

Version 0.25.1 shows points with DESTRUCTION above destroyed buildings/scenery.

[Play Chain Reaction](https://tstover91.github.io/chain-reaction/)

## Controls

- Touch/mouse: pull back from the green car and release to launch.
- When Aftershock is ready, pull back on the green car and release to blast in any direction. Tap the button for a quick blast toward the junction. Three more destruction awards earn a second blast.
- Retry resets the scene immediately. Pause contains sound and effects settings.
- Keyboard: left/right arrows aim, Space launches, R retries, P/Escape pauses.

This repository contains the playable web export. The Godot development project is maintained separately. Scores are saved locally in your browser; there are no online leaderboards yet.

Version 0.4 adds staged traffic damage: smoking cars retain their paint, further damage can ignite them, and an explosion leaves a black burnt body. Strong hits and burnout can shed wheels. Your launch car stays green.

Version 0.5 adds taxis, SUVs, and garbage trucks to the traffic mix. Taxis keep their yellow paint; SUVs resist blasts more; garbage trucks are larger, slower obstacles. All use the same damage stages and score once.

Version 0.6 addresses first-collision stutter by preparing collision visuals, material variants, score glyphs and audio during loading, then reusing effect/debris visuals during play. Retry skips this preparation step.

Version 0.7 adds directional Aftershock propulsion and keeps the player car inside the visible arena. A chosen blast replaces its old momentum so it can return to traffic.

Version 0.8 adds a four-second chain multiplier: ×2 at three events, ×3 at six, and ×4 at ten. New wrecks, destroyed scenery and first traffic-car explosions extend it. Each car explosion adds 50 base points once; new awards use the current multiplier. Banked points stay after the chain expires. The HUD shows chain progress, tier cues and actual awards, with explosions and best chain in results. Best scores start in a separate record for this scoring version.

Version 0.8.1 adds larger outlined point popups, lime multiplier callouts and orange explosion bonuses over the cars. Labels follow their source briefly, with limits and nearby tier coalescing to keep the pileup readable. Scoring and best-score records are unchanged from 0.8.

Version 0.9 replaces the scoring timer with explosion chains and blast combos. A car igniting the next car advances causal depth; siblings ignited by one blast form a separate combo when they detonate. Wreck/scenery values stay flat, while each car explosion earns 50 times its own depth and same-blast groups add growing combo bonuses. The HUD/results show chain depth and combo size separately. Fuel tanks can carry chains onward. This scoring version uses a separate best record.

## Credits

Built with Godot Engine. Vehicle, road, city, particle, and impact sound assets by [Kenney](https://kenney.nl/), provided under CC0. Pack licenses are included in `licenses/`. The arcade blast sound was generated for this project without third-party samples.

## Hosting

GitHub Pages serves `main` at the repository root. `.nojekyll` preserves the static Godot export. All game asset URLs are relative so the project works under `/chain-reaction/`. This is a single-threaded Compatibility export.

Version 0.10: swipe anywhere over the gameplay area toward traffic to launch; swipe in any direction when Aftershock is ready to blast and propel the player. Fixed power, release activation and a direction preview at the car.

Version 0.11 improves fire propagation with a slightly wider secondary heat radius and stronger thermal damage, independently of physical push. Damaged nearby cars can extend chains; fresh cars do not ignite from one secondary blast alone.

Version 0.12 adds building collapses and persistent ruins, pooled dust/chunks and collapse audio, skid/scorch marks, clearer fire buildup and stronger bounded camera shake. Swipe controls remain stable and Quiet FX remains available.

Version 0.13 fills out Downtown with 17 destructible buildings, distant city rows, sidewalks, crossings, lamps/signals and service-yard detail. Repeated decoration is batched, and traffic lanes and the launch approach remain clear. The expanded map uses a separate best-score record.

Version 0.14 adds cooler sidewalks, warm shop paving, green residential plots and paths, darker service yards and faint shared surface grain. Gameplay and score records stay the same.

Version 0.15 adds Suburbs: a residential roundabout with four staggered traffic approaches, destructible houses/fences, lawns and a driveway launch. Tap MAP in the header (M on desktop) before launching, on results or while paused to switch maps. Each map has its own best score and the selected map is remembered. Both maps share the same crash, fire, Aftershock and scoring systems.

Version 0.16 adds Crossroads and Main Street alongside Downtown and Suburbs. Crossroads has a central four-way intersection with alternating paired traffic waves. Main Street has two opposing T-junctions linked by a main road, with turning traffic and nearby destruction targets. MAP in the header (M on desktop) cycles through the four maps, each with its own best score. Launch, damage, scoring, Aftershock, fire and attempt-budget rules are shared across every map.

## v0.17

Added English/Spanish interface catalogs and a pause language selector with persistence.
Versioned local save migrations preserve existing map bests and preferences; newer save
schemas are protected from older builds. Core gameplay rules remain unchanged.

## v0.18

Added varied building/roof colors, matching colored ruins, and destructible house-yard
fence sections and planters on all four maps. Existing gameplay rules and local best
scores remain intact. Repeated background models retain the same rendering batches.

## v0.19

Blended building and landscaping ground into the surrounding terrain by removing
individual grass and paving pads. Existing gameplay is unchanged.

## v0.20

Rounds now have a fixed thirty-car traffic roster, a final-wave cue and crashed/30
results. Traffic continues at existing lane speeds/gaps until the roster is delivered,
then results wait for the tail and fires. Old timed records remain stored separately.

## v0.21

Shortened the ending when all arrivals are complete, at least one Aftershock is used and no blast is ready,
no fires remain, and only one or two clean cars are still crawling out.


Version 0.26.0 uses a steeper, centered overhead camera with a slightly wider view.
Buildings are broader and 20% lower, fitted around existing yards and roads.
Building collision, ruins and destruction labels follow the revised proportions.

Version 0.26.1 restores the previous camera position (3,30,28), width 35
and focus (0,0,2.5), retaining the larger, lower buildings from 0.26.0.
Grass is slightly brighter and greener, using the shared terrain material
for the ground and roundabout island. 589 core checks and native captures passed.

Version 0.26.2 strengthens the grass brightness change to a lighter green
(#9abd72); the previous camera and larger buildings remain. Native captures
verify the shared grass material on the four maps and roundabout island.

Version 0.27.0 adds a larger results panel with cars crashed, best chain
and five score categories: wrecks, destruction, special vehicle premium,
explosions and combos. The categories add up to the existing total; police
pay the existing 100 wreck points plus 400 special premium. No score rules
or save keys change. The whole panel retries immediately, and the existing
Retry button remains available. English and Spanish renders verified.
Validation: 589 core, 52 special-vehicle and 197 localization/save checks.

Version 0.28.0 adds freely selectable Balanced, Sports and Humvee launch vehicles.
The aim-phase button cycles choices without resetting traffic or the 15-second
launch countdown. Retry/map changes retain selection; saved stable IDs restore
it on startup. Balanced uses the original best-score key, while Sports/Humvee
keep separate local bests. Scoring, charge thresholds, blast radius/push and
round timing are shared. New specs contain model transforms, paint mesh names,
launch/kick scaling and stable display/selection IDs for future additions.

Balanced: mass 1.35, speed 30, kick 18. Sports: mass 1.05, speed 33.6, kick 21.24.
Humvee: mass 1.9, speed 26.4, kick 14.76. Sports uses its four separate wheels;
Humvee remains one visual mesh and uses the existing generic debris. Both remain
green and inside the existing play bounds. Their shader/material variants are
prewarmed behind the loading cover. Runtime chassis/debris/effect caps remain.
Attribution to Ignition Labs and madtrollstudio appears in Pause and the bundled
community vehicle-models.txt, also staged in the site's licenses directory.
Validation: 589 core, 148 player-choice/round checks and 218 localization/save checks.
Twelve complete map/vehicle rounds tested; native selector captures in en/es.


Version 0.29.0 adds local development foundations: shared Light/Medium/Heavy
player physics profiles, stable traffic vehicle IDs, independent saved paint
choice, an authored round setup, and one persisted completed-round record.
Existing vehicle behavior, camera, scores and best records are preserved.
Save schema 2 migrates older preferences safely. No daily mode, currency, color
picker, accounts, ads or online leaderboard is enabled. See game/docs/FOUNDATIONS.md
in the development workspace for extension boundaries and verification.


Version 0.30.0 tests landscape as the default (1280x720 logical canvas).
The 1280x552 gameplay viewport keeps the previous camera position/angle with
width 66 so all existing player bounds retain a touch margin. Score, chain,
countdown, selection, pause and result UI have dedicated landscape placement.
Swipe controls still use the same screen-to-road projection; maps and physics,
traffic timing, scoring, vehicle profiles and local best-score keys are unchanged.
Portrait remains available with `?layout=portrait` in the web URL or native
`-- --portrait` launch arguments. Landscape is a prototype, not a finalized
orientation decision. Current play/effect caps remain in place; mobile performance
and comfort still need real-device playtesting.


Version 0.30.1 extends road approaches and sidewalk/curb strips on all four maps
past the landscape camera edges, with extra margin for camera shake and portrait
comparison. Downtown roads now use the existing static visual batches. Background
ground coverage grows to match; traffic routes, spawn/exit points, physical floor,
player bounds, destructible targets and scoring remain unchanged.


Version 0.31.0 completes the landscape level pass across Downtown, Suburbs,
Crossroads and Main Street. Wider terrain blocks, residential yards, commercial
frontage, service parking, trees and street furniture fill the camera's new view;
repeated background models and markings use existing static batches. Paved blocks
share continuous terrain instead of separate pads around each building.
Traffic routes now begin/end offscreen at 42 units, with retirement beyond the
view and adjusted startup lead time to keep initial traffic near the junction.
The central launch locations, reachable destruction targets, 20-second arrivals,
15-second launch window, 28-second limit, scoring and pool caps remain unchanged.
Expanded approaches occupy the same 24-chassis pool, including offscreen cars.
Updated layouts use new map score IDs; old best-score sections remain saved.
Both portrait and landscape entry/exit visibility are checked under maximum shake.


Version 0.31.1 tightens landscape camera width from 66 to 62 (about 6.5% larger
on-screen objects). Position and focus translate together one unit toward the
upper map to preserve the viewing angle and balance margins around player bounds.
All-map touch margins, maximum-shake visibility, offscreen traffic and swipe
projection are verified. Portrait framing, gameplay and best-score keys stay unchanged.


Version 0.32.0 fixes the landscape movement region: the old portrait X ±13 clamp
now follows the gameplay camera with a whole-car visibility margin. Every player
model, map change, and retry receives the same precomputed region; Aftershock can
send the car inward from its edges. Newly reachable houses, buildings, fences,
trees and containers use visible destructible colliders rather than background-only
models. Distant scenery remains batched. Startup font warmup includes landscape HUD
sizes. Best scores are separated by orientation and the updated round format because
movement reach and destruction targets affect score eligibility. Earlier records remain saved.


Version 0.33.0 adds a start screen with four lightweight map previews, direct vehicle
selection, the selected setup's personal best, language selection and one Play button.
Map, car and paint preferences use the existing save format. Browsing pauses the world
and launch countdown; Play starts a fresh 15-second window. Maps & Vehicles in pause
and results returns to selection. In-game Retry and the result tap remain immediate.
The hidden 3D viewport stops rendering while browsing; map warmup runs before Play is
enabled. Gameplay rules and existing best-score keys remain unchanged.


Version 0.34.0 strengthens local saving and platform lifecycle handling. Save writes
are verified with checksums before replacement, retain a known-good backup, and
recover backup or first-write staging data after damage/interruption. Historical
best keys survive migration; stale tabs cannot lower bests, and newer save formats
remain protected. Storage failures and recovery are shown on selection/pause.

Focus loss, browser visibility/page events and native app suspension cancel swipes,
stop pending audio, save preferences, pause round clocks/physics and suspend 3D
rendering. Returning to a round requires Resume. Resize cancels input and pauses.
The browser canvas fits CSS device safe areas and dynamic viewport height, with a
rotate prompt on portrait touch devices. Native Android/iOS safe-area transforms
keep the world, HUD and touch projection aligned. Gameplay and score rules are
unchanged. Real phone interruption/notch testing remains part of release validation.


Version 0.35.0 polishes round results, crash feedback and vehicle selection. Results
reveal the exact banked score over 0.9 seconds, flag new personal bests, and show cars
wrecked and the biggest chain. Retry and result-panel taps work immediately throughout;
Quiet FX shows the final score without a count-up. Existing settle/round timing is unchanged.

Scores use blue, chains purple, destruction amber, explosions/combos orange and
Aftershock lime. A persistent green bracket identifies the player during a crash;
a charged Aftershock adds a restrained pulse. Busy awards prioritize important events,
render at most eight score labels, skip overlapping labels, and show one highest-chain
and one combo callout. Stored/scored awards and object/effect caps are unchanged.

The selection screen shows offline previews of the actual three player cars, relative
speed/weight/blast bars, readable comparisons, clearer pressed states and a short menu
fade. Quiet FX disables the pulse/fade. Both layouts and English/Spanish are supported.
Gameplay stats, scoring, save schema and personal-best keys remain unchanged.


Version 0.35.1 tallies results one category at a time: wrecks, destruction, special
bonuses, explosions, then combos. The active row is highlighted and the running total
matches the counted category values. Each nonzero row takes 0.4 seconds with a short
transition; zero rows skip the wait. Retry stays immediate and Quiet FX shows all
final values immediately. Scoring, saved results and round timing are unchanged.


Version 0.36.0 slightly raises vehicle damage thresholds across all maps: meaningful
collision strength increases from 1.8 to 1.9, and accumulated damage required for fire
increases from 15 to 16 (about 6%). The smoke warning, explosion fuse, blast heat,
part-detachment thresholds and vehicle stats retain their existing values. Round
records now include damage settings; updated damage rules use a separate best-score
key while retaining historical records.


Version 0.36.1 reduces simultaneous chassis from 24 to 22 (including the player),
across all maps. Special arrival slots stay reserved; traffic timing, total supply
budget and round duration stay unchanged. Setup descriptors record the cap, with
a new round-rule best-score key retaining older records.

Version 0.36.2 further lowers simultaneous chassis to 20, including the player.
Special reservations, arrival timing and round duration remain unchanged.
