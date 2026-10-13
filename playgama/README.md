# Playgama build — v0.79.2

Build with `./tools/Invoke-Godot.ps1 -Action Playgama`.

Upload artifact: `game/builds/ChainReaction-Playgama-v0.79.2.zip`. `index.html` is at the ZIP root. The package includes one hashed pack, the single-threaded Godot WebGL runtime, worklets, icons, asset/font licenses, the host adapter and Bridge config. Duplicate `index.pck`, gzip sidecars, tests, reports, source files and local player saves do not ship. Inventory and SHA-256 hashes: `game/reports/playgama-build.json`.

This is a dedicated export preset with the `playgama` feature. Standard Web and Windows builds have no Playgama interface or advertising. GitHub Pages remains the published v0.78.9 build. Preparing this ZIP does not upload or submit a game.

## SDK integration

- Official Bridge v2 stable CDN, initialized before Godot starts. All game assets are local; Bridge is the only external script.
- Load one versioned settings key through Bridge Storage before Godot reads preferences/bests/missions. Writes serialize and coalesce, keeping the latest state without out-of-order writes. The existing checksum/schema validation, best-score merge, and mission-mask merge apply.
- Remote load failure prevents overwriting unknown progress. Async save failure preserves the session state and exposes the existing save notice. Production saves exclude detailed playtest history; native and ordinary web history limits remain unchanged.
- Platform language selects English or Spanish, with English fallback. A saved manual preference wins.
- Game-ready is sent once after the first interactive scene and preparation cover clear. Gameplay start/stop messages follow active play.
- Platform pause freezes the simulation; platform audio mutes the Master bus. Closing an ad preserves the user's existing pause/mute choices. Focus loss during an ad does not introduce an unintended manual pause.
- Interstitial requests occur only when retrying a completed, revealed result. No ad requests during the round or tally, no rewarded/currency changes. First eligibility is 120 seconds after SDK initialization; at least 90 seconds between actually opened interstitials. Save flush precedes the ad; retry waits for close/failure. Unsupported/skipped ads continue immediately. A loading watchdog can recover if no ad opens, but it never unpauses an open ad.
- Landscape only. Existing safe-area sizing, rotate notice, touch/mouse input, fullscreen action, browser focus handling and visibility pause are preserved. Text selection/callout and context-menu suppression are included. Stats/Fullscreen are omitted from this menu; Settings opens the shared modal. See `PLAYGAMA_CLEANUP.md`.

## Submission fields

- Title: Chain Reaction
- Engine: Godot
- Orientation: Landscape
- Languages: English, Spanish
- Description: Launch a car into traffic and build a huge chain-reaction crash. Keep the wreck moving, trigger Aftershocks, and destroy each map's landmark to chase a higher score.
- How to play: Swipe or drag anywhere in the gameplay area to launch or move your car. Tap to trigger an Aftershock when the bottom-left gauge is ready. Cause crashes and destruction to build points and multipliers before time runs out. Beat each map's two score goals and complete its special and secondary objectives.

Do not claim older OS/browser compatibility or partner distribution until tested. Start with desktop and modern Android browsers; iOS/Safari needs a real device check. No leaderboard/account or purchase integration is included.

## Verification

See PLAYGAMA_CLEANUP.md for the complete cleanup and validation report. All 15 current regression suites passed, and SDK tests cover rejected and stalled storage. Actual browser checks verified the production menu, interactive Settings, language change, Back, a full Harbor round, and retained progress. The package verifier checks ZIP integrity, manifest hashes, HTML/script structure, local references and JavaScript syntax.

Actual Playgama-hosted ads/storage and real Android/iOS performance still need platform QA after upload.

Official references checked on October 13, 2026:

- https://wiki.playgama.com/playgama/bridge-sdk/setup
- https://wiki.playgama.com/playgama/bridge-sdk/api/platform
- https://wiki.playgama.com/playgama/bridge-sdk/api/storage
- https://wiki.playgama.com/playgama/bridge-sdk/api/advertisement/interstitial
- https://wiki.playgama.com/playgama/mcp/game-checklist
- https://wiki.playgama.com/playgama/game-requirements/technical-requirements
- https://wiki.playgama.com/playgama/submitting-a-game
