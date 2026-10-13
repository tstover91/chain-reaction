# Playgama build — v0.79.0

Build with `./tools/Invoke-Godot.ps1 -Action Playgama`.

Upload artifact: `game/builds/ChainReaction-Playgama-v0.79.0.zip`. `index.html` is at the ZIP root. The package includes one hashed pack, the single-threaded Godot WebGL runtime, worklets, icons, asset/font licenses, the host adapter and Bridge config. Duplicate `index.pck`, gzip sidecars, tests, reports, source files and local player saves do not ship. Inventory and SHA-256 hashes: `game/reports/playgama-build.json`.

This is a dedicated export preset with the `playgama` feature. Standard Web and Windows builds have no Playgama interface or advertising. GitHub Pages remains the published v0.78.9 build. Preparing this ZIP does not upload or submit a game.

## SDK integration

- Official Bridge v2 stable CDN, initialized before Godot starts. All game assets are local; Bridge is the only external script.
- Load one versioned settings key through Bridge Storage before Godot reads preferences/bests/missions. Writes serialize and coalesce, keeping the latest state without out-of-order writes. The existing checksum/schema validation, best-score merge, and mission-mask merge apply.
- Remote load failure prevents overwriting unknown progress. Async save failure preserves the session state and exposes the existing save notice. Save payload retains the latest 20 playtest records on reload; full session telemetry remains in memory. Native and ordinary web history limits remain unchanged.
- Platform language selects English or Spanish, with English fallback. A saved manual preference wins.
- Game-ready is sent once after the first interactive scene and preparation cover clear. Gameplay start/stop messages follow active play.
- Platform pause freezes the simulation; platform audio mutes the Master bus. Closing an ad preserves the user's existing pause/mute choices. Focus loss during an ad does not introduce an unintended manual pause.
- Interstitial requests occur only when retrying a completed, revealed result. No ad requests during the round or tally, no rewarded/currency changes. First eligibility is 120 seconds after SDK initialization; at least 90 seconds between actually opened interstitials. Save flush precedes the ad; retry waits for close/failure. Unsupported/skipped ads continue immediately. A loading watchdog can recover if no ad opens, but it never unpauses an open ad.
- Landscape only. Existing safe-area sizing, rotate notice, touch/mouse input, fullscreen action, browser focus handling and visibility pause are preserved. Text selection/callout suppression is included. The later submission audit found context-menu injection missing from generated HTML; see `PLAYGAMA_AUDIT.md` for the required correction and other pre-submission work.

## Submission fields

- Title: Chain Reaction
- Engine: Godot
- Orientation: Landscape
- Languages: English, Spanish
- Description: Launch a car into traffic and build a huge chain-reaction crash. Keep the wreck moving, trigger Aftershocks, and destroy each map's landmark to chase a higher score.
- How to play: Swipe or drag anywhere in the gameplay area to launch or move your car. Tap to trigger an Aftershock when the bottom-left gauge is ready. Cause crashes and destruction to build points and multipliers before time runs out. Beat each map's two score goals and complete its special and secondary objectives.

Do not claim older OS/browser compatibility or partner distribution until tested. Start with desktop and modern Android browsers; iOS/Safari needs a real device check. No leaderboard/account or purchase integration is included.

## Verification

- Node host integration tests: initialization deduplication, one-key storage, queue ordering, failed load/write behavior, language, pause/audio, game-ready timing, gameplay messages, interstitial cooldown and close/failure callbacks.
- Existing browser host sizing/fullscreen/lifecycle tests pass.
- Godot save recovery: 24 checks; platform pause/audio lifecycle: 8 checks.
- Real browser smoke test using the SDK's localhost adapter: startup/menu, map/vehicle/language selection, reload restoration, touch-style mouse drag launch, pause/resume, full round and final tally. No browser console errors observed.
- ZIP integrity, local references, root HTML, script syntax, license inventory, size and SHA hashes checked.
- Completed browser round scored 12,474; preferences and best score restored after reload, including a reload of the final packaged version with no console warnings/errors.
- Final ZIP: 18,505,067 bytes (26 files, 48,274,703 bytes unpacked). SHA-256: `f7f0ca8bd40d4058a1d59aa9cfebef1c56ab4943ad66cb543c1f561b518a7c41`.

Actual Playgama-hosted ad delivery, platform saves and mobile performance still require its QA Tool after upload; localhost/mock tests cannot certify them.

Official references checked on October 13, 2026:

- https://wiki.playgama.com/playgama/bridge-sdk/setup
- https://wiki.playgama.com/playgama/bridge-sdk/api/platform
- https://wiki.playgama.com/playgama/bridge-sdk/api/storage
- https://wiki.playgama.com/playgama/bridge-sdk/api/advertisement/interstitial
- https://wiki.playgama.com/playgama/mcp/game-checklist
- https://wiki.playgama.com/playgama/game-requirements/technical-requirements
- https://wiki.playgama.com/playgama/submitting-a-game
