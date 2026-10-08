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

## Credits

Built with Godot Engine. Vehicle, road, city, particle, and impact sound assets by [Kenney](https://kenney.nl/), provided under CC0. Pack licenses are included in `licenses/`. The arcade blast sound was generated for this project without third-party samples.

## Hosting

GitHub Pages serves `main` at the repository root. `.nojekyll` preserves the static Godot export. All game asset URLs are relative so the project works under `/chain-reaction/`. This is a single-threaded Compatibility export.
