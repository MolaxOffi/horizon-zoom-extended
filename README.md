# Zoom Extended

An extended version of [Horizon](https://github.com/horizon-rust/horizon)'s official Zoom mod
(from [horizon-mods](https://github.com/horizon-rust/horizon-mods/tree/main/native/zoom)).
Hold a key to zoom in, and use the mouse wheel to zoom much further than the original 10x.

## Features

- Hold **Z** (default, rebindable in Options > Controls) to zoom in.
- Scroll while holding it to zoom from 1.25x up to about **70x** (at the default 70° field of view).
- The hotbar stays put while you zoom.
- Settings in Options > Mods > Zoom: starting zoom (2x to 10x), smooth zoom, slower turning.
- Your existing Zoom settings and key binding carry over.

## How it goes past 10x

Horizon caps a mod's zoom at 10x, and only accepts a field of view between 1° and 179°.
Up to 10x this mod uses the game's own zoom. Beyond that it narrows the field of view
(never below 1°) and keeps slowing mouse turning, so the practical maximum is about
70x at a 70° FOV (less with a lower FOV). A zoom of 1,000,000,000x is not possible
with a mod on the current SDK.

## Install

1. Download `zoom-3.1.0.hmod` from the [latest release](<releases link>).
2. Put it in your game's `horizon-mods/` folder.
3. Remove the official Zoom first so you don't have two copies.

## Status

Experimental. The logic is unit-tested and the package passes `cargo horizon-mod check`,
but it has not been tested in game yet. Mouse sensitivity and smooth zoom past 10x may
need tuning. Issues and feedback welcome.

## Build

With [`cargo horizon-mod`](https://github.com/horizon-rust/horizon/tree/main/docs/modding)
(Rust 1.99.1, SDK f00125f):

```sh
cargo test
cargo horizon-mod build --wasm   # target/horizon-mod/zoom.hmod
cargo horizon-mod check
```

## Credits and licence

Based on the official Zoom mod by the Horizon project. Released under the MIT licence,
see [LICENSE](LICENSE).
