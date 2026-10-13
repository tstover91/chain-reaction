# Playgama cleanup — v0.79.1

## Player-facing changes

- The dedicated Playgama main menu has Settings and language selection. Stats and Fullscreen are not created. Development/native/ordinary web builds retain their diagnostic and fullscreen controls.
- Settings reuses the existing sound, effects, language and credits window. It stays above the menu for both rendering and GUI input, blocks underlying Play, and Back/Escape returns to the same selections. In-match pause/settings behavior is preserved.
- Playgama exports omit the playtest panel script and browser CSV/share/copy exporter, do not collect playtest history, and remove diagnostic history from platform saves. Bests, missions and preferences retain their existing keys and schema.
- The old portrait layout switch is disabled. Active canvas/camera/menu layouts are landscape, and the obsolete portrait HUD drawing implementation is removed. The rotate placeholder remains part of the browser host.

## Verified removal

- Retired the original 2D scene, its private gameplay modules/resources and 2D capture/profile/tests. Kept CrashHUD and CrashScore because the live 3D game inherits their shared behavior.
- Removed the Castle resource, catapult controller, retired Castle scene-building/finale code, obsolete capture/stress flags, Castle test alias and Castle menu preview. Renamed the shared road-curve helper to courtyard_loop; Graveyard keeps its existing geometry and traffic routes.
- Removed 38 unreferenced model/audio/texture files plus the retired Castle preview (39 asset files total). Asset licenses and source packs outside game/ are retained.
- Required community vehicle textures are retained: Godot's imported scene references them even though their original GLBs embed the images. The audit now reads these import dependencies as well as literal/dynamic-directory references and model URIs.
- Removed the old 2D HUD drawing function and unused vehicle trait labels. One-time migration scripts are archived, rather than left as rerunnable destructive tools.
- The 24 failures in the historical monolithic regression harness were obsolete expectations: identical retry traffic, portrait button locations, immediate result retry, swipe-to-explode, and causal explosion scoring. Archived that harness and replaced the release gate with current targeted suites; retained its report for traceability. Updated landscape tests to test swipe relaunches, all seven maps, and the wider Graveyard movement region.
- Recoverable ZIP backups are in cleanup-backups/, outside the game and export. Every removed file was verified against its backup before deletion. Synced sources/ and original downloaded packs were not edited.

## Reliability and packaging

- Fixed context-menu suppression using an explicit HTML script hook; added a package assertion.
- A platform storage read times out after five seconds and continues with session-only progress, without overwriting unknown remote data.
- Waiting for saves before an ad is bounded to 1.5 seconds. The underlying writes remain serialized: a stalled write cannot race a newer write, and its caller cannot indefinitely block retry. Added stalled-read/write SDK tests.
- Export excludes reports, tests, docs and old builds. A ZIP verifier checks CRC, per-file manifest hashes, local asset references, parsed HTML script presence, JavaScript syntax, one main pack, and absence of stats-export UI.

## Validation

- All 15 current regression suites passed: menu, landscape controls, banked scoring, missions, random traffic, blast/shell cleanup, platform lifecycle, save recovery, and seven map specials. Menu settings was rerun after the final stacking fix: 15 checks passed.
- SDK host tests include stalled storage; ordinary web-host tests pass. Export log has no script/resource errors.
- Actual packaged browser build at a 915×412 landscape viewport: menu has no Stats/Fullscreen; Settings opens; language changes; Back returns to the menu; Harbor starts, accepts a swipe, and completes its tally at 1,476. Existing best 12,474 survives migration. No browser warnings/errors observed.
- Final ZIP: 17,831,760 bytes, 26 files; 47,551,443 bytes unpacked. Main pack game-d81d9d6e72d715d1.pck. SHA-256: 666025a78701092d8da9298d57d30ff05f8464257dfa9c1fb726f3e27f4d5f09.

## Remaining platform verification

Run Playgama's QA after upload for real interstitial delivery, partner/platform storage, host-controlled mobile fullscreen, background/rotation recovery, and real Android/iOS performance. Local SDK mocks and desktop browser tests do not certify those. No extra monetization or gameplay systems are required for this cleanup.
