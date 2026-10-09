# Chain Reaction

A small 3D arcade crash prototype: pull back on the green car and release, then time your Aftershock to keep the pileup going.

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

