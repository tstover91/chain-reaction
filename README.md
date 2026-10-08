# Chain Reaction

A small 3D arcade crash prototype: pull back on the green car and release, then time your Aftershock to keep the pileup going.

[Play Chain Reaction](https://tstover91.github.io/chain-reaction/)

## Controls

- Touch/mouse: pull back from the green car and release to launch.
- Tap Aftershock when available. Three more destruction awards earn a second blast.
- Retry resets the scene immediately. Pause contains sound and effects settings.
- Keyboard: left/right arrows aim, Space launches, R retries, P/Escape pauses.

This repository contains the playable web export. The Godot development project is maintained separately. Scores are saved locally in your browser; there are no online leaderboards yet.

## Credits

Built with Godot Engine. Vehicle, road, city, particle, and impact sound assets by [Kenney](https://kenney.nl/), provided under CC0. Pack licenses are included in `licenses/`. The arcade blast sound was generated for this project without third-party samples.

## Hosting

GitHub Pages serves `main` at the repository root. `.nojekyll` preserves the static Godot export. All game asset URLs are relative so the project works under `/chain-reaction/`. This is a single-threaded Compatibility export.
