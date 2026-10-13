# Playgama v0.79.0 submission audit

Reviewed October 13, 2026. This is a tested prototype package, not a certified Playgama release. Gameplay and scoring remain unchanged. The existing repository stores distributable builds; the Godot development workspace is maintained separately.

## Fix before submission

1. **Prevent storage stalls from blocking startup/retry.** `tools/playgama-host.js` awaits `storage.get` before the engine starts, and awaits save flush before installing the ad-loading watchdog. A storage promise that never settles can therefore block either path indefinitely. Add bounded waits, preserve unknown remote progress rather than writing fresh data after a failed/timed-out load, and make failed saves allow play to continue. A timed-out write must not race a newer write. Test never-settling reads/writes and late completion. Current tests cover rejection, not stalls.
2. **Fix context-menu suppression in the packaged HTML.** `tools/package-playgama.mjs` searches for a literal LF-only marker spanning injected source. Windows CRLF prevents this replacement matching: final `index.html` contains no contextmenu handler. CSS selection/callout suppression is present, but does not establish that Chrome context menus are blocked. Inject the listener using a reliable marker or directly through the dedicated host, and make packaging fail if required hooks are absent. Add a generated-HTML assertion and verify long press on mobile.
3. **Test the actual uploaded game.** Local SDK-adapter and mock tests do not validate live ad delivery, iframe focus event ordering, partner saves, or mobile fullscreen. In Playgama QA, test an eligible interstitial after two minutes, close/failure, pause/mute restoration, retry exactly once, bests/mission stars restored after reload, and device rotation without resetting progress. Test fullscreen from a touch gesture and the rotate placeholder inside the host iframe. Check for clipped HUD/menu/results at narrow landscape sizes.

## Production cleanup

- Hide developer playtest history/export controls in the submission preset. Keep them available in the development/ordinary web build. The Playgama menu currently exposes Statistics and the bundled browser CSV/share/copy panel; these are development tools rather than core player progression. The export panel also has a separate visual style.
- Reduce platform storage to preferences, map/vehicle selections, best scores and mission completion. Currently it additionally persists 20 detailed playtest rounds. Keep diagnostic telemetry in development, then verify save size and migration before removing it from production.
- Profile all seven maps on an actual Android phone and iPhone/Safari before claiming broad mobile support. Focus on peak car/tree fires, landmark destruction, first collisions, map switching, and repeated retries. No explicit 60 FPS cap is set in project settings; consider a mobile/platform cap after measuring to avoid unnecessary high-refresh rendering. Keep existing physics/effect caps unless profiling proves a change necessary.
- Add package-level regression checks: required SDK initialization hook, context-menu listener, one main pack, no debug/source files, all referenced assets present, ZIP size and CRC. The final ZIP has been manually verified; automate the checks to catch future shell-export changes.
- Prepare title/icon/cover/screenshots and short English/Spanish submission text. Record exact tested devices/browsers rather than treating SDK integration as device certification.

## Verified now

- Dedicated single-threaded landscape preset; SDK initialized before Godot starts; external script limited to official Bridge CDN.
- Versioned one-key SDK storage, English/Spanish language selection, platform pause/audio handling, game-ready notification, and interstitials only after completed results.
- Node SDK host and ordinary web-host tests rerun successfully on October 13.
- Prior Godot save recovery: 24 checks; pause/audio lifecycle: 8 checks.
- Browser full-round smoke test: score 12,474 restored after reload, alongside map/vehicle/language preferences; no console errors observed.
- ZIP: 18,505,067 bytes, 26 files, 48,274,703 bytes unpacked. Root index.html, asset references, ZIP CRC and manifest SHA hashes verified.
- SHA-256: `f7f0ca8bd40d4058a1d59aa9cfebef1c56ab4943ad66cb543c1f561b518a7c41`.

No leaderboards, rewarded currency, login, purchases, or new metagame systems are needed for this submission pass.

Official requirements reviewed:
- https://wiki.playgama.com/playgama/mcp/game-checklist
- https://wiki.playgama.com/playgama/game-requirements/technical-requirements
